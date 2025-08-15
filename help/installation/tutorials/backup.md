---
title: Fazer backup e reverter o sistema de arquivos, a mídia e o banco de dados
description: Siga estas etapas para fazer backup e restaurar seu aplicativo do Adobe Commerce.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Fazer backup e reverter o sistema de arquivos, a mídia e o banco de dados

Esse comando permite fazer backup:

* O sistema de arquivos (excluindo os diretórios `var` e `pub/static`)
* O diretório `pub/media`
* O banco de dados

Os backups são armazenados no diretório `var/backups` e podem ser restaurados a qualquer momento usando o comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Depois do backup, você pode [reverter](#rollback) mais tarde.

>[!TIP]
>
>Para obter informações sobre projetos de infraestrutura em nuvem do Adobe Commerce, consulte [Gerenciamento de instantâneos e backup](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) no _Guia da nuvem_.

## Habilitar backups

O recurso de backup está desativado por padrão. Para habilitar, digite o seguinte comando da CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Aviso de descontinuação:**
>&#x200B;>A funcionalidade de backup está obsoleta a partir das versões 2.1.16, 2.2.7 e 2.3.0. Recomendamos investigar tecnologias adicionais de backup e ferramentas binárias de backup (como o Percona XtraBackup).

## Definir o limite de arquivos abertos

A reversão para um backup anterior pode falhar silenciosamente, resultando em dados incompletos sendo gravados no sistema de arquivos ou banco de dados usando o comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Às vezes, uma longa sequência de consulta faz com que o espaço de memória alocado do usuário fique sem memória devido a muitas chamadas recursivas.

## Como definir arquivos abertos `ulimit`

Recomendamos definir os arquivos abertos [`ulimit`](https://ss64.com/bash/ulimit.html) para o usuário do sistema de arquivos com um valor de `65536` ou mais.

Você pode fazer isso na linha de comando ou pode torná-lo uma configuração permanente para o usuário, editando seu shell script.

Antes de continuar, se ainda não tiver feito isso, alterne para o [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).

Comando:

```bash
ulimit -s 65536
```

Você pode alterá-la para um valor maior, se necessário.

>[!NOTE]
>
>A sintaxe para arquivos abertos `ulimit` depende do shell UNIX que você usa. A configuração anterior deve funcionar com CentOS e Ubuntu com o shell Bash. No entanto, para o macOS, a configuração correta é `ulimit -S 65532`. Consulte uma página de manual ou referência de sistema operacional para obter mais informações.

Para definir opcionalmente o valor no shell Bash do usuário:

1. Se ainda não tiver feito isso, alterne para o [proprietário do sistema de arquivos](../prerequisites/file-system/overview.md).
1. Abra `/home/<username>/.bashrc` em um editor de texto.
1. Adicione a seguinte linha:

   ```bash
   ulimit -s 65536
   ```

1. Salve as alterações em `.bashrc` e saia do editor de texto.

>[!WARNING]
>
>Recomendamos que você evite definir um valor para [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) no arquivo `php.ini` porque isso pode resultar em reversões incompletas sem aviso de falha.

## Fazendo backup

Uso do comando:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

O comando executa as seguintes tarefas:

1. Coloca o armazenamento no modo de manutenção.
1. Executa uma das seguintes opções de comando.

   | Opção | Significado | Nome e local do arquivo de backup |
   |--- |--- |--- |
   | `--code` | Faz backup do sistema de arquivos (excluindo os diretórios var e pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Faça backup do diretório pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Faça backup do banco de dados. | `var/backups/<timestamp>/_db.sql` |

1. Retira o armazenamento do modo de manutenção.

Por exemplo, para fazer backup do sistema de arquivos e do banco de dados,

```bash
bin/magento setup:backup --code --db
```

Mensagens semelhantes a esta são exibidas:

```
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Reversão

Esta seção discute como reverter para um backup feito anteriormente. Você deve saber o nome do arquivo de backup a ser restaurado.

Para localizar o nome dos seus backups, informe:

```bash
bin/magento info:backups:list
```

A primeira string no nome do arquivo de backup é o carimbo de data e hora.

Para efetuar rollback para um backup anterior, informe:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Por exemplo, para restaurar um backup de mídia chamado `1440611839_filesystem_media.tgz`, digite

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Mensagens semelhantes a esta são exibidas:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
