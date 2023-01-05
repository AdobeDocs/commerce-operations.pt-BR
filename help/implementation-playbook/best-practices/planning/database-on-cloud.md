---
title: Práticas recomendadas de configuração de banco de dados para implantações em nuvem
description: Saiba como configurar as configurações do banco de dados e do aplicativo para melhorar o desempenho ao implantar o Adobe Commerce na infraestrutura em nuvem.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# Práticas recomendadas para a configuração do banco de dados

Saiba mais sobre as práticas recomendadas para melhorar o desempenho do banco de dados e trabalhar com o banco de dados com eficiência ao implantar o Adobe Commerce na infraestrutura em nuvem.

## Produtos afetados

Adobe Commerce na infraestrutura de nuvem

## Converter todas as tabelas do MyISAM para InnoDB

O Adobe recomenda o uso do mecanismo de banco de dados InnoDB. Em uma instalação padrão do Adobe Commerce, todas as tabelas no banco de dados são armazenadas usando o mecanismo InnoDB. No entanto, alguns módulos de terceiros (extensões) podem introduzir tabelas no formato MyISAM . Depois de instalar um módulo de terceiros, verifique o banco de dados para identificar qualquer tabela em `myisam` formatar e converter em `innodb` formato.

### Determine se um módulo inclui tabelas do MyISAM

Você pode analisar o código do módulo de terceiros antes de instalá-lo, para determinar se ele usa as tabelas do MyISAM.

Se você já tiver instalado uma extensão, execute a seguinte consulta para determinar se o banco de dados tem alguma tabela MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Alterar o mecanismo de armazenamento para InnoDB

No `db_schema.xml` arquivo declarando a tabela, defina o `engine` valor do atributo para o `table` nó para `innodb`. Para referência, consulte [Configurar schema declarativo > nó de tabela](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) na documentação do desenvolvedor.

O esquema declarativo foi introduzido no Adobe Commerce na versão 2.3 da infraestrutura em nuvem.

## Configurar o mecanismo de pesquisa recomendado para pesquisa nativa do MySQL

O Adobe recomenda que você sempre configure o Elasticsearch ou o OpenSearch para o seu projeto Adobe Commerce na infraestrutura em nuvem, mesmo que planeje configurar uma ferramenta de pesquisa de terceiros para o seu aplicativo Adobe Commerce. Essa configuração fornece uma opção de fallback caso a ferramenta de pesquisa de terceiros falhe.

O mecanismo de pesquisa usado depende da Adobe Commerce na versão em nuvem instalada:

- Para o Adobe Commerce 2.4.4 e posterior, use o serviço OpenSearch para pesquisa nativa do MySQL.

- Para versões anteriores do Adobe Commerce, use Elasticsearch.

Para determinar qual mecanismo de pesquisa está em uso, execute o seguinte comando:

```bash
./bin/magento config:show catalog/search/engine
```

Para obter instruções de configuração, consulte o Guia do desenvolvedor para Adobe Commerce na nuvem:

- [Configurar o serviço OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configurar o serviço Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Evitar acionadores personalizados

Evite usar acionadores personalizados, se possível.

Os Triggers são usados para registrar alterações em tabelas de auditoria. O Adobe recomenda configurar o aplicativo para gravar diretamente nas tabelas de auditoria em vez de usar a funcionalidade do acionador pelos seguintes motivos:

- Os acionadores são interpretados como código e o MySQL não os pré-compila. Aderindo ao espaço de transações do seu query, eles adicionam a sobrecarga a um analisador e interpretador para cada query executada com a tabela.
- Os acionadores compartilham o mesmo espaço de transações que as consultas originais e, enquanto essas consultas competem por bloqueios na tabela, os acionadores competem independentemente em bloqueios em outra tabela.

Para saber mais sobre as alternativas para usar acionadores personalizados, consulte [Usar acionadores MySQL com eficácia](mysql-triggers-usage.md) na nossa base de conhecimento de apoio.

## Atualizar [!DNL ECE-Tools] para versão 2002.0.21 ou superior {#ece-tools-version}

Para evitar possíveis problemas com bloqueios do cron, atualize o ECE-Tools para a versão 2002.0.21 ou superior. Para obter instruções, consulte [Atualizar `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) na documentação do desenvolvedor.

## Alternar o modo indexador com segurança

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

A alternância de indexadores gera [!DNL data definition language] (DDL) instruções para criar acionadores que podem causar bloqueios de banco de dados. Você pode evitar esse problema colocando seu site no modo de manutenção e desativando tarefas do cron antes de alterar a configuração.
Para obter instruções, consulte [Configurar indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) no *Guia de configuração do Adobe Commerce*.

## Não executar instruções DDL em produção

Evite executar instruções DDL no ambiente de Produção para evitar conflitos (como modificações de tabela e criações). O `setup:upgrade` O processo é uma exceção.

Se você precisar executar uma instrução DDL, coloque o site no modo de manutenção e desative o cron (consulte as instruções para alternar índices com segurança na seção anterior).

## Ativar arquivamento de pedidos

Habilite o arquivamento de pedidos do Administrador para reduzir o espaço necessário para tabelas de vendas à medida que seus dados de pedidos crescem. O arquivamento economiza espaço em disco do MySQL e melhora o desempenho do check-out.

Consulte [Ativar arquivamento](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) na documentação do Adobe Commerce Merchant.

## Informações adicionais

- [Mecanismos de armazenamento MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Pré-requisitos de atualização do Adobe Commerce 2.3.5 para o MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Práticas recomendadas para resolver problemas de desempenho do banco de dados](../maintenance/resolve-database-performance-issues.md)
