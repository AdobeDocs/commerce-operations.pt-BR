---
title: Práticas recomendadas de configuração de categoria
description: Conheça as práticas recomendadas para maximizar o desempenho do site limitando o número de categorias no catálogo.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Práticas recomendadas para configuração de categoria

Para obter o melhor desempenho, não configure mais do que o número máximo recomendado de categorias para sites do Adobe Commerce.

- Para o Adobe Commerce versão 2.4.2 e posterior, configure um máximo de 6000 categorias
- Para Adobe Commerce versão 2.3.x e 2.4.0 para 2.4.1-p1, configure um máximo de 3000 categorias

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduza o número de produtos

Use as seguintes estratégias para reduzir o número de categorias:

- Gerenciar recursos exclusivos do produto por meio de atributos e opções personalizadas
- Remover categorias inativas
- Otimizar a profundidade do catálogo na navegação

## Potenciais impactos no desempenho

Ter mais do que o número máximo recomendado de categorias pode afetar o desempenho do site das seguintes maneiras:

- Aumento tangível no tempo de resposta para páginas de catálogo não armazenadas em cache
- Execução longa e tempos limite ao gerenciar categorias do Administrador
- Aumento do tamanho das tabelas de banco de dados correspondentes
- Tabelas de índice maiores aumentam o tempo necessário para concluir operações de indexação para o `[category/product relation index\]`
- Aumento do tempo de processamento para concluir as operações de criação de árvore de categorias, recuperação de menu e gerenciamento de regras de categoria

## Informações adicionais

- [Visão geral das categorias](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Visão geral da navegação](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Atribuições de produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce na infraestrutura de nuvem: Práticas recomendadas para configuração de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
