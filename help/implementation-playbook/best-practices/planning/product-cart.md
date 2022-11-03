---
title: Práticas recomendadas para carrinho de produtos
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de produtos em um carrinho.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Práticas recomendadas para o gerenciamento do carrinho de produtos

Para obter o melhor desempenho, use as seguintes diretrizes para gerenciar os limites do carrinho para Adobe Commerce e Magento Open Source:

- Para as versões 2.3.x - 2.4.2, permita no máximo 100 produtos em um carrinho.
- Nas versões 2.4.3 e posteriores, o aprimoramento dos recursos das regras de vendas aumentou o máximo do carrinho para 750.


Para as versões 2.3.x - 2.4.2, o desempenho esperado com base nos limites de item do carrinho é:

- Até **100** produtos em um carrinho — o produto funciona, atingindo metas de desempenho para o tempo de resposta.
- Até **300** produtos em um carrinho — o produto funciona, mas o tempo de resposta aumenta acima dos alvos.
- Acima **500** produtos em um carrinho — os fluxos de carrinho e check-out não têm garantia de funcionar

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduzir o número de itens do carrinho

Use as seguintes estratégias para gerenciar o número de itens do carrinho

- Divida pedidos em vários pedidos menores com um número menor de linhas usando o [!UICONTROL Add Item by SKU] recurso.
- Adicione somente a lógica personalizada e a personalização do carrinho necessárias para carregar uma lista de itens.

## Potenciais impactos no desempenho

Ter mais do que o número máximo recomendado de produtos no carrinho pode afetar o desempenho do site das seguintes maneiras:

- Aumento do tempo de resposta para operações de recuperação de dados, validação de itens do carrinho, verificações para aplicar regras de preço e cálculos de imposto e total.
- Aumento do tempo de resposta para renderização de minicart, incluindo renderização de exibições do carrinho, fluxo de finalização e execução.
- Tempo de carregamento aumentado para todas as páginas do site em que o minicart está presente.

## Informações adicionais

- [Configurar opções do produto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Gerenciar um carrinho de compras](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
