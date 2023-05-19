---
title: Configurar e executar tarefas cron
description: Saiba como gerenciar trabalhos cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '745'
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
>O comércio depende da configuração adequada do trabalho cron para muitas funções importantes do sistema, incluindo a indexação. Se não for configurado corretamente, significa que o Commerce não funcionará conforme esperado.

Os sistemas UNIX programam tarefas a serem executadas por usuários específicos utilizando um _crontab_, que é um arquivo que contém instruções para o daemon cron que informam o daemon em vigor para &quot;executar este comando neste momento nesta data&quot;. Cada usuário tem seu próprio crontab, e os comandos em qualquer crontab são executados como o usuário que o possui.

Para executar o cron em um navegador da Web, consulte [Proteger cron.php para ser executado em um navegador](../security/secure-cron-php.md).

## Criar ou remover o crontab Comércio

Esta seção discute como criar ou remover o crontab de Commerce (ou seja, a configuração para jobs cron de Commerce).

A variável _crontab_ é a configuração usada para executar os trabalhos cron.

O aplicativo Commerce usa tarefas cron que podem ser executadas com configurações diferentes. A configuração da linha de comando do PHP controla o trabalho cron geral que reindexa indexadores, gera e-mails, gera o mapa do site e assim por diante.

>[!WARNING]
>
>- Para evitar problemas durante a instalação e atualização, recomendamos que você aplique as mesmas configurações do PHP tanto para a configuração da linha de comando do PHP quanto para a configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte [Configurações necessárias do PHP](../../installation/prerequisites/php-settings.md).
>- Em um sistema de vários nós, o crontab pode ser executado em apenas um nó. Isso se aplica somente se você configurar mais de um nó da Web por motivos relacionados ao desempenho ou à escalabilidade.


### Criar o crontab Comércio

A partir da versão 2.2, o Commerce cria um crontab para você. Adicionamos o crontab Comércio a qualquer crontab configurado para o proprietário do sistema de arquivos do Commerce. Em outras palavras, se você já configurou crontabs para outras extensões ou aplicativos, adicionamos o crontab Commerce a ele.

O crontab Comércio está dentro `#~ MAGENTO START` e `#~ MAGENTO END` comentários no crontab.

Para criar o crontab Comércio:

1. Efetue login como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Uso `--force` para reescrever um crontab existente.

>[!INFO]
>
>- `magento cron:install` não reescreve um crontab existente dentro `#~ MAGENTO START` e `#~ MAGENTO END` comentários no crontab.
>- `magento cron:install --force` não tem efeito em nenhum trabalho cron fora dos comentários do Commerce.


Para ver o crontab, digite o seguinte comando como o proprietário do sistema de arquivos:

```bash
crontab -l
```

A seguir, há uma amostra:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>A variável `update/cron.php` O arquivo foi removido no Commerce 2.4.0. Caso ele exista na instalação, é possível removê-lo com segurança.
>
>Qualquer referência a `update/cron.php` e `bin/magento setup:cron:run` também deve ser removido do crontab

### Remova o crontab Comércio

Você deve remover o crontab Comércio somente antes de desinstalar o aplicativo Comércio.

Para remover o crontab Comércio:

1. Faça logon como ou alterne para a [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Este comando não tem efeito em trabalhos cron fora do `#~ MAGENTO START` e `#~ MAGENTO END` comentários no crontab.

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
>Você deve executar o cron duas vezes: a primeira vez que descobrir tarefas a serem executadas e a segunda vez — para executar as próprias tarefas. A segunda execução de cron deve ocorrer em ou após a `scheduled_at` hora para cada tarefa.

## Logs

Todos `cron` as informações do trabalho foram movidas de `system.log` em um `cron.log`.
Por padrão, as informações do cron podem ser encontradas em `<install_directory>/var/log/cron.log`.
Todas as exceções dos trabalhos cron são registradas por `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Além de estar conectado `cron.log`:

- Trabalhos com falha com `ERROR` e `MISSED` Os status são registrados na variável `<install_directory>/var/log/support_report.log`.

- Trabalhos com um `ERROR` Os status são sempre registrados como `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Trabalhos com um `MISSED` status são registrados como `INFO` no `<install_directory>/var/log/debug.log` diretório (somente modo de desenvolvedor).

>[!INFO]
>
>Todos os dados CRON também são gravados na `cron_schedule` tabela no banco de dados do Commerce. A tabela fornece um histórico de tarefas cron, incluindo:
>
>- ID da tarefa e código
>- Status
>- Data de criação
>- Data programada
>- Data de execução
>- Data de término
>
>Para ver os registros na tabela, faça logon no banco de dados do Commerce na linha de comando e insira `SELECT * from cron_schedule;`.
