---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# Definições de configuração do MariaDB

A reindexação no MariaDB 10.4 e 10.6 leva mais tempo em comparação com as versões anteriores do MariaDB ou MySQL. Para acelerar a reindexação, recomendamos definir esses parâmetros de configuração do MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Se ocorrer degradação de desempenho não relacionada à indexação após a atualização para o MariaDB 10.6, considere ativar o [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) configuração. Por exemplo, `--query-cache-type=ON`.

Além dessas recomendações, você deve consultar o administrador do banco de dados sobre a configuração dos seguintes parâmetros:

>[!NOTE]
>
>Essas configurações estão disponíveis somente para implantações locais. Os clientes do Adobe Commerce na infraestrutura em nuvem não têm acesso a essas configurações.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
