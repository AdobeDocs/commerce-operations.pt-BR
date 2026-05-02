---
title: Atualizar uma instalação baseada em Git
description: Atualize uma instalação do Adobe Commerce clonada de um repositório Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Atualizar uma instalação baseada em Git

Este tópico discute como um desenvolvedor contribuinte pode atualizar o Adobe Commerce sem reinstalá-lo. Se você não for um desenvolvedor contribuinte, consulte [Fazer uma atualização](../implementation/perform-upgrade.md).

Para atualizar se você for um desenvolvedor contribuinte:

{{$include /help/_includes/server-login.md}}

1. Salve as alterações feitas no arquivo `composer.json` porque as próximas etapas o substituem.

1. Crie um backup do arquivo `composer.json`.

   ```shell
   cp composer.json composer.json.old
   ```

1. Atualize seu repositório local para obter o código mais recente:

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Se `git pull origin develop` falhar, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Compare e mescle seu arquivo `composer.json.old` com o arquivo `composer.json`.

1. Resolva as dependências e grave versões exatas no arquivo `composer.lock`.

   ```shell
   composer update
   ```

1. Atualize o banco de dados:

   ```shell
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
