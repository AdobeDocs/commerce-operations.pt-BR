---
title: Práticas recomendadas para configurar promoções
description: Conheça as práticas recomendadas para configurar regras de vendas e códigos de cupom para otimizar o desempenho da loja do Commerce.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Práticas recomendadas para configurar promoções

Para obter o melhor desempenho, siga estas práticas recomendadas para configurar vendas e promoções para itens em um carrinho de compras:

- **Regras de vendas (regras de preço do carrinho)**-Configure no máximo 1000 regras de preço do carrinho para todos os sites
   - Gerencie e remova regras não usadas.
   - Adicione condições de regras restritas (como atributo ou filtro de categoria) para a correspondência mais eficiente.
- **Cupons**—
   - Verifique se o número total de cupons no banco de dados é menor que 250.000.
   - Remova os cupons não utilizados e expirados.
   - Gere apenas o número de cupons necessários para atender aos requisitos da campanha.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Potenciais impactos no desempenho

Ter mais do que o número máximo recomendado de regras de preço do carrinho ou cupons pode afetar o desempenho do site das seguintes maneiras:

- Aumento do tempo de resposta quando os produtos são adicionados ao carrinho.
- Aumento do tempo para carregar e renderizar o minicart.
- Aumento do tempo para renderizar a página do carrinho.
- Aumento do tempo para renderizar o **Totais** na página Check-out.
- A aplicação de cupons pode levar mais de 2 segundos.

## Informações adicionais

- [Noções básicas sobre campanhas e promoções de marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Regras de preço do carrinho](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: Criar uma regra de preço do carrinho](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Códigos de cupom](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce na infraestrutura de nuvem: Práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
