---
title: Pré-requisitos de atualização do Adobe Commerce 2.3.5 para o MariaDB
description: Saiba como preparar seu banco de dados do Adobe Commerce para atualizar do Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 071e88c6a07df0f74b6d4b09cce858710c9332cc
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Pré-requisitos de atualização do Adobe Commerce 2.3.5

Este artigo explica como preparar seu banco de dados ao atualizar para o Adobe Commerce 2.3.5 da versão 2.3.4 ou anterior.

Essa atualização requer que a equipe de suporte atualize o MariaDB na infraestrutura de nuvem de MariaDB 10.0 para 10.2 para atender aos requisitos da versão 2.3.5 e posterior do Adobe Commerce.

## Produto e versões afetados

Adobe Commerce na infraestrutura de nuvem com Adobe Commerce versão 2.3.4 ou anterior e MariaDB versão 10.0 ou anterior.

## Preparar seu banco de dados para a atualização

Antes de a equipe de suporte da Adobe Commerce iniciar o processo de atualização, prepare o banco de dados convertendo as tabelas do banco de dados:

- Converter o formato de linha de `COMPACT` para `DYNAMIC`
- Converter o mecanismo de armazenamento de `MyISAM` para `InnoDB`

Lembre-se das seguintes considerações ao planejar e programar a conversão:

- Conversão de `COMPACT` para `DYNAMIC` tabelas podem levar várias horas com um banco de dados grande.

- Para evitar a corrupção de dados, não conclua o trabalho de conversão em um site ativo.

- Conclua o trabalho de conversão durante um período de tráfego baixo no site.

- Mudar seu site para [modo de manutenção](../../../installation/tutorials/maintenance-mode.md) antes de executar os comandos para converter tabelas de banco de dados.

### Converter formato de linha da tabela do banco de dados

Você pode converter tabelas em um nó do cluster. As alterações são replicadas automaticamente para os outros nós de serviço.

1. No ambiente de infraestrutura em nuvem do Adobe Commerce, use SSH para se conectar ao nó 1.

1. Efetue login no MariaDB.

1. Identificar as tabelas a serem convertidas do formato compacto para dinâmico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
   ```

1. Determine os tamanhos da tabela para agendar o trabalho de conversão.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Tabelas maiores demoram mais para serem convertidas. Revise as tabelas e agrupe o trabalho de conversão em lote por prioridade e tamanho da tabela para ajudar a planejar as janelas de manutenção necessárias.

1. Converta todas as tabelas em formato dinâmico, uma de cada vez.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### Converter formato de armazenamento de tabela de banco de dados

Você pode converter tabelas em um nó do cluster. As alterações são replicadas automaticamente para os outros nós de serviço.

O processo para converter o formato de armazenamento é diferente para projetos Adobe Commerce Starter e Adobe Commerce Pro.

- Para arquitetura Inicial, use o MySQL `ALTER` para converter o formato.
- Na arquitetura Pro, use o MySQL `CREATE` e `SELECT` comandos para criar uma tabela de banco de dados com `InnoDB` e copie os dados da tabela existente para a nova tabela. Esse método garante que as alterações sejam replicadas para todos os nós no cluster.

**Converter formato de armazenamento de tabela para projetos do Adobe Commerce Pro**

1. Identificar tabelas que usam `MyISAM` armazenamento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converter todas as tabelas em `InnoDB` formato de armazenamento, um de cada vez.

   - Renomeie a tabela existente para evitar conflitos de nome.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Crie uma tabela que use `InnoDB` armazenamento usando os dados da tabela existente.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Verifique se a nova tabela tem todos os dados necessários.

   - Exclua a tabela original que você renomeou.


**Converter formato de armazenamento de tabela para projetos Adobe Commerce Starter**

1. Identificar tabelas que usam `MyISAM` armazenamento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converter tabelas que usam `MyISAM` armazenamento para `InnoDB` armazenamento.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Verificar a conversão do banco de dados

No dia anterior à atualização programada para a versão 10.2 do MariaDB, verifique se todas as tabelas têm o formato de linha e mecanismo de armazenamento corretos. A verificação é necessária porque implantações de código feitas após a conclusão da conversão podem fazer com que algumas tabelas sejam revertidas para a configuração original.

1. Faça logon no banco de dados.

1. Verifique se há tabelas que ainda tenham a variável `COMPACT` formato de linha.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Verifique se há tabelas que ainda usam o `MyISAM` formato de armazenamento

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Se alguma tabela tiver sido revertida, repita as etapas para alterar o formato da linha da tabela e o mecanismo de armazenamento.

## Informações adicionais

[Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](../planning/database-on-cloud.md)
