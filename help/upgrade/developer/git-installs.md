---
title: Atualizar uma instalação baseada em Git
description: Atualize uma instalação Adobe Commerce ou Magento Open Source clonada de um repositório Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Atualizar uma instalação baseada em Git

Este tópico discute como um desenvolvedor contribuinte pode atualizar o Adobe Commerce ou o Magento Open Source sem reinstalá-lo. Se você não for um desenvolvedor do contributing, consulte [Executar uma atualização](../implementation/perform-upgrade.md).

Para atualizar se você for um desenvolvedor contribuinte:

{{$include /help/_includes/server-login.md}}

1. Salve todas as alterações feitas na `composer.json` porque as próximas etapas o substituem.

1. Crie um backup do seu `composer.json` arquivo.

   ```bash
   cp composer.json composer.json.old
   ```

1. Atualize seu repositório local para obter o código mais recente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Se `git pull origin develop` falha, consulte [solução de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Comparar e mesclar seu `composer.json.old` arquivo com o `composer.json` arquivo.

1. Resolva as dependências e grave versões exatas no `composer.lock` arquivo.

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
