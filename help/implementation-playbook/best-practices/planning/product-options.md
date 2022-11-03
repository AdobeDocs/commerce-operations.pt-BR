---
title: Práticas recomendadas de configuração das opções de produto
description: Otimize o desempenho do Adobe Commerce limitando o número de opções de produto.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Práticas recomendadas das opções de produto

Para obter o melhor desempenho, configure no máximo 100 opções de produto por produto.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Reduzir as opções do produto

Para obter o melhor desempenho do site, use as seguintes estratégias para reduzir o número de opções de produto:

- Configure produtos complexos e opções personalizadas como uma fonte de variações de produto.
- Em vez de criar modelos de produto global e contêineres de opção que se aplicam a todos os produtos, use conjuntos de atributos para criar modelos de produto específicos com atributos e opções direcionadas.
- Gerencie informações do produto por meio de um PMS (Product Management System, sistema de gerenciamento de produtos) externo.

## Potencial impacto no desempenho

Configurar muitas opções de produto aumenta a quantidade de dados recuperados para cada produto em todas as operações de leitura e gravação, resultando em:

- Aumento do tráfego de consultas SQL e maior `JOIN` operações aumentam a taxa de transferência do banco de dados.
- Ampliado o tamanho dos índices do Adobe Commerce e do índice de pesquisa de texto completo.

Os aumentos listados acima podem afetar o desempenho do site das seguintes maneiras:

- Tempo de resposta mais longo para a maioria dos cenários de loja relacionados a produtos que contêm muitas opções em atributos.
- Aumento significativo no tempo necessário para concluir as operações de gerenciamento de produtos na Administração, que pode levar ao esgotamento dos tempos limite, especialmente em cenários relacionados à lista de atributos e recuperação de árvore, incluindo o gerenciamento de regras de promoção.
- Pode bloquear ações em massa que concluem operações em massa assíncronas, como importação e exportação, e atribuir preços personalizados a vários produtos em um catálogo compartilhado.

## Informações adicionais

- [Criar um produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Práticas recomendadas para a configuração do atributo do produto](product-attributes-and-options.md)
- [Log de ações em massa](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API de ações em massa de inventário](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formação: Gerencie catálogos e produtos usando o Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

