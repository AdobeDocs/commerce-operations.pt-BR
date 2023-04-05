---
title: Desinstalar pacotes de idiomas
description: Siga estas etapas para desinstalar um pacote de idioma Adobe Commerce ou Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Desinstalar pacotes de idiomas

Esta seção discute como desinstalar um ou mais pacotes de idioma, incluindo o código dos pacotes de idioma do sistema de arquivos. Você pode criar backups primeiro para restaurar os dados posteriormente.

Este comando desinstala *only* pacotes de idioma especificados em `composer.json`; em outras palavras, pacotes de idioma que são fornecidos como pacotes do Composer. Se o pacote de idioma não for um pacote Composer, você deve desinstalá-lo manualmente removendo o código do pacote de idioma do sistema de arquivos.

Você pode restaurar os backups a qualquer momento usando o [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Uso do comando:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

O comando de desinstalação do pacote de idioma executa as seguintes tarefas:

1. Verifica as dependências; nesse caso, o comando será encerrado.

   Para contornar isso, você pode desinstalar todos os pacotes de idioma dependentes ao mesmo tempo ou desinstalar os pacotes de idioma dependentes primeiro.

1. If `--backup code` for especificado, faça backup do sistema de arquivos (excluindo `var` e `pub/static` diretórios) para `var/backups/<timestamp>_filesystem.tgz`
1. Remove os arquivos de pacotes de idioma da base de código usando `composer remove`.
1. Limpa o cache.

Por exemplo, se você tentar desinstalar um pacote de idioma do qual outro pacote de idioma depende, a seguinte mensagem será exibida:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Uma alternativa é desinstalar ambos os pacotes de idioma após fazer o backup da base de código:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Mensagens semelhantes à seguinte exibição:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
