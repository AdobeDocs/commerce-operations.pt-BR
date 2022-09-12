---
title: Configurar e executar trabalhos do cron
description: Saiba como gerenciar trabalhos do cron.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurar trabalhos do cron

{{file-system-owner}}

Vários recursos do Commerce exigem pelo menos um trabalho cron, o que agende as atividades para que ocorram no futuro. Uma lista parcial dessas atividades é exibida a seguir:

- Regras de preço do catálogo
- Informativos
- Geração de mapas de site do Google
- Alertas/notificações do cliente (alteração do preço do produto, produto de volta ao estoque)
- Reindexação
- Vendas privadas (somente Adobe Commerce)
- Atualização automática das taxas de câmbio
- Todos os e-mails de comércio (incluindo confirmação de pedido e transacional)

>[!WARNING]
>
>Não é mais possível executar `dev/tools/cron.sh` porque o script foi removido.

>[!INFO]
>
>O Commerce depende da configuração correta do trabalho de cron para muitas funções importantes do sistema, incluindo indexação. Falhar em configurá-lo corretamente significa que o Commerce não funcionará como esperado.

Os sistemas UNIX programam tarefas a serem realizadas por usuários específicos usando um _crontab_, que é um arquivo que contém instruções para o daemon cron que informa o daemon em vigor a &quot;executar este comando neste momento nesta data&quot;. Cada usuário tem seu próprio crontab e os comandos em qualquer crontab são executados como o usuário que o possui.

Para executar o cron em um navegador da Web, consulte [Seguro o cron.php para ser executado em um navegador](../security/secure-cron-php.md).

## Criar ou remover o crontab Comércio

Esta seção discute como criar ou remover seu crontab de Comércio (ou seja, a configuração de trabalhos do Commerce cron).

O _crontab_ é a configuração usada para executar trabalhos do cron.

O aplicativo Commerce usa tarefas cron que podem ser executadas com configurações diferentes. A configuração da linha de comando PHP controla o trabalho de cron geral que reindexa os indexadores, gera e-mails, gera o mapa do site e assim por diante.

>[!WARNING]
>
>- Para evitar problemas durante a instalação e a atualização, recomendamos que você aplique as mesmas configurações PHP tanto na configuração da linha de comando PHP quanto na configuração do plug-in do servidor Web PHP. Para obter mais informações, consulte [Configurações PHP necessárias](../../installation/prerequisites/php-settings.md).
>- Em um sistema de vários nós, o crontab pode ser executado em apenas um nó. Isso se aplica a você somente se você configurar mais de um nó da Web por motivos relacionados ao desempenho ou escalabilidade.


### Crie o crontab de Comércio

A partir da versão 2.2, o Commerce cria um crontab para você. Adicionamos o crontab Comércio a qualquer crontab configurado para o proprietário do sistema de arquivos do Commerce. Em outras palavras, se você já configurar crontabs para outras extensões ou aplicativos, adicionamos o crontab Comércio a ele.

O crontab de Comércio está dentro `#~ MAGENTO START` e `#~ MAGENTO END` comentários em seu crontab.

Para criar o crontab de Comércio:

1. Faça logon como ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Use `--force` para reescrever um crontab existente.

>[!INFO]
>
>- `magento cron:install` não reescreve um crontab existente dentro de `#~ MAGENTO START` e `#~ MAGENTO END` comentários em seu crontab.
>- `magento cron:install --force` não tem efeito em trabalhos cron fora dos comentários do Commerce.


Para exibir o crontab, insira o seguinte comando como proprietário do sistema de arquivos:

```bash
crontab -l
```

Uma amostra:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>O `update/cron.php` O arquivo foi removido no Commerce 2.4.0, se esse arquivo existir em sua instalação, ele poderá ser removido com segurança.
>
>Qualquer referência a `update/cron.php` e `bin/magento setup:cron:run` também deve ser removido do crontab&quot;

### Remova a guia Comércio

Remova o crontab do Commerce somente antes de desinstalar o aplicativo do Commerce.

Para remover o crontab de Comércio:

1. Faça o login como ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Esse comando não tem efeito em trabalhos cron fora do `#~ MAGENTO START` e `#~ MAGENTO END` comentários em seu crontab.

## Execute cron a partir da linha de comando

Opções de comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

em que `--group` especifica o grupo cron a ser executado (omita esta opção para executar o cron para todos os grupos)

Para executar o trabalho de indexação cron, insira:

```bash
bin/magento cron:run --group index
```

Para executar o trabalho cron padrão, insira:

```bash
bin/magento cron:run --group default
```

Para configurar trabalhos e grupos personalizados do cron, consulte [Configurar trabalhos do cron personalizados e grupos do cron](../cron/custom-cron.md).

>[!INFO]
>
>Você deve executar o cron duas vezes: a primeira vez que você descobre tarefas a serem executadas e a segunda vez — para executar as próprias tarefas. A segunda execução do cron deve ocorrer em ou após a `scheduled_at` para cada tarefa.

## Registro

Todos `cron` as informações do trabalho foram movidas de `system.log` em separado `cron.log`.
Por padrão, as informações de cron podem ser encontradas em `<install_directory>/var/log/cron.log`.
Todas as exceções de trabalhos do cron são registradas por `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Além de estar conectado `cron.log`:

- Falha de trabalhos com `ERROR` e `MISSED` os status são registrados no `<install_directory>/var/log/support_report.log`.

- Trabalhos com um `ERROR` status são sempre registradas como `CRITICAL` em `<install_directory>/var/log/exception.log`.

- Trabalhos com um `MISSED` status são registradas como `INFO` no `<install_directory>/var/log/debug.log` diretório (somente no modo desenvolvedor).

>[!INFO]
>
>Todos os dados do cron também são gravados no `cron_schedule` no banco de dados do Commerce. A tabela fornece um histórico de trabalhos do cron, incluindo:
>
>- ID da tarefa e código
>- Status
>- Data de criação
>- Data agendada
>- Data de execução
>- Data de término
>
>Para ver registros na tabela, faça logon no banco de dados do Commerce na linha de comando e insira `SELECT * from cron_schedule;`.
