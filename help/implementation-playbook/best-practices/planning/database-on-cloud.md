---
title: Práticas recomendadas de configuração de banco de dados para implantações em nuvem
description: Saiba como definir configurações de banco de dados e aplicativo para melhorar o desempenho ao implantar o Adobe Commerce na infraestrutura em nuvem.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Práticas recomendadas para configuração de banco de dados

Saiba mais sobre as práticas recomendadas para melhorar o desempenho do banco de dados e trabalhar de forma eficiente com o banco de dados ao implantar o Adobe Commerce na infraestrutura em nuvem.

## Produtos afetados

Adobe Commerce na infraestrutura em nuvem

## Converter todas as tabelas MyISAM em InnoDB

A Adobe recomenda o uso do mecanismo de banco de dados InnoDB. Em uma instalação padrão do Adobe Commerce, todas as tabelas do banco de dados são armazenadas usando o mecanismo do InnoDB. No entanto, alguns módulos de terceiros (extensões) podem introduzir tabelas no formato MyISAM. Após instalar um módulo de terceiros, verifique o banco de dados para identificar quaisquer tabelas no formato `myisam` e convertê-las no formato `innodb`.

### Determinar se um módulo inclui tabelas MyISAM

Você pode analisar o código do módulo de terceiros antes de instalá-lo, para determinar se ele usa tabelas MyISAM.

Se você já tiver instalado uma extensão, execute a seguinte consulta para determinar se o banco de dados tem alguma tabela MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Alterar o mecanismo de armazenamento para o InnoDB

No arquivo `db_schema.xml` declarando a tabela, defina o valor do atributo `engine` do nó `table` correspondente como `innodb`. Para referência, consulte [Configurar esquema declarativo > nó da tabela](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) na documentação do desenvolvedor.

O esquema declarativo foi introduzido no Adobe Commerce na versão 2.3 da infraestrutura em nuvem.

## Configurar o mecanismo de pesquisa recomendado para pesquisa MySQL nativa

A Adobe recomenda que você sempre configure o Elasticsearch ou o OpenSearch para o projeto de infraestrutura do Adobe Commerce na nuvem, mesmo que planeje configurar uma ferramenta de pesquisa de terceiros para o aplicativo do Adobe Commerce. Essa configuração fornece uma opção de fallback caso a ferramenta de pesquisa de terceiros falhe.

O mecanismo de pesquisa usado depende da versão do Adobe Commerce na nuvem instalada:

- Para o Adobe Commerce 2.4.4 e posterior, use o serviço OpenSearch para pesquisa nativa do MySQL.

- Para versões anteriores do Adobe Commerce, use o Elasticsearch.

Para determinar qual mecanismo de pesquisa está em uso no momento, execute o seguinte comando:

```bash
./bin/magento config:show catalog/search/engine
```

Para obter instruções de configuração, consulte o Guia do desenvolvedor do Adobe Commerce na nuvem:

- [Configurar o serviço OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [Configurar o serviço Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## Evitar acionadores personalizados

Evite usar acionadores personalizados, se possível.

Os acionadores são usados para registrar alterações em tabelas de auditoria. O Adobe recomenda configurar o aplicativo para gravar diretamente nas tabelas de auditoria, em vez de usar a funcionalidade de acionador pelos seguintes motivos:

- Os acionadores são interpretados como código e o MySQL não os pré-compila. Conectando o espaço de transação do query, eles adicionam o overhead a um analisador e interpretador para cada query executada com a tabela.
- Os acionadores compartilham o mesmo espaço de transação que as consultas originais e, enquanto essas consultas competem por bloqueios na tabela, os acionadores competem independentemente em bloqueios em outra tabela.

Para saber mais sobre alternativas ao uso de acionadores personalizados, consulte [Acionadores do MySQL](mysql-configuration.md#triggers).

## Atualizar [!DNL ECE-Tools] para a versão 2002.0.21 ou superior {#ece-tools-version}

Para evitar possíveis problemas com bloqueios do cron, atualize as ECE-Tools para a versão 2002.0.21 ou superior. Para obter instruções, consulte [Atualizar `ece-tools` versão](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) na documentação do desenvolvedor.

## Alternar modo indexador com segurança

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Alternar indexadores gera instruções [!DNL data definition language] (DDL) para criar disparadores que podem causar bloqueios de banco de dados. Você pode evitar esse problema colocando o site no modo de manutenção e desabilitando os trabalhos cron antes de alterar a configuração.
Para obter instruções, consulte [Configurar indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) no *Guia de Configuração do Adobe Commerce*.

## Não executar instruções DDL na Produção

Evite executar instruções DDL no ambiente de Produção para evitar conflitos (como modificações e criações de tabela). O processo `setup:upgrade` é uma exceção.

Se você precisar executar uma instrução DDL, coloque o site no modo de manutenção e desabilite o cron (consulte as instruções para alternar índices com segurança na seção anterior).

## Habilitar arquivamento de pedidos

Ative o arquivamento de pedidos do administrador para reduzir o espaço necessário para tabelas de vendas à medida que os dados de pedidos aumentam. O arquivamento economiza espaço em disco do MySQL e melhora o desempenho do check-out.

Consulte [Habilitar arquivamento](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) na documentação do Adobe Commerce Merchant.

## Informações adicionais

- [Mecanismos de Armazenamento MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Pré-requisitos de atualização do Adobe Commerce 2.3.5 para MariaDB](../maintenance/mariadb-upgrade.md)
- [Práticas recomendadas para resolver problemas de desempenho do banco de dados](../maintenance/resolve-database-performance-issues.md)
