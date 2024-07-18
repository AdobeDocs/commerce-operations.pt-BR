---
title: Configurar e executar tarefas cron
description: Saiba como gerenciar trabalhos cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Configurar trabalhos cron

{{file-system-owner}}

Vários recursos do Commerce exigem pelo menos um trabalho cron, que agenda atividades para ocorrer no futuro. Segue-se uma lista parcial dessas atividades:

- Regras de preço de catálogo
- Boletins informativos
- Gerar mapas de site do Google
- Alertas/notificações do cliente (alteração de preço do produto, produto de volta ao estoque)
- Reindexação
- Vendas privadas (somente Adobe Commerce)
- Atualização automática das taxas de câmbio
- Todos os emails do Commerce (incluindo confirmação de pedido e transacional)

>[!WARNING]
>
>Você não pode mais executar `dev/tools/cron.sh` porque o script foi removido.

>[!INFO]
>
>O Commerce depende da configuração adequada do trabalho cron para muitas funções importantes do sistema, incluindo a indexação. Se não for configurado corretamente, o Commerce não funcionará conforme esperado.

Os sistemas UNIX agendam tarefas a serem executadas por usuários específicos usando um _crontab_, que é um arquivo que contém instruções para o daemon cron que instruem o daemon a &quot;executar este comando neste momento nesta data&quot;. Cada usuário tem seu próprio crontab, e os comandos em qualquer crontab são executados como o usuário que o possui.

Para executar o cron em um navegador da Web, consulte [Secure cron.php para executar em um navegador](../security/secure-cron-php.md).

## Criar ou remover o crontab do Commerce

Esta seção discute como criar ou remover o crontab do Commerce (ou seja, a configuração dos trabalhos cron do Commerce).

O _crontab_ é a configuração usada para executar tarefas cron.

O aplicativo Commerce usa tarefas cron que podem ser executadas com configurações diferentes. A configuração da linha de comando do PHP controla o trabalho cron geral que reindexa indexadores, gera e-mails, gera o mapa do site e assim por diante.

>[!WARNING]
>
>- Para evitar problemas durante a instalação e atualização, recomendamos que você aplique as mesmas configurações do PHP tanto para a configuração da linha de comando do PHP quanto para a configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte [Configurações PHP necessárias](../../installation/prerequisites/php-settings.md).
>- Em um sistema de vários nós, o crontab pode ser executado em apenas um nó. Isso se aplica somente se você configurar mais de um nó da Web por motivos relacionados ao desempenho ou à escalabilidade.

### Crie o crontab do Commerce

A partir da versão 2.2, o Commerce cria um crontab para você. Adicionamos o crontab Commerce a qualquer crontab configurado para o proprietário do sistema de arquivos Commerce. Em outras palavras, se você já configurou crontabs para outras extensões ou aplicativos, nós adicionamos o crontab Commerce a ele.

O crontab Commerce está dentro de `#~ MAGENTO START` e `#~ MAGENTO END` comentários no crontab.

Para criar o crontab do Commerce:

1. Faça logon como ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Use `--force` para reescrever um crontab existente.

>[!INFO]
>
>- `magento cron:install` não reescreve um crontab existente dentro de comentários `#~ MAGENTO START` e `#~ MAGENTO END` em seu crontab.
>- `magento cron:install --force` não tem efeito em nenhum trabalho cron fora dos comentários do Commerce.

Para ver o crontab, digite o seguinte comando como o proprietário do sistema de arquivos:

```bash
crontab -l
```

A seguir, há uma amostra:

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>O arquivo `update/cron.php` foi removido no Commerce 2.4.0. Se ele existir na sua instalação, poderá ser removido com segurança.
>
>Qualquer referência a `update/cron.php` e `bin/magento setup:cron:run` também deve ser removida do crontab

### Remova o crontab do Commerce

Você deve remover o crontab Commerce somente antes de desinstalar o aplicativo Commerce.

Para remover o crontab do Commerce:

1. Faça logon como ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Este comando não tem efeito nos trabalhos cron fora dos comentários `#~ MAGENTO START` e `#~ MAGENTO END` em seu crontab.

## Executar cron a partir da linha de comando

Opções de comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

onde `--group` especifica o grupo cron a ser executado (omita esta opção para executar o cron para todos os grupos)

Para executar o trabalho cron de indexação, insira:

```bash
bin/magento cron:run --group index
```

Para executar a tarefa cron padrão, digite:

```bash
bin/magento cron:run --group default
```

Para configurar trabalhos e grupos cron personalizados, consulte [Configurar trabalhos cron personalizados e grupos cron](../cron/custom-cron.md).

>[!INFO]
>
>Você deve executar o cron duas vezes: a primeira vez que descobrir tarefas a serem executadas e a segunda vez — para executar as próprias tarefas. A segunda execução de cron deve ocorrer em ou após `scheduled_at` hora para cada tarefa.

## Logs

Todas as informações do trabalho `cron` foram movidas de `system.log` para uma `cron.log` separada.
Por padrão, as informações de cron podem ser encontradas em `<install_directory>/var/log/cron.log`.
Todas as exceções dos trabalhos cron são registradas por `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Além de estar conectado em `cron.log`:

- Trabalhos com falha com status `ERROR` e `MISSED` são registrados no `<install_directory>/var/log/support_report.log`.

- Os trabalhos com status `ERROR` sempre são registrados como `CRITICAL` em `<install_directory>/var/log/exception.log`.

- Os trabalhos com status `MISSED` são registrados como `INFO` no diretório `<install_directory>/var/log/debug.log` (somente modo de desenvolvedor).

>[!INFO]
>
>Todos os dados CRON também são gravados na tabela `cron_schedule` no banco de dados do Commerce. A tabela fornece um histórico de tarefas cron, incluindo:
>
>- ID da tarefa e código
>- Status
>- Data de criação
>- Data programada
>- Data de execução
>- Data de término
>
>Para ver registros na tabela, faça logon no banco de dados do Commerce na linha de comando e digite `SELECT * from cron_schedule;`.
