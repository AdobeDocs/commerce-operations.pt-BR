---
title: Mecanismo de pesquisa atual não suportado
description: Solucione problemas com a atualização do Adobe Commerce ou do Magento Open Source após encontrar um erro sobre um mecanismo de pesquisa não compatível.
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Mecanismo de pesquisa atual não suportado

A seguinte mensagem de erro indica que a versão do Adobe Commerce ou do Magento Open Source que você está atualizando está configurada para usar um mecanismo de pesquisa de catálogo que não é compatível na versão para a qual você está atualizando:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Esse erro significa que uma das seguintes condições é verdadeira na versão de nível inferior do Adobe Commerce ou Magento Open Source:

- O mecanismo de pesquisa é definido como MySQL.
- O mecanismo de pesquisa está definido como uma versão do Elasticsearch que não é mais suportada.

Use o seguinte comando para verificar o mecanismo de pesquisa atual:

```bash
bin/magento config:show catalog/search/engine
```

O erro ocorre se o valor retornado for `mysql`, `elasticsearch`ou `elasticsearch6`.

>[!WARNING]
>
>Caso tenha recebido esse erro, sua instalação está em um estado inconsistente e você não pode acessar o Administrador. Recomendamos que você reverta para sua versão anterior enquanto resolve esse erro. Para fazer isso, execute um dos seguintes comandos:
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
>Onde `<version>` é a versão do Magento que você estava executando **antes** a atualização. Por exemplo, `2.3.5`.

Siga as diretrizes descritas nas seções a seguir para recuperar-se de um estado inconsistente.

## Se o mecanismo de pesquisa for `mysql`

Antes da versão 2.4, o MySQL era o mecanismo de pesquisa de catálogo padrão, mas MySQL não é mais compatível nessa capacidade. Agora, você deve instalar e configurar o Elasticsearch ou o OpenSearch como mecanismo de pesquisa antes de atualizar para a versão 2.4.

Use os seguintes recursos para ajudar a orientá-lo durante esse processo:

- [Instalar e configurar o mecanismo de pesquisa](../../configuration/search/overview-search.md)
- [Configuração do mecanismo de pesquisa](../../configuration/search/configure-search-engine.md)

Após configurar o mecanismo de pesquisa e reindexar, você estará pronto para atualizar para a versão 2.4.

## Se o mecanismo de pesquisa for `elasticsearch`

O Elasticsearch 6 e anterior não são mais compatíveis.

Um valor de `elasticsearch` indica que sua versão de nível inferior do Adobe Commerce ou Magento Open Source está configurada para usar o Elasticsearch 2.x. Esta versão do Elasticsearch não é mais suportada.

Você deve executar as seguintes tarefas antes de atualizar para a versão 2.4:

1. Atualização para uma versão do Elasticsearch compatível com o Commerce. Consulte [Atualizando o Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obter instruções completas sobre como fazer backup dos dados, detectar possíveis problemas de migração e testar atualizações antes de implantar na produção. Dependendo da sua versão atual do Elasticsearch, uma reinicialização completa do cluster pode ou não ser necessária.

   >[!NOTE]
   >
   >O Elasticsearch exige o JDK 1.8 ou superior. Consulte [Instalar o Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para verificar qual versão do JDK está instalada.

1. [Configurar Elasticsearch](../../configuration/search/configure-search-engine.md) e reindexar.

Após configurar o mecanismo de pesquisa e reindexar, você estará pronto para atualizar para a versão 2.4.
