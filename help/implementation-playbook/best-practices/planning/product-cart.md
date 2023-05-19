---
title: Práticas recomendadas para o carrinho de produtos
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de produtos em um carrinho.
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Práticas recomendadas para gerenciamento do carrinho do produto

Para obter o melhor desempenho, use as diretrizes a seguir para gerenciar os limites de carrinho do Adobe Commerce e do Magento Open Source:

- Nas versões 2.3.x - 2.4.2, permita no máximo 100 produtos em um carrinho.
- Para as versões 2.4.3 e posteriores, o aprimoramento dos recursos de regras de vendas aumentou o máximo do carrinho para 750.


Para as versões 2.3.x - 2.4.2, o desempenho esperado com base nos limites de itens do carrinho é:

- Até **100** produtos em um carrinho — o produto funciona, cumprindo metas de desempenho para o tempo de resposta.
- Até **300** produtos em um carrinho — o produto funciona, mas o tempo de resposta aumenta acima das metas.
- Acima **500** produtos em um carrinho — o carrinho e os fluxos de check-out não têm garantia de funcionamento

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduzir o número de itens do carrinho

Use as estratégias a seguir para gerenciar o número de itens do carrinho

- Dividir pedidos em vários pedidos menores com um número menor de linhas usando o [!UICONTROL Add Item by SKU] recurso.
- Adicione apenas a lógica personalizada e a personalização do carrinho necessária para carregar uma lista de itens.

## Possíveis impactos no desempenho

Ter mais do que o número máximo recomendado de produtos no carrinho pode afetar o desempenho do site das seguintes maneiras:

- Maior tempo de resposta para operações de recuperação de dados, validação de itens de carrinho, verificações de aplicação de regras de preço e cálculos de imposto e total.
- Maior tempo de resposta para renderização de minicart, incluindo renderização de exibições do carrinho, fluxo de finalização e execução.
- Tempo de carregamento aumentado para todas as páginas do site em que o minicart está presente.

## Informações adicionais

- [Configurar opções do produto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Gerenciar um carrinho de compras](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
