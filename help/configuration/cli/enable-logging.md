---
title: Ativar registro
description: Saiba como ativar e desativar tipos de registro.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Ativar registro

{{file-system-owner}}

## Registro de depuração

Por padrão, o Commerce grava no log de depuração (`<install_directory>/var/log/debug.log`) quando estiver no modo padrão ou de desenvolvimento, mas não quando estiver em modo de produção. Use o `bin/magento setup:config:set --enable-debug-logging` para alterar o valor padrão.

>[!INFO]
>
>A partir do Commerce 2.3.1, você não poderá mais usar o `bin/magento config:set dev/debug/debug_logging` para ativar ou desativar o log de depuração para o modo atual.

### Para ativar o log de depuração

1. Use o `setup:config:set` para ativar o log de depuração no modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desativar o log de depuração

1. Use o `setup:config:set` para desativar o log de depuração no modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

## Registro do banco de dados

Por padrão, o Commerce grava logs de atividade do banco de dados no `<install-dir>/var/debug/db.log` arquivo.

### Para habilitar o log do banco de dados

1. Use o `dev:query-log` para ativar ou desativar o log do banco de dados.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

## Registro de cron

Com o lançamento da versão 2.3.1, o Commerce agora cria um `cron` log. \
Recentemente, o comércio tornou mais verboso o registro de cron, o que forneceu mais informações, mas aumentou o `system.log` consideravelmente.
Movimentação `cron` as informações em um log dedicado facilitam a leitura de ambos os logs.

Por padrão, o Commerce grava `cron` informações para a `<install-directory>/var/log/cron.log` arquivo.

## Registro do Syslog

Por padrão, o Commerce grava _syslog_ registra no sistema operacional `syslog` arquivo.
A partir do Commerce 2.3.1, você deve usar o `magento` para ativar ou desativar o syslog.
A configuração em Admin foi removida.

### Para ativar o registro em log do syslog

Logon em `syslog` está desativado por padrão.

1. Use o `setup:config:set` para alterar o `dev/syslog/syslog_logging` valor do banco de dados para `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desabilitar o log do syslog

1. Use o `setup:config:set` para alterar o `dev/syslog/syslog_logging` valor do banco de dados para `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```
