---
source-git-commit: d7926b9150137813b1161581bb1d7884a6fe11e9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# Definições de configuração do MariaDB

A reindexação no MariaDB 10.4 e 10.6 leva mais tempo em comparação com as versões anteriores do MariaDB ou MySQL. Para acelerar a reindexação, recomendamos definir esses parâmetros de configuração do MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Se ocorrer degradação de desempenho não relacionada à indexação após a atualização para o MariaDB 10.6, considere ativar o [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) configuração. Por exemplo, `--query-cache-type=ON`.

Antes de atualizar o Adobe Commerce em projetos de infraestrutura em nuvem, também pode ser necessário atualizar o MariaDB ([consulte Práticas recomendadas de atualização do MariaDB](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Por exemplo:

* Adobe Commerce 2.4.6 com MariaDB versão 10.5.1 ou superior
* Adobe Commerce 2.3.5 com MariaDB versão 10.3 ou anterior

Além dessas recomendações, você deve consultar o administrador do banco de dados sobre a configuração dos seguintes parâmetros:

>[!NOTE]
>
>Essas configurações estão disponíveis somente para implantações locais. Os clientes do Adobe Commerce na infraestrutura em nuvem não têm acesso a essas configurações.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
