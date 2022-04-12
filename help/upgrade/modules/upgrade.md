---
title: Atualizar módulos e extensões
description: Use a interface de linha de comando e o Composer para atualizar módulos e extensões Adobe Commerce e Magento Open Source.
source-git-commit: 70f1bda91023526fbc0024b6a6fef93c7633ecc2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Atualizar módulos e extensões

Para atualizar ou atualizar um módulo ou extensão:

1. Baixe o arquivo atualizado do Marketplace ou de outro desenvolvedor de extensão. Anote o nome e a versão do módulo.

1. Exporte o conteúdo para o diretório de instalação raiz do Adobe Commerce ou Magento Open Source.

1. Se houver um pacote Composer para o módulo, execute um dos seguintes procedimentos.

   Atualizar por nome de módulo:

   ```bash
   composer update vendor/module-name
   ```

   Atualizar por versão:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Execute os seguintes comandos para atualizar, implantar e limpar o cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Extensões agrupadas pelo fornecedor (VBEs)

Adobe removido tudo [VBEs](https://devdocs.magento.com/extensions/vendor/) na versão 2.4.4. Os fornecedores continuam a oferecer suporte a essas extensões no Adobe Commerce Marketplace.

Se quiser continuar usando essas extensões com o Adobe Commerce e o Magento Open Source 2.4.4 e posterior, atualize as dependências do pacote correspondentes em sua `composer.json` arquivo _before_ atualizando para 2.4.4. Entre em contato com o fornecedor para obter o nome e a versão do pacote que será usado.
