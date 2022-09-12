---
title: AWS OpenSearch
description: Siga estas etapas para configurar o serviço Web AWS OpenSearch para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# AWS OpenSearch

O Adobe Commerce e o Magento Open Source 2.4.3 são compatíveis com o uso de clusters do Amazon OpenSearch Service. Esse serviço é o sucessor do Amazon Elasticsearch Service. Este tópico descreve como configurar o Commerce para usar o AWS OpenSearch e como migrar dados de um Elasticsearch local ou instância OpenSearch para um cluster AWS OpenSearch.

## Criar um domínio de serviço AWS OpenSearch

Primeiro, você deve estabelecer uma instância OpenSearch no AWS.
Ler [Criação e gerenciamento de domínios do Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) para obter instruções detalhadas.

## Obter dados para o AWS OpenSearch

Quando tudo estiver preparado no AWS, é hora de preenchê-lo com dados.

Para instalações menores, recomendamos que você crie índices diretamente na instância do AWS pelos seguintes motivos:

* Recriar os índices é uma operação rápida.
* Pode haver incompatibilidades de versão entre a instância antiga e a instância do AWS, e elas podem ser evitadas ao criar diretamente na instância do AWS.

Instalações maiores podem considerar a migração de seus índices de dados da instância existente para o AWS. Embora isso possa reduzir o tempo de inatividade, ainda há um pequeno risco de problemas de incompatibilidade devido às diferentes versões entre o servidor Elasticsearch antigo e o AWS.

Não há necessidade de migrar índices, pois eles podem ser facilmente recriados na instância do AWS.
No entanto, ao migrar índices de dados, verifique se as versões do Elasticsearch/OpenSearch são compatíveis.

Consulte Amazon [Migrando para o Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) instruções para obter mais informações.

### Configurar comércio para OpenSearch

As etapas para configurar o OpenSearch são abordadas na seção [Instalação avançada](../../advanced.md) tópico.

Para testar se a nova configuração está funcionando, teste o ponto de extremidade OpenSearch diretamente:

1. Crie um produto no Administrador (por exemplo: sku=&quot;testproduct1&quot;).
1. Reindexe pelo Administrador.
1. Consulte o ponto de extremidade OpenSearch (encontrado na interface do usuário do AWS):

   Para obter índices, anexe: `/_cat/indices/*?v=true` ao URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Para obter produtos do índice, anexe: `/magento2docker_product_1/_search?q=*` ao URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Recursos adicionais

Para obter mais informações, consulte o [Documentação do OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
