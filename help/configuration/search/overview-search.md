---
title: Visão geral do mecanismo de pesquisa
description: Saiba mais sobre o Elasticsearch e o OpenSearch para pesquisa no catálogo do Adobe Commerce, pré-requisitos, configuração do servidor Web e tarefas de manutenção após a instalação.
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Visão geral do mecanismo de pesquisa

A partir da versão 2.4.4, o Adobe Commerce exige que o [Elasticsearch](https://www.elastic.co) ou o [OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) seja o mecanismo de pesquisa do catálogo. As versões anteriores da 2.4.x exigiam o Elasticsearch. Consulte os seguintes tópicos para obter detalhes sobre a instalação de um mecanismo de pesquisa e a configuração inicial:

- [Pré-requisitos do mecanismo de pesquisa](../../installation/prerequisites/search-engine/overview.md)
- [Configurar o nginx para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-nginx.md)
- [Configurar o Apache para seu mecanismo de pesquisa](../../installation/prerequisites/search-engine/configure-apache.md)
- [Instalar o software Commerce](../../installation/composer.md) (interface de linha de comando)

Depois de instalar e integrar seu mecanismo de pesquisa ao Adobe Commerce, é necessário executar manutenção adicional:

- [Configurar palavras irrelevantes de pesquisa](search-stopwords.md)
- [Configuração do mecanismo de pesquisa](configure-search-engine.md)

