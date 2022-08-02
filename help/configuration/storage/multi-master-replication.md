---
title: Replicação de banco de dados
description: Veja os benefícios da configuração da replicação do banco de dados.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Replicação de banco de dados

{#ee-only}

{{deprecate-split-db}}

A configuração da replicação do banco de dados oferece os seguintes benefícios:

- Fornece backup de dados
- Permite a análise de dados sem afetar o banco de dados principal
- Escalabilidade

Os bancos de dados MySQL são replicados de forma assíncrona, o que significa que os escravos não precisam ser conectados permanentemente para receber atualizações do principal.

## Configurar replicação de banco de dados

Uma discussão detalhada sobre replicação de banco de dados está além do escopo desse guia. Para configurá-lo, consulte um recurso como:

- [Documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Como configurar a replicação Principal de escravos no MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

O Commerce fornece exemplos de configurações do MySQL para seus bancos de dados escravos. Uma configuração simples é fornecida com a variável `ResourceConnections` classe `README.md`.

O seguinte é mais avançado e é fornecido apenas para suas informações:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Melhoria no desempenho

Para melhorar o desempenho da replicação de escravos principais, você pode filtrar algumas tabelas em instâncias escravas. Recomendamos filtrar todas as tabelas temporárias com o padrão de nome `search\_tmp\_%` usados para [catálogo](https://glossary.magento.com/catalog) pesquisar.

Para fazer isso, adicione a seguinte linha em `my.cnf` nas instâncias do subordinado:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
