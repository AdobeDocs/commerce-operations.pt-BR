---
title: Pré-requisitos de atualização do Adobe Commerce para o MariaDB
description: Saiba como preparar seu banco de dados do Adobe Commerce para atualizar o MariaDB de uma versão anterior.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Pré-requisitos de atualização para o MariaDB

Antes de atualizar o Adobe Commerce na infraestrutura em nuvem, talvez você também precise atualizar seu software de banco de dados se estiver usando o MariaDB. Por exemplo:

- Adobe Commerce 2.4.6 com MariaDB versão 10.5.1 ou superior
- Adobe Commerce 2.3.5 com MariaDB versão 10.3 ou anterior

## Adobe Commerce 2.4.6

A partir de MariaDB 10.5.1, as colunas com formatos temporais antigos são marcadas com um comentário `/* mariadb-5.3 */` na saída das instruções `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE`, bem como na coluna `COLUMN_TYPE` da tabela `INFORMATION_SCHEMA.COLUMNS`. [Consulte a documentação do MariaDB](https://mariadb.com/kb/en/datetime/#internal-format).

O Adobe Commerce não pode mapear as colunas de data para um tipo de dados adequado devido ao comentário MariaDB, o que pode causar um comportamento inesperado no código personalizado.

Para evitar um comportamento inesperado ao atualizar o MariaDB de versões anteriores para a versão 10.6, a Adobe recomenda migrar as colunas para o novo formato interno.

### Configuração padrão

No MariaDB 10.1.2, um novo formato temporal foi introduzido a partir do MySQL 5.6. A variável de sistema `mysql56_temporal_format` permite que o banco de dados converta automaticamente o formato de data antigo para o novo quando uma tabela alterada é executada ou o banco de dados é importado. A configuração padrão para `mysql56_temporal_format` está sempre habilitada no Adobe Commerce na infraestrutura de nuvem.

### Migrar colunas de data

A consulta a seguir mostra a tabela e as colunas afetadas que devem ser migradas após a atualização do MariaDB para 10.5.1 ou posterior:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

A migração das colunas para o novo formato de data interno requer a reimportação do banco de dados ou a execução de alter na coluna identificada com a mesma definição de coluna. A consulta a seguir gera as consultas alter necessárias:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>É importante migrar as colunas para o novo formato de data interno _antes_ de implantar o novo código para evitar um comportamento inesperado.

## Adobe Commerce 2.3.5

Atualização do serviço MariaDB na infraestrutura em nuvem da versão 10.0 ou 10.2 para a versão 10.3, 10.4 ou 10.5. A versão 10.3 e posterior da MariaDB exige que o banco de dados use o formato de linha de tabela dinâmica, e a Adobe Commerce exige o uso do mecanismo de armazenamento InnoDB para tabelas. Este artigo explica como atualizar seu banco de dados para cumprir esses requisitos do MariaDB.

Depois de preparar o banco de dados, envie um tíquete de suporte do Adobe Commerce para atualizar a versão do serviço MariaDB na infraestrutura de nuvem antes de prosseguir com o processo de atualização do Adobe Commerce.

### Preparar seu banco de dados para a atualização

Antes que a equipe de Suporte da Adobe Commerce inicie o processo de atualização, prepare o banco de dados convertendo as tabelas do banco de dados:

- Converter o formato de linha de `COMPACT` para `DYNAMIC`
- Alterar o mecanismo de armazenamento de `MyISAM` para `InnoDB`

Lembre-se das seguintes considerações ao planejar e agendar a conversão:

- A conversão de `COMPACT` em `DYNAMIC` tabelas pode levar várias horas com um banco de dados grande.

- Para evitar a corrupção de dados, não conclua o trabalho de conversão em um site ativo.

- Conclua o trabalho de conversão durante um período de tráfego baixo no site.

- Alterne seu site para o [modo de manutenção](../../../installation/tutorials/maintenance-mode.md) antes de executar os comandos para converter tabelas de banco de dados.

#### Converter formato de linha da tabela do banco de dados

Você pode converter tabelas em um nó no cluster. As alterações são replicadas automaticamente para os outros nós de serviço.

1. No ambiente de infraestrutura em nuvem do Adobe Commerce, use o SSH para se conectar ao nó 1.

1. Faça logon no MariaDB.

1. Identifique as tabelas a serem convertidas do formato compacto para o dinâmico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Determine os tamanhos da tabela para poder agendar o trabalho de conversão.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Tabelas maiores demoram mais para serem convertidas. Revise as tabelas e coloque o trabalho de conversão em lote por prioridade e tamanho da tabela para ajudar a planejar as janelas de manutenção necessárias.

1. Converter todas as tabelas em formato dinâmico, uma de cada vez.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Converter formato de armazenamento de tabela de banco de dados

Você pode converter tabelas em um nó no cluster. As alterações são replicadas automaticamente para os outros nós de serviço.

O processo para converter o formato de armazenamento é diferente para projetos do Adobe Commerce Starter e do Adobe Commerce Pro.

- Para arquitetura Starter, use o comando MySQL `ALTER` para converter o formato.
- Na arquitetura Pro, use os comandos MySQL `CREATE` e `SELECT` para criar uma tabela de banco de dados com armazenamento `InnoDB` e copiar os dados da tabela existente para a nova tabela. Esse método garante que as alterações sejam replicadas em todos os nós do cluster.

**Converter formato de armazenamento de tabela para projetos do Adobe Commerce Pro**

1. Identifique as tabelas que usam o armazenamento `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converta todas as tabelas para o formato de armazenamento `InnoDB`, uma de cada vez.

   - Renomeie a tabela existente para evitar conflitos de nome.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Crie uma tabela que use o armazenamento `InnoDB` usando os dados da tabela existente.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Verifique se a nova tabela tem todos os dados necessários.

   - Exclua a tabela original que você renomeou.


**Converter formato de armazenamento de tabela para projetos Adobe Commerce Starter**

1. Identifique as tabelas que usam o armazenamento `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converter tabelas que usam o armazenamento `MyISAM` para o armazenamento `InnoDB`.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Verifique a conversão do banco de dados

No dia anterior à atualização programada para o MariaDB versão 10.3, 10.4 ou 10.6, verifique se todas as tabelas têm o formato de linha e o mecanismo de armazenamento corretos. A verificação é necessária porque as implantações de código feitas após a conclusão da conversão podem fazer com que algumas tabelas sejam revertidas para a configuração original.

1. Faça logon no banco de dados.

1. Verifique se há tabelas que ainda tenham o formato de linha `COMPACT`.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Verifique se há tabelas que ainda usam o formato de armazenamento `MyISAM`

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Se alguma tabela tiver sido revertida, repita as etapas para alterar o formato da linha da tabela e o mecanismo de armazenamento.

### Alterar o mecanismo de armazenamento

Consulte [Converter tabelas MyISAM em InnoDB](../planning/database-on-cloud.md).
