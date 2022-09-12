---
title: Diretrizes do MySQL
description: Siga estas etapas para instalar e configurar o MySQL e o MariaDB para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Diretrizes gerais do MySQL

Consulte [Requisitos do sistema](../../system-requirements.md) para versões compatíveis do MySQL.

Adobe _strong_ A recomenda observar o seguinte padrão ao configurar seu banco de dados:

* Adobe Commerce e Magento Open Source use [Acionadores do banco de dados MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) para melhorar o acesso ao banco de dados durante a reindexação. Eles são criados quando o modo de indexador é definido como [programação](../../../configuration/cli/manage-indexers.md#configure-indexers). O aplicativo não suporta acionadores personalizados no banco de dados porque os acionadores personalizados podem introduzir incompatibilidades com versões futuras do Adobe Commerce e do Magento Open Source.
* Familiarize-se com [essas limitações potenciais do acionador do MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) antes de continuar.
* Para aprimorar a postagem de segurança do banco de dados, habilite o [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) O modo SQL impede o armazenamento de valores de dados inválidos, o que pode causar interações indesejadas no banco de dados.
* Adobe Commerce e Magento Open Source do _not_ oferecem suporte à replicação baseada em instruções MySQL. Certifique-se de usar _only_ [replicação baseada em linha](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce e Magento Open Source atualmente em uso `CREATE TEMPORARY TABLE` instruções dentro de transações, que são [incompatível](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) com implementações de banco de dados, use a replicação baseada em GTID, como [Instâncias de segunda geração do SQL da Google Cloud](https://cloud.google.com/sql/docs/features#differences). Considere o MySQL for Cloud SQL 8.0 como uma alternativa.

>[!NOTE]
>
>Se o servidor Web e o servidor de banco de dados estiverem em hosts diferentes, execute as tarefas discutidas neste tópico no host do servidor de banco de dados e consulte [Configurar uma conexão remota de banco de dados do MySQL](mysql-remote.md).

## Instalação do MySQL no Ubuntu

O Adobe Commerce e o Magento Open Source 2.4 exigem uma instalação limpa do MySQL 8.0. Siga os links abaixo para obter instruções sobre como instalar o MySQL em sua máquina.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Se você espera importar grandes números de produtos, é possível aumentar o valor de [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) que é maior que o padrão, 16 MB.

>[!NOTE]
>
>O valor padrão se aplica ao Adobe Commerce na infraestrutura de nuvem _e_ Projetos no local. Os clientes do Adobe Commerce na infraestrutura em nuvem Pro devem abrir um tíquete de suporte para aumentar o `max_allowed_packet` valor. Os clientes do Adobe Commerce on cloud Infrastructure Starter podem aumentar o valor ao atualizar a configuração no `/etc/mysql/mysql.cnf` arquivo.

Para aumentar o valor, abra o `/etc/mysql/mysql.cnf` em um editor de texto e localize o valor de `max_allowed_packet`. Salve as alterações no `mysql.cnf` , feche o editor de texto e reinicie o MySQL (`service mysql restart`).

Para verificar opcionalmente o valor definido, digite o seguinte comando em uma `mysql>` prompt:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Então, [Configurar a instância do banco de dados](#configuring-the-database-instance).

## Alterações no MySQL 8

Para Adobe Commerce e Magento Open Source 2.4, adicionamos suporte para MySQL 8.
Esta seção descreve as principais alterações no MySQL 8 que os desenvolvedores devem conhecer.

### Largura removida para tipos inteiros (preenchimento)

A especificação de largura de exibição para tipos de dados inteiros (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) foi descontinuada no MySQL 8.0.17. As instruções que incluem definições de tipo de dados em sua saída não mostram mais a largura de exibição para tipos inteiros, exceto para TINYINT(1). Os MySQL Connectors consideram que as colunas TINYINT(1) são originadas como colunas BOOLEAN. Essa exceção permite que eles continuem a fazer essa suposição.

#### Exemplo

Descreva admin_user em mysql 8.19

| Campo | Tipo | Null | Chave | Padrão | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NÃO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | SIM |  | `NULL` |  |
| `lastname` | `varchar(32`) | SIM |  | `NULL` |  |
| `email` | `varchar(128)` | SIM |  | `NULL` |  |
| `username` | `varchar(40)` | SIM | UNI | `NULL` |  |
| `password` | `varchar(255)` | NÃO |  | `NULL` |  |
| `created` | `timestamp` | NÃO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NÃO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` na atualização `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | SIM |  | `NULL` |  |
| `lognum` | `smallint unsigned` | NÃO |  | `0` |  |

Exceto para _TINYINT(1)_, todo o preenchimento do número inteiro (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) deve ser removido do `db_schema.xml` arquivo.

Para obter mais informações, consulte [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportamento ORDEM POR padrão

Antes de 8.0, as entradas eram classificadas pela chave estrangeira. A ordem de classificação padrão depende do mecanismo usado.
Sempre especifique uma ordem de classificação se o código depender de uma classificação específica.

### Qualificadores ASC e DESC obsoletos para GROUP BY

A partir do MySQL 8.0.13, o `ASC` ou `DESC` qualificadores para `GROUP BY` as cláusulas foram removidas. Queries que antes dependiam de `GROUP BY` a classificação pode produzir resultados diferentes das versões anteriores do MySQL. Para produzir uma determinada ordem de classificação, forneça uma `ORDER BY` cláusula.

## Commerce e MySQL 8

Houve algumas alterações no Adobe Commerce e no Magento Open Source para dar suporte adequado ao MySQL 8.

### Consulta e Inserir Comportamento

Adobe Commerce e Magento Open Source desabilitaram o comportamento de validação regular definindo SET SQL_MODE=&#39;&#39; em `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Com a validação desativada, é possível que o MySQL trunque os dados. No MySQL, o comportamento do Query foi alterado: `Select * on my_table where IP='127.0.0.1'` O não retorna mais resultados porque o endereço IP agora é visto corretamente como uma string, em vez de um inteiro.

## Atualização do MySQL 5.7 para o MySQL 8

Para atualizar adequadamente o MySQL da versão 5.7 para a 8, siga estas etapas em ordem:

1. Atualize o Adobe Commerce ou o Magento Open Source para 2.4.0. Teste tudo e verifique se o sistema funciona conforme o esperado.
1. Ativar o modo de manutenção:

   ```bash
   bin/magento maintenance:enable
   ```

1. Faça um backup do banco de dados:

   ```bash
   bin/magento setup:backup --db
   ```

1. Atualize o MySQL para a versão 8.
1. Importe os dados de backup no MySQL.
1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Desativar modo de manutenção:

   ```bash
   bin/magento maintenance:disable
   ```

## Configuração da instância do banco de dados

Esta seção discute como criar uma instância de banco de dados para Adobe Commerce ou Magento Open Source. Embora uma nova instância de banco de dados seja recomendada, você pode opcionalmente instalar o Adobe Commerce ou o Magento Open Source com uma instância de banco de dados existente.

Para configurar uma instância de banco de dados MySQL:

1. Faça logon no servidor de banco de dados como qualquer usuário.
1. Vá para um prompt de comando do MySQL:

   ```bash
   mysql -u root -p
   ```

1. Digite o MySQL `root` senha do usuário, quando solicitado.
1. Insira os seguintes comandos na ordem mostrada para criar uma instância de banco de dados chamada `magento` com nome de usuário `magento`:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Enter `exit` para sair do prompt de comando.

1. Verifique o banco de dados:

   ```bash
   mysql -u magento -p
   ```

   Se o monitor MySQL for exibido, você criou o banco de dados corretamente. Se um erro for exibido, repita os comandos anteriores.

1. Se o servidor Web e o servidor de banco de dados estiverem em hosts diferentes, execute as tarefas discutidas neste tópico no host do servidor de banco de dados e consulte [Configurar uma conexão remota de banco de dados do MySQL](mysql-remote.md).

   Recomendamos que você configure a instância do banco de dados conforme apropriado para sua empresa. Ao configurar seu banco de dados, lembre-se do seguinte:

   * Indexadores exigem maior `tmp_table_size` e `max_heap_table_size` valores (por exemplo, 64 M). Se você configurar o `batch_size` , você pode ajustar esse valor junto com as configurações de tamanho da tabela para melhorar o desempenho do indexador. Consulte a [Guia de otimização](../../../performance/configuration.md) para obter mais informações.

   * Para obter o melhor desempenho, verifique se todas as tabelas de índice do MySQL e Adobe Commerce ou Magento Open Source podem ser mantidas na memória (por exemplo, configure `innodb_buffer_pool_size`).

   * A reindexação no MariaDB 10.4 leva mais tempo em comparação com outras versões de MariaDB ou MySQL. Consulte [Práticas recomendadas de configuração](../../../performance/configuration.md#indexers).

1. Para MySQL `TIMESTAMP` campos para seguir as preferências e a composição esperadas pela arquitetura de esquema declarativa do aplicativo, a variável do sistema `explicit_defaults_for_timestamp` deve ser definido como `on`.

   Referências:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Se esta configuração não estiver ativada, `bin/magento setup:db:status` sempre relata que a variável `Declarative Schema is not up to date`.

>[!NOTE]
>
>O `explicit_defaults_for_timestamp` está obsoleta. Esta configuração controla comportamentos TIMESTAMP obsoletos que serão removidos em uma versão futura do MySQL. Quando esses comportamentos forem removidos, a variável `explicit_defaults_for_timestamp` também é removida.

>[!WARNING]
>
>Para projetos de infraestrutura em nuvem do Adobe Commerce, a variável `explicit_defaults_for_timestamp` a configuração do MySQL (MariaDB) assume como padrão _OFF_.

A reindexação no MariaDB 10.4 leva mais tempo em comparação com outras versões de MariaDB ou MySQL. Para acelerar a reindexação, recomendamos configurar esses parâmetros de configuração do MariaDB:

* otimizer_switch=&#39;rowid_filter=off&#39;
* otimizer_use_condition_seltivity = 1
