---
title: Atualizar uma instalação baseada em Git
description: Atualize uma instalação do Adobe Commerce clonada de um repositório Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
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

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
