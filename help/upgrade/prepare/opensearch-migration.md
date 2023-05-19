---
title: Migração do Elasticsearch para o OpenSearch
description: Saiba mais sobre como substituir o mecanismo de pesquisa usado para instalações locais do Adobe Commerce e do Magento Open Source.
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Migração para o OpenSearch

OpenSearch é uma bifurcação de código aberto do Elasticsearch 7.10.2, criada após a alteração do licenciamento do Elasticsearch.

A partir de 2.4.4, 2.4.3-p2 e 2.3.7-p3, o Adobe Commerce e o Magento Open Source suportam OpenSearch. As instalações locais continuam a oferecer suporte ao Elasticsearch, embora ele não seja mais compatível com o Adobe Commerce na infraestrutura em nuvem. A partir da versão 2.4.6, o OpenSearch tem seu próprio módulo e campos nas configurações de Admin.

## Caminho de migração

As etapas para migrar para o OpenSearch são simples e seguem as etapas para configuração de Elasticsearch. Essas etapas pressupõem que o Adobe Commerce é o único aplicativo que usa o mecanismo de pesquisa. Nos casos em que vários aplicativos usarem o mecanismo de pesquisa, siga o guia de migração oficial [Migração do Elasticsearch de código aberto para OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Certifique-se de que sua instalação atenda aos [pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md).

1. Colocar o site em [Modo de manutenção](../../installation/tutorials/maintenance-mode.md).

1. Desinstale opcionalmente o Elasticsearch.

1. [Instalar o OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurar o mecanismo de pesquisa](../../configuration/search/configure-search-engine.md) e executar tarefas relacionadas, como limpar o cache e reindexar o índice de pesquisa do catálogo.

Não são necessárias mais alterações no valor de configuração.
