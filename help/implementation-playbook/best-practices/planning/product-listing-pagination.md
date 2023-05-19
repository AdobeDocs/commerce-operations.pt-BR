---
title: Práticas recomendadas para paginação de lista de produtos
description: Saiba como otimizar o desempenho do Adobe Commerce gerenciando o número de produtos exibidos em cada página do catálogo da loja.
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Práticas recomendadas para paginação de lista de produtos

Para obter o melhor desempenho, exiba no máximo 48 produtos por página.

Você pode configurar o Adobe Commerce para permitir que os compradores visualizem todos os produtos da categoria em uma única página. Se o número de produtos da categoria exceder significativamente 48 produtos, atualize a configuração do catálogo para controles de paginação de vitrines.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Atualizar a configuração da lista de produtos

Se você tiver mais de 48 produtos em qualquer categoria, atualize a configuração do catálogo da loja para desativar a opção para **Permitir todos os produtos por página**.

Depois que você desativa essa opção, o Adobe Commerce usa os controles de paginação de vitrine eletrônica de produtos para gerenciar o número de produtos exibidos nos componentes da vitrine eletrônica. Para obter instruções, consulte [Configurar controles de paginação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Informações adicionais

- [Configurar listas de produtos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
