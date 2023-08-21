---
title: Práticas recomendadas de configuração de variações de produto
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de variações de produto configuradas.
role: Admin
feature: Best Practices, Catalog Management
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Práticas recomendadas para configurar variações de produtos

Para obter o melhor desempenho, configure no máximo 50 variações por produto.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduzir o número de variações de produtos

Para obter o melhor desempenho do site, use as seguintes estratégias para reduzir o número de variações de produtos:

- Reestruturar o catálogo distribuindo o número de variações entre diferentes produtos.
- Remova as opções de atributo configuráveis que não estão em estoque.
- Gerencie variações por meio de recursos alternativos, como opções personalizadas, categorias, produtos relacionados, agrupados e pacotes.

## Possível impacto no desempenho

Exceder o número recomendado de variações de produtos pode afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização em detalhes do produto e páginas de categoria contendo produtos complexos.
- Maior tempo de resposta para concluir as operações de Salvar no Administrador.
- Mais tempo para renderizar o formulário Edição de produto.
- Check-out lento.

## Informações adicionais

- [Criar produtos configuráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Treinamento—[Gerenciar catálogos e produtos usando o Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
