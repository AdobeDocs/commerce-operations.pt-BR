---
title: Desinstalar pacotes de idioma
description: Siga estas etapas para desinstalar um pacote de idioma do Adobe Commerce ou do Magento Open Source.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Desinstalar pacotes de idioma

Esta seção discute como desinstalar um ou mais pacotes de idioma, incluindo, opcionalmente, o código dos pacotes de idioma do sistema de arquivos. Você pode criar backups primeiro para poder restaurar os dados posteriormente.

Este comando desinstala o *somente* pacotes de idiomas especificados em `composer.json`; em outras palavras, pacotes de linguagem que são fornecidos como pacotes do Composer. Se o pacote de idioma não for um pacote do Composer, você deverá desinstalá-lo manualmente removendo o código do pacote de idioma do sistema de arquivos.

É possível restaurar backups a qualquer momento usando o [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Uso do comando:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

O comando de desinstalação do pacote de idioma executa as seguintes tarefas:

1. Verifica as dependências; nesse caso, o comando é finalizado.

   Para contornar isso, você pode desinstalar todos os pacotes de idiomas dependentes ao mesmo tempo ou pode desinstalar os pacotes de idiomas dependentes primeiro.

1. Se `--backup code` for especificado, fazer backup do sistema de arquivos (excluindo `var` e `pub/static` diretórios) para `var/backups/<timestamp>_filesystem.tgz`
1. Remove arquivos de pacotes de idiomas da base de código usando `composer remove`.
1. Limpa o cache.

Por exemplo, se você tentar desinstalar um pacote de idioma do qual outro pacote de idioma depende, a seguinte mensagem será exibida:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Uma alternativa é desinstalar ambos os pacotes de idioma após fazer backup da base de código:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Mensagens semelhantes a esta são exibidas:

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
