---
title: Migração do Elasticsearch para o OpenSearch
description: Saiba como substituir o mecanismo de pesquisa usado para instalações locais do Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migração para o OpenSearch

O OpenSearch é uma bifurcação de código aberto do Elasticsearch 7.10.2, criada após a alteração de licenciamento da Elasticsearch.

A partir das versões 2.4.4, 2.4.3-p2 e 2.3.7-p3, o Adobe Commerce é compatível com o OpenSearch. As instalações locais continuam sendo compatíveis com o Elasticsearch, embora não sejam mais compatíveis com o Adobe Commerce na infraestrutura em nuvem. A partir da versão 2.4.6, o OpenSearch tem seu próprio módulo e campos nas configurações de Admin.

## Caminho de migração

As etapas para migrar para o OpenSearch são simples e seguem amplamente as etapas para configuração do Elasticsearch. Essas etapas pressupõem que o Adobe Commerce é o único aplicativo que usa o mecanismo de pesquisa. Nos casos em que vários aplicativos usam o mecanismo de pesquisa, siga o guia de migração oficial [Migração do Elasticsearch de código aberto para o OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Certifique-se de que sua instalação atenda aos [pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md).

1. Coloque o site em [Modo de Manutenção](../../installation/tutorials/maintenance-mode.md).

1. Opcionalmente, desinstale o Elasticsearch.

1. [Instalar OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configure o mecanismo de pesquisa](../../configuration/search/configure-search-engine.md) e execute tarefas relacionadas, como a liberação do cache e a reindexação do índice de pesquisa do catálogo.

Não são necessárias mais alterações no valor de configuração.
