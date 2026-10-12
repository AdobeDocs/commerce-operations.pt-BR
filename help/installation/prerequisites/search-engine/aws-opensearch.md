---
title: AWS OpenSearch
description: Siga estas etapas para configurar o serviço Web AWS OpenSearch para instalações locais do Adobe Commerce.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
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
source-wordcount: '341'
ht-degree: 0%
---
# AWS OpenSearch

O Adobe Commerce 2.4.5 é compatível com o uso de clusters do Amazon OpenSearch Service. Este serviço é o sucessor do Amazon Elasticsearch Service. Este tópico descreve como configurar o Commerce para usar o AWS OpenSearch e como migrar dados de uma instância local do Elasticsearch ou OpenSearch para um cluster do AWS OpenSearch.

## Criar um domínio do serviço AWS OpenSearch

Primeiro, é necessário estabelecer uma instância OpenSearch no AWS.
Leia [Criação e gerenciamento de domínios do Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) para obter instruções detalhadas.

## Obter dados para o AWS OpenSearch

Depois que tudo estiver preparado no AWS, é hora de preenchê-lo com dados.

Para instalações menores, recomendamos que você crie índices diretamente na instância do AWS pelos seguintes motivos:

* Recriar os índices é uma operação rápida.
* Pode haver incompatibilidades de versão entre a instância antiga e a instância do AWS e elas podem ser evitadas ao criar diretamente na instância do AWS.

Instalações maiores podem considerar a migração de seus índices de dados da instância existente para o AWS. Embora isso possa reduzir o tempo de inatividade, ainda há um pequeno risco de problemas de incompatibilidade devido a versões diferentes entre o servidor Elasticsearch antigo e o AWS.

Não há necessidade de migrar índices, pois eles podem ser facilmente recriados na instância do AWS.
No entanto, ao migrar índices de dados, verifique se as versões do Elasticsearch/OpenSearch são compatíveis.

Consulte as instruções do [Migrating to Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) da Amazon para obter mais informações.

### Configurar o Commerce para OpenSearch

As etapas para configurar o OpenSearch são abordadas no tópico [Instalação avançada](../../advanced.md).

Para testar se a nova configuração está funcionando, teste o endpoint do OpenSearch diretamente:

1. Crie um produto no Administrador (Por exemplo: sku=&quot;testproduct1&quot;).
1. Reindexe por meio do Administrador.
1. Consulte o endpoint do OpenSearch (encontrado na interface do usuário do AWS):

   Para obter índices, anexe: `/_cat/indices/*?v=true` à URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Para obter produtos do índice, anexe: `/magento2docker_product_1/_search?q=*` à URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Recursos adicionais

Para obter informações adicionais, consulte a [documentação do OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
