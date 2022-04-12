---
title: Mecanismo de pesquisa atual não suportado
description: Solucione problemas na atualização do Adobe Commerce ou do Magento Open Source após encontrar um erro sobre um mecanismo de pesquisa não suportado.
source-git-commit: 96534d5307062aa4fda8f6433630d2d39e2848e7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Mecanismo de pesquisa atual não suportado

A seguinte mensagem de erro indica que a versão do Adobe Commerce ou do Magento Open Source que você está atualizando está configurada para usar um mecanismo de pesquisa de catálogo que não é compatível com a versão para a qual você está atualizando:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Esse erro significa que uma das seguintes condições é verdadeira na versão de nível inferior do Adobe Commerce ou do Magento Open Source:

- O mecanismo de pesquisa é definido como MySQL.
- O mecanismo de pesquisa é definido como uma versão de Elasticsearch que não é mais suportada.

Use o seguinte comando para verificar o mecanismo de pesquisa atual:

```bash
bin/magento config:show catalog/search/engine
```

O erro ocorre se o valor retornado for `mysql` ou `elasticsearch`.

>[!WARNING]
>
>Se você recebeu esse erro, sua instalação está em um estado inconsistente e não pode acessar o Administrador. Recomendamos que você reverta para a versão anterior enquanto resolve esse erro. Para fazer isso, execute um dos seguintes comandos:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Onde `<version>` é a versão do Magento que você estava executando **before** a atualização. Por exemplo, `2.3.5`.

Siga as diretrizes descritas nas seções a seguir para recuperar de um estado inconsistente.

## Se o seu mecanismo de pesquisa for `mysql`

Antes da versão 2.4, o MySQL era o mecanismo de pesquisa de catálogo padrão, mas o MySQL não é mais compatível com essa capacidade. Agora, você deve instalar e configurar o Elasticsearch ou OpenSearch como mecanismo de pesquisa antes de atualizar para 2.4.

Use os seguintes recursos para ajudar a orientá-lo durante este processo:

- [Instalar e configurar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Instalação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configure o Elasticsearch para funcionar com [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) ou [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Configurar o Magento para usar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Após configurar o mecanismo de pesquisa e reindexar, você estará pronto para atualizar para a versão 2.4.

## Se o seu mecanismo de pesquisa for `elasticsearch`

Um valor de `elasticsearch` indica que sua versão de nível inferior do Adobe Commerce ou Magento Open Source está configurada para usar o Elasticsearch 2.x. Esta versão do Elasticsearch não é mais compatível.

Você deve executar as seguintes tarefas antes de atualizar para a versão 2.4:

1. Atualize para uma versão do Elasticsearch suportada pelo Commerce. Consulte [Atualização do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obter instruções completas sobre como fazer backup de seus dados, detectar possíveis problemas de migração e testar atualizações antes de implantar na produção. Dependendo da versão atual do Elasticsearch, pode ser ou não necessário reiniciar o cluster completo.

   >[!NOTE]
   >
   >O Elasticsearch requer o JDK 1.8 ou superior. Consulte [Instale o Java Software Development Kit (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) para verificar qual versão do JDK está instalada.

1. [Configurar o Magento para usar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) e reindexe.

Após configurar o mecanismo de pesquisa e reindexar, você estará pronto para atualizar para a versão 2.4.
