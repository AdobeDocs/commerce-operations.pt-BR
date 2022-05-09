---
title: Atualizar módulos e extensões
description: Use a interface de linha de comando e o Composer para atualizar módulos e extensões Adobe Commerce e Magento Open Source.
source-git-commit: c619bff9785d22298bc49e2ac9874480ff7a320b
workflow-type: tm+mt
source-wordcount: '0'
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

Consulte as seguintes listagens do Adobe Commerce Marketplace para obter mais informações:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)

