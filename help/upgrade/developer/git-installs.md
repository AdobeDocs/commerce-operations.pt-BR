---
title: Atualizar uma instalação baseada em Git
description: Atualize uma instalação do Adobe Commerce ou Magento Open Source que você clonou de um repositório Git.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Atualizar uma instalação baseada em git

Este tópico discute como um desenvolvedor contribuinte pode atualizar o Adobe Commerce ou o Magento Open Source sem reinstalá-lo. Se você não for um desenvolvedor contribuidor, consulte [Executar uma atualização](../implementation/perform-upgrade.md).

Para atualizar se você for um desenvolvedor contribuidor:

1. Faça logon no servidor.

1. Alterne para [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Altere para o diretório onde você clonou o aplicativo. Por exemplo,

   ```bash
   cd /var/www/magento2
   ```

1. Salve as alterações feitas no `composer.json` porque as próximas etapas o substituem.

1. Crie um backup do `composer.json` arquivo.

   ```bash
   cp composer.json composer.json.old
   ```

1. Atualize seu repositório local para obter o código mais recente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` falha, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Compare e mescle seu `composer.json.old` com o `composer.json` arquivo.

1. Resolva as dependências e grave as versões exatas no `composer.lock` arquivo.

   ```bash
   composer update
   ```

1. Atualize o banco de dados:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```
