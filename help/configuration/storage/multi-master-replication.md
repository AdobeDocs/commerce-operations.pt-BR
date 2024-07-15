---
title: Replicação de banco de dados
description: Veja os benefícios de configurar a replicação de banco de dados.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Replicação de banco de dados

{{ee-only}}

{{deprecate-split-db}}

A configuração da replicação de banco de dados oferece os seguintes benefícios:

- Fornece backup de dados
- Habilita a análise de dados sem afetar o banco de dados mestre
- Escalabilidade

Os bancos de dados MySQL são replicados de forma assíncrona, o que significa que os escravos não precisam ser conectados permanentemente para receber atualizações do mestre.

## Configurar replicação de banco de dados

Uma discussão detalhada sobre replicação de banco de dados está além do escopo deste guia. Para configurá-lo, você pode consultar um recurso como:

- [Documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Como configurar a replicação subordinada principal no MySQL (digitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

O Commerce fornece configurações MySQL de exemplo para seus bancos de dados subordinados. Uma configuração simples é fornecida com a classe `ResourceConnections` `README.md`.

O item a seguir está mais avançado e é fornecido apenas para fins informativos:

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

## Aprimoramento de desempenho

Para melhorar o desempenho da replicação master-slave, você pode filtrar algumas tabelas em instâncias slave. Recomendamos filtrar todas as tabelas temporárias com o padrão de nome `search\_tmp\_%` que são usadas para pesquisa no catálogo.

Para fazer isso, adicione a seguinte linha ao arquivo `my.cnf` nas instâncias subordinadas:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
