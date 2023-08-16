---
title: Desinstalar módulos
description: Siga estas etapas para desinstalar um módulo Adobe Commerce ou Magento Open Source.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Desinstalar módulos

Esta seção discute como desinstalar um ou mais módulos. Durante a desinstalação, você pode remover opcionalmente o código dos módulos, o esquema do banco de dados e os dados do banco de dados. Você pode criar backups primeiro para recuperar os dados mais tarde.

Você só deve desinstalar um módulo se tiver certeza de que não o usará. Em vez de desinstalar um módulo, você pode desativá-lo conforme discutido em [Ativar ou desativar módulos](manage-modules.md).

>[!NOTE]
>
>Esse comando verifica se somente as dependências declaradas no `composer.json` arquivo. Se você desinstalar um módulo que esteja _não_ definido na variável `composer.json` , esse comando desinstala o módulo sem verificar as dependências. Esse comando não _não_ No entanto, remova o código do módulo do sistema de arquivos. Você deve usar as ferramentas do sistema de arquivos para remover o código do módulo (por exemplo, `rm -rf <path to module>`). Como alternativa, você pode [disable](manage-modules.md) módulos não-Composer.

Uso do comando:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Onde `{ModuleName}` especifica o nome do módulo em `<VendorName>_<ModuleName>` formato. Por exemplo, o nome do módulo Cliente é `Magento_Customer`. Para obter uma lista de nomes de módulo, insira `magento module:status`

O comando de desinstalação do módulo executa as seguintes tarefas:

1. Verifica se os módulos especificados existem na base de código e se são pacotes instalados pelo Composer.

   Esse comando funciona _somente_ com módulos definidos como pacotes do Composer.

1. Verifica as dependências com outros módulos e encerra o comando se houver dependências não atendidas.

   Para contornar isso, você pode desinstalar todos os módulos ao mesmo tempo ou desinstalar os módulos dependentes primeiro.

1. Solicita confirmação para continuar.
1. Coloca o armazenamento no modo de manutenção.
1. Processa as seguintes opções de comando.

   | Opção | Significado | Nome e local do arquivo de backup |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Faz backup do sistema de arquivos (excluindo `var` e `pub/static` diretórios). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Faz backup do diretório pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Faz backup do banco de dados. | `var/backups/<timestamp>_db.gz` |

1. Se `--remove-data` for especificado, remova o esquema do banco de dados e os dados definidos no `Uninstall` classes.

   Para cada módulo especificado a ser desinstalado, chama a variável `uninstall` no seu `Uninstall` classe. Esta classe deve herdar de [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Remove os módulos especificados da `setup_module` tabela de banco de dados.
1. Remove os módulos especificados da lista de módulos no [configuração de implantação](../../configuration/reference/deployment-files.md).
1. Remove o código da base de código usando `composer remove`.

   >[!NOTE]
   >
   >Desinstalando um módulo _sempre_ execuções `composer remove`. A variável `--remove-data` A opção remove os dados do banco de dados e o esquema definidos pelo `Uninstall` classe.

1. Limpa o cache.
1. Atualiza classes geradas.
1. Se `--clear-static-content` for especificado, limpa [arquivos de visualização estáticos gerados](../../configuration/cli/static-view-file-deployment.md).
1. Retira o armazenamento do modo de manutenção.

Por exemplo, se você tentar desinstalar um módulo do qual outro módulo depende, a seguinte mensagem será exibida:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Uma alternativa é desinstalar ambos os módulos após fazer o backup do sistema de arquivos do módulo, `pub/media` arquivos e tabelas de banco de dados, mas _não_ removendo o esquema ou os dados do banco de dados do módulo:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Mensagens semelhantes a esta são exibidas:

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Os erros são exibidos se você tentar desinstalar um módulo do com uma dependência de outro módulo. Nesse caso, não é possível desinstalar um módulo; é necessário desinstalar ambos.

## Reverter o sistema de arquivos, o banco de dados ou os arquivos de mídia

Para restaurar a base de código para o estado em que você fez o backup, use o seguinte comando:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Onde `<filename>` é o nome do arquivo de backup na variável `<app_root>/var/backups` diretório. Para exibir uma lista de arquivos de backup, informe `magento info:backups:list`

>[!WARNING]
>
>Este comando exclui os arquivos especificados ou o banco de dados antes de restaurá-los. Por exemplo, a variável `--media-file` A opção exclui ativos de mídia na variável `pub/media` antes de restaurar a partir do arquivo de reversão especificado. Verifique se você não alterou o sistema de arquivos ou o banco de dados que deseja manter antes de usar este comando.

>[!NOTE]
>
>Para exibir uma lista de arquivos de backup disponíveis, informe `magento info:backups:list`

Esse comando executa as seguintes tarefas:

1. Coloca o armazenamento no modo de manutenção.
1. Verifica o nome do arquivo de backup.
1. Se você especificar um arquivo de reversão de código:

   a. Verifica se os locais de destino de rollback são graváveis (observe que a variável `pub/static` e `var` pastas são ignoradas).

   b. Exclui todos os arquivos e diretórios no diretório de instalação do aplicativo.

   c. Extrai o arquivo de arquivamento para os locais de destino.

1. Se você especificar um arquivo de rollback de banco de dados:

   a. Descarta todo o banco de dados.

   b. Restaura o banco de dados usando o backup do banco de dados.

1. Se você especificar um arquivo de reversão de mídia:

   a. Verifica se os locais de destino de rollback são graváveis.

   b. Exclui todos os arquivos e diretórios em `pub/media`

   c. Extrai o arquivo de arquivamento para os locais de destino.

1. Retira o armazenamento do modo de manutenção.

Por exemplo, para restaurar um backup de código (ou seja, do sistema de arquivos), insira os seguintes comandos na ordem mostrada:

* Exibir uma lista de backups:

  ```bash
  magento info:backups:list
  ```

* Restaurar um backup de arquivo chamado `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Mensagens semelhantes a esta são exibidas:

  ```terminal
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Para executar o `magento` novamente sem alterar os diretórios, talvez seja necessário inserir `cd pwd`.
