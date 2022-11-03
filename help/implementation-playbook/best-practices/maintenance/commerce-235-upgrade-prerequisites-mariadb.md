---
title: Pré-requisitos de atualização do Adobe Commerce 2.3.5 para o MariaDB
description: Saiba como preparar seu banco de dados do Adobe Commerce para atualizar do Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Pré-requisitos de atualização do Adobe Commerce 2.3.5

Este artigo explica como preparar seu banco de dados ao atualizar para o Adobe Commerce 2.3.5 da versão 2.3.4 ou anterior.

Essa atualização requer que a equipe de suporte atualize o MariaDB na infraestrutura de nuvem de MariaDB 10.0 para 10.2 para atender aos requisitos do Adobe Commerce . Adobe Commerce versão 2.3.5 e posterior.

## Produto e versões afetados

Adobe Commerce na infraestrutura de nuvem com Adobe Commerce versão 2.3.4 ou anterior e MariaDB versão 10.0 ou anterior.

## Preparar seu banco de dados para a atualização

Antes de a equipe de suporte da Adobe Commerce iniciar o processo de atualização, prepare seu banco de dados convertendo o formato de todas as tabelas de `COMPACT` para `DYNAMIC`. Você também deve converter o tipo de mecanismo de armazenamento de `MyISAM` para `InnoDB`.

Lembre-se das diretrizes a seguir ao criar o plano e o agendamento para conversão do banco de dados.

- Conversão de `COMPACT` para `DYNAMIC` tabelas podem levar várias horas com um banco de dados grande.

- Para evitar corrupção de dados, não execute a conversão quando o site estiver ativo.

- Conclua o trabalho de conversão durante um período de tráfego baixo no site.

- Mudar seu site para [modo de manutenção](../../../installation/tutorials/maintenance-mode.md) antes de executar o `ALTER` comandos.

### Converter tabelas de banco de dados

Você pode converter tabelas em um nó do cluster. As alterações serão replicadas para os outros nós principais no cluster.

1. No ambiente de infraestrutura em nuvem do Adobe Commerce, use SSH para se conectar ao nó 1.

1. Efetue login no MariaDB.

1. Converta o formato da tabela.

   - Identificar as tabelas a serem convertidas do formato compacto para dinâmico.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Determine os tamanhos da tabela para agendar o trabalho de conversão.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      Tabelas maiores demoram mais para serem convertidas. Você deve planejar adequadamente ao colocar e sair do modo de manutenção quais lotes de tabelas serão convertidos em qual ordem, de modo a planejar os horários das janelas de manutenção necessárias

   - Converta todas as tabelas em formato dinâmico, uma de cada vez.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Atualize o mecanismo de armazenamento de tabela.

   - Identificar tabelas que usam `MyISAM` armazenamento.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Converter tabelas que usam `MyISAM` armazenamento para `InnoDB` armazenamento.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Verifique a conversão.

   Essa etapa é necessária porque as implantações de código feitas após a conclusão da conversão podem fazer com que algumas tabelas sejam revertidas para a configuração original.

   - O dia antes da atualização programada para o MariaDB versão 10.2, faça logon no banco de dados e execute as consultas para verificar o formato e o mecanismo de armazenamento.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Se alguma tabela tiver sido revertida, repita as etapas para alterar o formato da tabela e o mecanismo de armazenamento.

## Informações adicionais

[Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](../planning/database-on-cloud.md)
