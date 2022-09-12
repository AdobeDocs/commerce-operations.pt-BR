---
title: Migrar do Elasticsearch para o OpenSearch
description: Saiba mais sobre a substituição do mecanismo de pesquisa usado em instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Migrando para o OpenSearch

O OpenSearch é uma bifurcação de fonte aberta do Elasticsearch 7.10.2 criada após uma alteração de licenciamento do Elasticsearch.

A partir de 2.4.4, 2.4.3-p2 e 2.3.7-p3, o Adobe Commerce e o Magento Open Source suportarão o OpenSearch. As instalações locais continuam a oferecer suporte ao Elasticsearch, embora ele não seja mais compatível com o Adobe Commerce na infraestrutura em nuvem.

## Caminho de migração

As etapas para migrar para o OpenSearch são simples e seguem amplamente as etapas para a configuração do Elasticsearch. Essas etapas consideram que o Adobe Commerce é o único aplicativo que usa o mecanismo de pesquisa. Nos casos em que vários aplicativos usam o mecanismo de pesquisa, siga o guia de migração oficial [Transferência do Elasticsearch de código aberto para o OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Certifique-se de que a instalação atenda ao [pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md).

1. Coloque o site em [Modo de manutenção](../../installation/tutorials/maintenance-mode.md).

1. Como opção, desinstale o Elasticsearch.

1. [Instalar o OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurar o mecanismo de pesquisa](../../configuration/search/configure-search-engine.md) e executar tarefas relacionadas, como limpar o cache e reindexar o índice de pesquisa do catálogo.

Nenhuma outra alteração no valor de configuração é necessária.
