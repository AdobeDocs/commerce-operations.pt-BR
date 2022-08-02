---
title: Implantação de máquina única
description: Saiba como implantar atualizações no Commerce em um servidor de produção usando a linha de comando.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---

# Implantação em uma única máquina

Este tópico fornece instruções para implantar atualizações no Commerce em um servidor de produção usando a linha de comando. Esse processo se aplica a usuários técnicos responsáveis por lojas em uma única máquina com alguns temas e localidades instalados.

## Pressupostos

- Você instalou o Commerce usando [Composer].
- Você está aplicando atualizações diretamente no servidor.

>[!WARNING]
>
>Este guia não se aplica se você tiver usado `git clone` para instalar o Commerce.
>A contribuição dos desenvolvedores deve usar [este guia][install] para atualizar a instalação do Commerce.

## Etapas de implantação

1. Faça logon no servidor de produção como, ou alterne para, o [proprietário do sistema de arquivos][file-owner].

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

   **pacote**: O nome do pacote que você deseja atualizar.

   Por exemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: A versão de destino do pacote que você deseja atualizar.

1. Atualizar componentes com o Composer:

   ```bash
   composer update
   ```

1. Atualize o schema e os dados do banco de dados:

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

[install]: https://devdocs.magento.com/guides/v2.4/install-gde/install/prepare-install.html
[composer]: https://devdocs.magento.com/guides/v2.4/install-gde/composer.html
[file-owner]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html#magento-file-system-owner
