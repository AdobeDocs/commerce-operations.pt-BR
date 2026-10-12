---
title: Visão geral do mecanismo de pesquisa
description: Saiba mais sobre o Elasticsearch e o OpenSearch para pesquisa no catálogo do Adobe Commerce, pré-requisitos, configuração do servidor Web e tarefas de manutenção após a instalação.
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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

