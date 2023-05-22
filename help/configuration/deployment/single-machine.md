---
title: Implantação de computador único
description: Saiba como implantar atualizações ao Commerce em um servidor de produção usando a linha de comando.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Implantação em um único computador

Este tópico fornece instruções para implantar atualizações para o Commerce em um servidor de produção usando a linha de comando. Esse processo se aplica aos usuários técnicos responsáveis pelas lojas em execução em uma única máquina com alguns temas e localidades instalados.

## Suposições

- Você instalou o Commerce usando o [Compositor](../../installation/composer.md).
- Você está aplicando atualizações diretamente ao servidor.

>[!WARNING]
>
>Este guia não se aplica se você usou `git clone` para instalar o Commerce.
>Os desenvolvedores colaboradores devem usar [este guia][install] para atualizar a instalação do Commerce.

## Etapas de implantação

1. Faça logon no servidor de produção como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

1. Altere o diretório para o diretório base do Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Ative o modo de manutenção usando o comando:

   ```bash
   bin/magento maintenance:enable
   ```

1. Aplique atualizações ao Commerce ou seus componentes usando o seguinte padrão de comando:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **pacote**: o nome do pacote que você deseja atualizar.

   Por exemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: a versão de destino do pacote que você deseja atualizar.

1. Atualizar componentes com o Composer:

   ```bash
   composer update
   ```

1. Atualize o esquema do banco de dados e os dados:

   ```bash
   bin/magento setup:upgrade
   ```

1. Compile o código:

   ```bash
   bin/magento setup:di:compile
   ```

1. Implantar conteúdo estático:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Sair do modo de manutenção:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
