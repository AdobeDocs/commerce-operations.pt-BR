---
title: Práticas recomendadas para resolver problemas de desempenho do banco de dados
description: Saiba como corrigir problemas de banco de dados que tornam o desempenho lento em sites do Adobe Commerce implantados na infraestrutura em nuvem.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---


<!--Consider moving this topic to the Maintenance section-->

# Práticas recomendadas para resolver problemas de desempenho do banco de dados

Este artigo discute como corrigir problemas de banco de dados que afetam negativamente o desempenho do banco de dados no Adobe Commerce em sites de infraestrutura em nuvem.

## Versões afetadas

Adobe Commerce na infraestrutura de nuvem

## Identificar e resolver consultas de longa duração

Determine se você tem algum query MySQL em execução lenta. Dependendo do seu Adobe Commerce sobre o plano de infraestrutura em nuvem e, portanto, da disponibilidade das ferramentas, você pode fazer o seguinte.

### Analisar consultas de banco de dados com MySQL

Você pode usar o MySQL para identificar e resolver consultas de longa duração em qualquer projeto de infraestrutura em nuvem do Adobe Commerce.

1. Execute o [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) instrução.
1. Se você vir consultas de longa execução, execute [MySQL `EXPLAIN` e `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) para cada um deles, para descobrir o que faz o query ser executado por um longo tempo.
1. Com base nos problemas encontrados, execute as etapas necessárias para corrigir o query de forma que ele seja executado mais rapidamente.

### Analisar consultas usando o Percona Toolkit (somente para a arquitetura Pro)

Se seu projeto do Adobe Commerce for implantado na arquitetura Pro, você poderá usar o Percona Toolkit para analisar consultas.

1. Execute o `pt-query-digest --type=slowlog` comando em logs de consulta lentos do MySQL.
   * Para localizar a localização dos logs de consulta lentos, consulte **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) na documentação do desenvolvedor.
   * Consulte a [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) documentação.
1. Com base nos problemas encontrados, execute as etapas necessárias para corrigir o query de forma que ele seja executado mais rapidamente.

## Verifique se todas as tabelas têm uma chave primária

A definição de chaves primárias é um requisito para um bom design de banco de dados e tabela. As chaves primárias fornecem uma maneira de identificar exclusivamente uma única linha em qualquer tabela.

Se você tiver tabelas sem uma chave primária, o mecanismo de banco de dados padrão para Adobe Commerce (InnoDB) usará a primeira chave exclusiva não nula como chave primária. Se nenhuma chave exclusiva estiver disponível, o InnoDB criará uma chave primária oculta (6 bytes). O problema com uma chave primária definida implicitamente é que você não tem controle sobre ela. Além disso, o valor implícito é atribuído globalmente para todas as tabelas sem chaves primárias. Essa configuração pode causar problemas de contenção se você executar gravações simultâneas nessas tabelas. Isso pode levar a problemas de desempenho, pois as tabelas também compartilham o incremento do índice da chave primária oculta global.

Evite esses problemas definindo uma chave primária para qualquer tabela que não tenha uma.

### Identificar e atualizar tabelas sem uma chave primária

1. Identifique tabelas sem uma chave primária usando a seguinte consulta SQL:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Para qualquer tabela que não tenha uma chave primária, adicione uma chave primária atualizando o `db_schema.xml` (o schema declarativo) com um nó semelhante ao seguinte:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Ao adicionar o nó, substitua o `referenceID` e `column name` com seus valores personalizados.

Para obter mais informações, consulte [Configurar schema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) na documentação do desenvolvedor.

## Identificar e remover índices duplicados

Identifique quaisquer índices duplicados no banco de dados e remova-os.

### Verificar índices duplicados

Para verificar índices duplicados na arquitetura de nuvem Pro ou Starter, execute a seguinte consulta SQL.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

A query retorna os nomes das colunas e os nomes de qualquer índice duplicado.

Os comerciantes de arquitetura Pro também podem executar a verificação usando o Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` comando.

### Remover índices duplicados

Usar o SQL [Instrução DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) para remover índices duplicados.

```SQL
DROP INDEX
```

## Informações adicionais

[Práticas recomendadas de configuração de banco de dados para implantações em nuvem](../planning/database-on-cloud.md)

