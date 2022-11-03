---
title: Práticas recomendadas de configuração de variações do produto
description: Saiba como otimizar o desempenho do Adobe Commerce limitando o número de variações de produto configuradas.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Práticas recomendadas para configurar variações do produto

Para melhor desempenho, configure um máximo de 50 variações por produto.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduza o número de variações do produto

Para obter o melhor desempenho do site, use as seguintes estratégias para reduzir o número de variações de produto:

- Reestruturar o catálogo distribuindo o número de variações entre diferentes produtos.
- Remova as opções de atributo configuráveis que não estão em estoque.
- Gerencie variações por meio de recursos alternativos, como opções personalizadas, categorias, produtos relacionados, agrupados e pacotes.

## Potencial impacto no desempenho

Exceder o número recomendado de variações de produto pode afetar o desempenho do site das seguintes maneiras:

- Longos tempos de solicitação e renderização em detalhes do produto e páginas de categoria contendo produtos complexos.
- Aumento do tempo de resposta para concluir as operações de Salvar no Administrador.
- Aumento do tempo para renderizar o formulário de Edição de produto.
- Check-out lento.

## Informações adicionais

- [Criar produtos configuráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formação—[Gerencie catálogos e produtos usando o Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
