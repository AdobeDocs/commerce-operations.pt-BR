---
title: Práticas recomendadas para paginação da lista de produtos
description: Saiba como otimizar o desempenho do Adobe Commerce gerenciando o número de produtos exibidos em cada página do catálogo da loja.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Práticas recomendadas para paginação da lista de produtos

Para um melhor desempenho, exiba no máximo 48 produtos por página.

É possível configurar o Adobe Commerce para permitir que os compradores visualizem todos os produtos da categoria em uma única página. Se o número de produtos da categoria exceder 48 produtos, atualize a configuração do Catálogo para controles de paginação da frente de loja.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Atualizar a configuração da lista de produtos

Se você tiver mais de 48 produtos em qualquer categoria, atualize a configuração do catálogo da loja para desativar a opção para **Permitir todos os produtos por página**.

Após desativar essa opção, o Adobe Commerce usa os controles de paginação da loja de listagem de produtos para gerenciar o número de produtos exibidos nos componentes da loja. Para obter instruções, consulte [Configurar controles de paginação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Informações adicionais

- [Configurar listas de produtos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
