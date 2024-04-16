---
title: Visão geral do mecanismo de pesquisa
description: Visão geral das opções do mecanismo de pesquisa para o Adobe Commerce.
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Visão geral do mecanismo de pesquisa

A partir da versão 2.4.4, o Adobe Commerce exige [Elasticsearch] ou [OpenSearch] para ser o mecanismo de pesquisa do catálogo. As versões anteriores da 2.4.x exigiam o Elasticsearch. Consulte os seguintes tópicos para obter detalhes sobre a instalação de um mecanismo de pesquisa e a configuração inicial:

- [Pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md)
- [Configurar o nginx para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-nginx.md)
- [Configurar o Apache para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-apache.md)
- [Instale o software da Commerce](../../installation/composer.md) (interface de linha de comando)

Depois de instalar e integrar seu mecanismo de pesquisa ao Adobe Commerce, é necessário executar manutenção adicional:

- [Configurar palavras irrelevantes de pesquisa](search-stopwords.md)
- [Configuração do mecanismo de pesquisa](configure-search-engine.md)

<!-- Link Definitions -->

[Elasticsearch]: https://www.elastic.co
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
