---
title: Visão geral do mecanismo de pesquisa
description: Visão geral das opções do mecanismo de pesquisa para Adobe Commerce e Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Visão geral do mecanismo de pesquisa

A partir da versão 2.4.4, o Adobe Commerce e o Magento Open Source exigem [Elasticsearch] ou [OpenSearch] para ser o mecanismo de pesquisa do catálogo. As versões anteriores da versão 2.4.x exigiam Elasticsearch. Consulte os tópicos a seguir para obter detalhes sobre a instalação de um mecanismo de pesquisa e a configuração inicial:

- [Pré-requisitos do mecanismo de pesquisa]
- [Configurar o nó do mecanismo de pesquisa]
- [Configurar o Apache para seu mecanismo de pesquisa]
- [Instalar o software Commerce] (interface de linha de comando)

Depois de instalar e integrar seu mecanismo de pesquisa com o Adobe Commerce, você deve realizar uma manutenção adicional:

- [Configurar paradas de pesquisa](search-stopwords.md)
- [Configuração do mecanismo de pesquisa](configure-search-engine.md)

<!-- Link Definitions -->

[Pré-requisitos do mecanismo de pesquisa]: ../../installation/prerequisites/search-engine/overview.md
[Configurar o nó do mecanismo de pesquisa]: ../../installation/prerequisites/search-engine/configure-nginx.md
[Configurar o Apache para seu mecanismo de pesquisa]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[Instalar o software Commerce]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
