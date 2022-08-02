---
title: Visão geral do mecanismo de pesquisa
description: Visão geral das opções do mecanismo de pesquisa para Adobe Commerce e Magento Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
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

[Pré-requisitos do mecanismo de pesquisa]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Configurar o nó do mecanismo de pesquisa]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Configurar o Apache para seu mecanismo de pesquisa]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Instalar o software Commerce]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
