---
title: Atualizar módulos e extensões
description: Use a interface de linha de comando e o Composer para atualizar módulos e extensões do Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Atualizar módulos e extensões

Para atualizar ou atualizar um módulo ou uma extensão:

1. Baixe o arquivo atualizado do Marketplace ou de outro desenvolvedor de extensão. Anote o nome e a versão do módulo.

1. Exporte o conteúdo para o diretório de instalação raiz do Adobe Commerce.

1. Se existir um pacote do Composer para o módulo, execute um dos procedimentos a seguir.

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

## VBEs (Vendor bundled extensions)

O Adobe removeu todos os [VBEs](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/upgrade-guide/modules/upgrade) na versão 2.4.4. Os fornecedores continuam a oferecer suporte a essas extensões no Adobe Commerce Marketplace.

Se quiser continuar usando essas extensões com o Adobe Commerce 2.4.4 e posterior, atualize as dependências de pacote correspondentes no arquivo `composer.json` _antes_ de atualizar para a versão 2.4.4. Entre em contato com o fornecedor para obter o nome e a versão do pacote que serão usados.

Consulte as seguintes listagens do Adobe Commerce Marketplace para obter mais informações:

- [Pagamento do Amazon](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vértice](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
