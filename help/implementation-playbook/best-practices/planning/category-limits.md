---
title: Práticas recomendadas de configuração de categoria
description: Conheça as práticas recomendadas para maximizar o desempenho do site limitando o número de categorias no catálogo.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Práticas recomendadas para configuração de categoria

Para melhor desempenho, não configure mais do que o número máximo recomendado de categorias para sites do Adobe Commerce.

- Para a versão 2.4.2 e posterior do Adobe Commerce, configure no máximo 6.000 categorias
- Para a versão 2.3.x e 2.4.0 para 2.4.1-p1 do Adobe Commerce, configure no máximo 3000 categorias

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduzir o número de produtos

Use as seguintes estratégias para reduzir o número de categorias:

- Gerencie recursos exclusivos do produto por meio de atributos e opções personalizadas
- Remover categorias inativas
- Otimizar profundidade do catálogo na navegação

## Possíveis impactos no desempenho

Ter mais do que o número máximo recomendado de categorias pode afetar o desempenho do site das seguintes maneiras:

- Aumento tangível no tempo de resposta para páginas de catálogo não armazenadas em cache
- Execução longa e tempos limite ao gerenciar categorias do administrador
- Aumento no tamanho das tabelas do banco de dados correspondentes
- Tabelas de índice maiores aumentam o tempo necessário para concluir operações de indexação para o `[category/product relation index\]`
- Maior tempo de processamento para concluir as operações de criação de árvore de categorias, recuperação de menu e gerenciamento de regras de categoria

## Informações adicionais

- [Visão geral das categorias](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Visão geral da navegação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Atribuições de produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce na infraestrutura em nuvem: práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
