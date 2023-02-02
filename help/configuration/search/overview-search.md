---
title: Visão geral do mecanismo de pesquisa
description: Visão geral das opções do mecanismo de pesquisa para Adobe Commerce e Magento Open Source.
source-git-commit: 6d2efee51d740583a4606ffa61c972a4020d124b
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Visão geral do mecanismo de pesquisa

A partir da versão 2.4.4, o Adobe Commerce e o Magento Open Source exigem [Elasticsearch] ou [OpenSearch] para ser o mecanismo de pesquisa do catálogo. As versões anteriores da versão 2.4.x exigiam Elasticsearch. Consulte os tópicos a seguir para obter detalhes sobre a instalação de um mecanismo de pesquisa e a configuração inicial:

- [Pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md)
- [Configurar o nó do mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-nginx.md)
- [Configurar o Apache para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-apache.md)
- [Instalar o software Commerce](../../installation/composer.md) (interface de linha de comando)

Depois de instalar e integrar seu mecanismo de pesquisa com o Adobe Commerce, você deve realizar uma manutenção adicional:

- [Configurar paradas de pesquisa](search-stopwords.md)
- [Configuração do mecanismo de pesquisa](configure-search-engine.md)

<!-- Link Definitions -->

[Elasticsearch]: https://www.elastic.co
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
