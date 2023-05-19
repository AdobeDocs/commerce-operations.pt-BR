---
title: Habilitar registro
description: Saiba como ativar e desativar tipos de registro.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Habilitar registro

{{file-system-owner}}

## Log de depuração

Por padrão, o Commerce grava no log de depuração (`<install_directory>/var/log/debug.log`) quando está no modo padrão ou de desenvolvimento, mas não quando está no modo de produção. Use o `bin/magento setup:config:set --enable-debug-logging` para alterar o valor padrão.

>[!INFO]
>
>A partir do Commerce 2.3.1, você não poderá mais usar o `bin/magento config:set dev/debug/debug_logging` comando para ativar ou desativar o log de depuração do modo atual.

### Para ativar o registro de depuração

1. Use o `setup:config:set` comando para habilitar o log de depuração para o modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desativar o log de depuração

1. Use o `setup:config:set` comando para desativar o log de depuração do modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

## Logon do banco de dados

Por padrão, o Commerce grava registros de atividade do banco de dados no `<install-dir>/var/debug/db.log` arquivo.

### Para habilitar o log do banco de dados

1. Use o `dev:query-log` comando para habilitar ou desabilitar o log do banco de dados.

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

## Registro de Cron

Com o lançamento da versão 2.3.1, o Commerce agora cria uma `cron` registro. \
O comércio recentemente tornou o registro de cron mais explícito, o que forneceu mais informações, mas aumentou o `system.log` consideravelmente.
Movendo `cron` para um log dedicado facilita a leitura de ambos os logs.

Por padrão, o Commerce escreve `cron` informações para o `<install-directory>/var/log/cron.log` arquivo.

## Registro do Syslog

Por padrão, o Commerce escreve _syslog_ registros no sistema operacional `syslog` arquivo.
A partir do Commerce 2.3.1, você deve usar o `magento` comando para ativar ou desativar o syslog.
A configuração no Administrador foi removida.

### Para ativar o registro do syslog

Efetuando logon em `syslog` O está desativado por padrão.

1. Use o `setup:config:set` comando para alterar o `dev/syslog/syslog_logging` valor do banco de dados para `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desativar o registro de syslog

1. Use o `setup:config:set` comando para alterar o `dev/syslog/syslog_logging` valor do banco de dados para `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```
