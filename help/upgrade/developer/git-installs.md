---
title: Atualizar uma instalação baseada em Git
description: Atualize uma instalação do Adobe Commerce clonada de um repositório Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Atualizar uma instalação baseada em Git

Este tópico discute como um desenvolvedor contribuinte pode atualizar o Adobe Commerce sem reinstalá-lo. Se você não for um desenvolvedor contribuinte, consulte [Fazer uma atualização](../implementation/perform-upgrade.md).

Para atualizar se você for um desenvolvedor contribuinte:

{{$include /help/_includes/server-login.md}}

1. Salve as alterações feitas no arquivo `composer.json` porque as próximas etapas o substituem.

1. Crie um backup do arquivo `composer.json`.

   ```bash
   cp composer.json composer.json.old
   ```

1. Atualize seu repositório local para obter o código mais recente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Se `git pull origin develop` falhar, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Compare e mescle seu arquivo `composer.json.old` com o arquivo `composer.json`.

1. Resolva as dependências e grave versões exatas no arquivo `composer.lock`.

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
