---
title: Práticas recomendadas para resolver problemas de desempenho do banco de dados
description: Saiba como corrigir problemas do banco de dados que atrasam o desempenho em Adobe Systems Comércio sites implantados em infraestrutura em nuvem.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Práticas recomendadas para resolver problemas de desempenho do banco de dados

Este artigo discute como corrigir problemas de banco de dados que afetam negativamente o desempenho do banco de dados em Adobe Systems Comércio em sites de infraestrutura em nuvem.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem

## Identificar e resolver consultas longas

Determine se há consultas MySQL de execução lenta. Dependendo do plano de infraestrutura em nuvem do Adobe Commerce e, portanto, da disponibilidade de ferramentas, você pode fazer o seguinte.

### Analisar consultas de banco de dados com o MySQL

Você pode usar o MySQL para identificar e resolver consultas de longa execução em qualquer projeto do Adobe Commerce na infraestrutura em nuvem.

1. Execute a [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) declaração.
1. Se você vir consultas de longa duração, execute [MySQL `EXPLAIN` e `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) para cada uma delas, para descobrir o que faz com que os query executem por muito tempo.
1. Com base nos problemas encontrados, tome medidas para corrigir a query para que ela seja executada mais rapidamente.

### Analise queries usando o Percona ToolKit (somente para arquitetura Pro)

Se o Adobe Systems Comércio projeto for implantado na arquitetura Pro, você poderá usar o Percona Toolkit para analisar queries.

1. Execute o `pt-query-digest --type=slowlog` comando em logs de query lentos do MySQL.
   * Para encontrar a localização dos logs de consulta lenta, consulte **[!UICONTROL Log locations > Service Logs]**(https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs) em nossa documentação do desenvolvedor.
   * Consulte a documentação do [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. Com base nos problemas encontrados, siga as etapas para corrigir a consulta para que ela seja executada mais rapidamente.

## Verificar se todas as tabelas têm uma chave primária

A definição de chaves primárias é um requisito para um bom design de banco de dados e tabela. As chaves primárias fornecem uma maneira de identificar exclusivamente uma única linha em qualquer tabela.

Se você tiver tabelas sem uma chave primária, o mecanismo de banco de dados padrão para Adobe Systems Comércio (InnoDB) usará a primeira chave não nula exclusiva como a chave primária. Se nenhuma chave exclusiva estiver disponível, InnoDB criará uma oculto chave primária (6 bytes). O problema com uma chave primária implicitamente definida é que você não tem controle sobre ela. Além disso, o valor implícito é atribuído globalmente para todas as tabelas sem chaves primárias. Essa configuração pode causar problemas de contenção se você executar gravações simultâneas nessas tabelas. Isso pode cliente potencial a problemas de desempenho porque as tabelas também compartilham o aumento global dos oculto principal índice principal.

Evite esses problemas definindo uma chave primária para qualquer tabela que não tenha uma.

### Identificar e atualizar tabelas sem uma chave primária

1. Identifique tabelas sem uma chave primária usando a seguinte consulta SQL:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Para qualquer tabela sem uma chave primária, adicione uma chave primária atualizando o `db_schema.xml` (o esquema declarativo) com um nó semelhante ao seguinte:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Ao adicionar o nó, substitua as variáveis `referenceID` e `column name` pelos valores personalizados.

Para obter mais informações, consulte [Configurar esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) na documentação do desenvolvedor.

## Identificar e remover índices duplicados

Identifique quaisquer duplicado índices no banco de dados e remova-os.

### Verificar índices de duplicado

Para verificar se há índices duplicado na arquitetura nuvem Pro ou Starter, execute os seguintes query SQL.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

A query retorna os nomes das colunas e os nomes de qualquer índice duplicado.

Comerciantes de arquitetura pro também podem executar a verificação usando o comando Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` .

### Índices duplicado do Remover

Use a [Instrução DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) do SQL para remover índices duplicados.

```SQL
DROP INDEX
```

## Informações adicionais

[Práticas recomendadas de configuração de banco de dados para implantações em nuvem](../planning/database-on-cloud.md)
