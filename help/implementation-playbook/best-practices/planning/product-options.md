---
title: Práticas recomendadas de configuração de opções de produto
description: Otimize o desempenho do Adobe Commerce limitando o número de opções de produto.
role: Admin
feature: Best Practices, Catalogs
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Práticas recomendadas de opções de produtos

Para obter o melhor desempenho, configure no máximo 100 opções de produto por produto.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Reduza as opções de produtos

Para obter o melhor desempenho do site, use as seguintes estratégias para reduzir o número de opções de produtos:

- Configure produtos complexos e opções personalizadas como uma fonte de variações de produtos.
- Em vez de criar modelos de produtos globais e contêineres de opções que se aplicam a todos os produtos, use conjuntos de atributos para criar modelos de produtos específicos com atributos e opções direcionados.
- Gerencie informações do produto por meio de um Sistema de gerenciamento de produtos (PMS) externo.

## Possível impacto no desempenho

A configuração de muitas opções de produtos aumenta a quantidade de dados recuperados para cada produto em todas as operações de leitura e gravação, resultando em:

- Maior tráfego de consulta SQL e mais pesado `JOIN` operações aumentam a taxa de transferência do banco de dados.
- Aumento do tamanho dos índices do Adobe Commerce e do índice de pesquisa de texto completo.

Os aumentos listados acima podem afetar o desempenho do site das seguintes maneiras:

- Tempo de resposta mais longo para a maioria dos cenários de loja relacionados a produtos contendo muitas opções em atributos.
- Aumentos significativos no tempo necessário para concluir as operações de gerenciamento de produtos no Admin que podem levar a tempos limite, especialmente em cenários relacionados à lista de atributos e recuperação de árvore, incluindo o gerenciamento de regras de promoção.
- Pode bloquear ações em massa que concluem operações em massa assíncronas, como importação e exportação, e atribuir preços personalizados a vários produtos em um catálogo compartilhado.

## Informações adicionais

- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Práticas recomendadas para a configuração do atributo de produto](product-attributes-and-options.md)
- [Log de ações em massa](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API de ações em massa de estoque](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Treinamento: Gerenciar catálogos e produtos usando o Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
