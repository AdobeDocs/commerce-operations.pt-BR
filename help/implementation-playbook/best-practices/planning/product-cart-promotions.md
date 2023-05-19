---
title: Práticas recomendadas para configurar promoções
description: Conheça as práticas recomendadas para configurar regras de vendas e códigos de cupom para otimizar o desempenho da loja do Commerce.
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Práticas recomendadas para configurar promoções

Para obter o melhor desempenho, siga estas práticas recomendadas para configurar vendas e promoções para itens em um carrinho de compras:

- **Regras de vendas (regras de preço do carrinho)**-Configurar no máximo 1000 regras de preço de carrinho para todos os sites
   - Gerenciar e remover regras não usadas.
   - Adicione condições de regra estritas (como atributo ou filtro de categoria) para a correspondência mais eficiente.
- **Cupons**—
   - Verifique se o número total de cupons no banco de dados é inferior a 250.000.
   - Remova os cupons não utilizados e expirados.
   - Gere apenas o número de cupons necessários para atender aos requisitos da campanha.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Possíveis impactos no desempenho

Ter mais do que o número máximo recomendado de regras de preço do carrinho ou cupons pode afetar o desempenho do site das seguintes maneiras:

- Maior tempo de resposta quando os produtos são adicionados ao carrinho.
- Aumento do tempo para carregar e renderizar o minicart.
- Mais tempo para renderizar a página do carrinho.
- Maior tempo para renderizar o **Totais** na página Check-out.
- A aplicação de cupons pode levar mais de 2 segundos.

## Informações adicionais

- [Noções básicas sobre campanhas e promoções de marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Regras de preço do carrinho](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: Criar uma regra de preço do carrinho](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Códigos de cupom](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce na infraestrutura em nuvem: práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
