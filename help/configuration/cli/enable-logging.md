---
title: Habilitar registro
description: Saiba como ativar e desativar diferentes tipos de logon no Adobe Commerce. Descubra a configuração de registro e as técnicas de gerenciamento.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Habilitar registro

{{file-system-owner}}

## Log de depuração

Por padrão, o Commerce grava no log de depuração (`<install_directory>/var/log/debug.log`) quando está no modo padrão ou de desenvolvimento, mas não quando está no modo de produção. Use o comando `bin/magento setup:config:set --enable-debug-logging` para alterar o valor padrão.

>[!INFO]
>
>A partir do Commerce 2.3.1, não é mais possível usar o comando `bin/magento config:set dev/debug/debug_logging` para habilitar ou desabilitar o log de depuração para o modo atual.

### Para ativar o registro de depuração

1. Use o comando `setup:config:set` para habilitar o log de depuração para o modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desativar o log de depuração

1. Use o comando `setup:config:set` para desabilitar o log de depuração para o modo atual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

## Logon do banco de dados

Por padrão, o Commerce grava logs de atividades do banco de dados no arquivo `<install-dir>/var/debug/db.log`.

### Local de armazenamento do log de consulta

Quando o log do banco de dados está ativado, o Commerce armazena logs de consulta no seguinte local:

- **Arquivo de log da consulta**: `<install-directory>/var/debug/db.log`
- **Diretório de log**: `<install-directory>/var/debug/`

O log de consulta contém:
- Consultas SQL executadas pelo aplicativo
- Tempos de execução da consulta
- Parâmetros e associações de consulta
- Informações de conexão do banco de dados

>[!NOTE]
>
>O arquivo de log de consultas pode crescer rapidamente em ambientes de alto tráfego. Monitore o espaço em disco e considere implementar a rotação de logs ou a limpeza periódica do arquivo de log de consulta.

### Para habilitar o log do banco de dados

1. Use o comando `dev:query-log` para habilitar ou desabilitar o log do banco de dados.

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

### Para exibir logs de consulta

Você pode exibir os logs de consulta usando comandos padrão de exibição de arquivo:

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Registro de Cron

Com o lançamento da versão 2.3.1, o Commerce agora cria um log `cron` separado. \
Recentemente, a Commerce tornou o registro em log do cron mais explícito, o que forneceu mais informações, mas aumentou consideravelmente o `system.log`.
Mover as informações de `cron` para um log dedicado facilita a leitura de ambos os logs.

Por padrão, o Commerce grava informações de `cron` no arquivo `<install-directory>/var/log/cron.log`.

## Registro do Syslog

Por padrão, o Commerce grava os logs _syslog_ no arquivo `syslog` do sistema operacional.
A partir do Commerce 2.3.1, você deve usar o comando `magento` para habilitar ou desabilitar o syslog.
A configuração no Administrador foi removida.

### Para ativar o registro do syslog

O registro em log para `syslog` está desabilitado por padrão.

1. Use o comando `setup:config:set` para alterar o valor do banco de dados `dev/syslog/syslog_logging` para `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```

### Para desativar o registro de syslog

1. Use o comando `setup:config:set` para alterar o valor do banco de dados `dev/syslog/syslog_logging` para `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:flush
   ```
