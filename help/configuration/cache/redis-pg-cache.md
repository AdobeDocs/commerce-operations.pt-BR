---
title: Usar Redis para cache padrão
description: Saiba como configurar o Redis como cache padrão para Adobe Commerce e Magento Open Source.
source-git-commit: 47d513e7ca51ad7dbc149d0f1e076f673452918c
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---


# Usar Redis para cache padrão

O Commerce fornece opções de linha de comando para configurar a página Redis e o cache padrão. Embora você possa configurar o armazenamento em cache editando o `<Commerce-install-dir>app/etc/env.php` , usar a linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação, garantindo que a configuração seja sintaticamente correta.

Você deve [instalar o Redis](config-redis.md#install-redis) antes de continuar.

## Configurar o cache padrão do Redis

Execute o `setup:config:set` e especifique parâmetros específicos para o cache padrão do Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--cache-backend=redis` ativa o cache padrão Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-redis-<parameter>=<value>` é uma lista de pares de chave e valor que configuram o cache padrão:

| Parâmetro da linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Nome do host, endereço IP ou um caminho absoluto totalmente qualificado para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `cache-backend-redis-db` | banco de dados | Obrigatório se você usar o Redis para o cache padrão e de página inteira. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br><br>**Importante**: Se você usar Redis para mais de um tipo de armazenamento em cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de armazenamento em cache a 0, o número do banco de dados de armazenamento em cache de página a 1 e o número do banco de dados de armazenamento de sessão a 2. | `0` |
| `cache-backend-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança incorporados: o `auth` , que requer que os clientes sejam autenticados para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração do Redis: `/etc/redis/redis.conf` |  |

### comando Exemplo

O exemplo a seguir ativa o armazenamento em cache padrão do Redis, e define o host como `127.0.0.1`e atribui o número do banco de dados a 0. Redis usa valores padrão para todos os outros parâmetros.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar o armazenamento em cache de páginas do Redis

Para configurar o armazenamento em cache da página do Redis no Commerce, execute o `setup:config:set` com parâmetros adicionais.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--page-cache=redis` habilita o armazenamento em cache de página do Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-redis-<parameter>=<value>` é uma lista de pares de chave e valor que configuram o armazenamento em cache de páginas:

| Parâmetro da linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Nome do host, endereço IP ou um caminho absoluto totalmente qualificado para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `page-cache-redis-db` | banco de dados | Obrigatório se você usar o Redis para o cache de página padrão e completo. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br/>**Importante**: Se você usar Redis para mais de um tipo de armazenamento em cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de armazenamento em cache a 0, o número do banco de dados de armazenamento em cache de página a 1 e o número do banco de dados de armazenamento de sessão a 2. | `0` |
| `page-cache-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança incorporados: o `auth` , que requer que os clientes sejam autenticados para acessar o banco de dados. Configure a senha no arquivo de configuração Redis: `/etc/redis/redis.conf` |  |

### comando Exemplo

O exemplo a seguir ativa o armazenamento em cache de página do Redis, e define o host como `127.0.0.1`e atribui o número do banco de dados a 1. Todos os outros parâmetros são definidos com o valor padrão.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Resultados

Como resultado dos dois comandos de exemplo, o Commerce adiciona linhas semelhantes às seguintes a `<Commerce-install-dir>app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Uso do AWS ElastiCache com sua instância do EC2

Desde o Commerce 2.4.3, as instâncias hospedadas no Amazon EC2 podem usar um AWS ElastiCache no lugar de uma instância de Redis local.

>[!WARNING]
>
>Esta seção só funciona para instâncias de Comércio executadas em VPCs Amazon EC2. Não funciona para instalações no local.

### Configurar um cluster Redis

Depois [configuração de um cluster Redis no AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configure a instância do EC2 para usar o ElastiCache.

1. [Criar um cluster ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) na mesma região e no VPC da instância do EC2.
1. Verifique a conexão.

   - Abra uma conexão SSH com sua instância do EC2
   - Na instância do EC2, instale o cliente Redis:

      ```bash
      sudo apt-get install redis
      ```

   - Adicione uma regra de entrada ao grupo de segurança EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Adicione uma regra de entrada ao grupo de segurança do Cluster ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conecte-se à CLI de Redis:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Configurar o Commerce para utilizar o cluster

O Commerce é compatível com vários tipos de configurações de armazenamento em cache. Geralmente, as configurações de armazenamento em cache são divididas entre front-end e backend. O armazenamento em cache de fronteira é classificado como `default`, usado para qualquer tipo de cache. Você pode personalizar ou dividir em caches de nível inferior para obter melhor desempenho. Uma configuração comum do Redis está separando o cache padrão e o cache de página em seu próprio RDB (Redis Database).

Executar `setup` comandos para especificar os endpoints do Redis.

Para configurar o Commerce for Redis como cache padrão:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Para configurar o armazenamento em cache de página do Commerce for Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Para configurar o Commerce para usar o Redis para armazenamento de sessão:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verificar conectividade

**Para verificar se o Commerce está conversando com o ElastiCache**:

1. Abra uma conexão SSH para a instância do Commerce EC2.
1. Inicie o monitor Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Abra uma página na interface do usuário do Commerce.
1. Verifique o [saída do cache](#verify-redis-connection) no terminal.

## Nova implementação de cache de Redis

A partir do Commerce 2.3.5, é recomendável usar a implementação estendida do cache do Redis: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Recurso de pré-carregamento Redis

Como o Commerce armazena dados de configuração no cache de Redis, podemos pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise dados transferidos de Redis para Commerce. Sugerimos pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis usa o `pipeline` para compor solicitações de carregamento. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento tem a seguinte aparência: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Caso esteja usando o recurso de pré-carregamento com o cache L2, não se esqueça de adicionar a variável `:hash` sufixo em suas chaves, já que o cache L2 transfere apenas o hash dos dados, não os dados em si:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Geração paralela

A partir da versão 2.4.0, introduzimos o `allow_parallel_generation` para os usuários que desejam eliminar a espera por bloqueios.
Está desativado por padrão e recomendamos desativá-lo até que você tenha configurações e/ou blocos excessivos.

**Para permitir a geração paralela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Como é um sinalizador, não é possível desativá-lo com um comando. Você deve definir manualmente o valor de configuração como `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Verifique a conexão Redis

Para verificar se o Redis e o Commerce estão funcionando juntos, faça logon no servidor que executa o Redis, abra um terminal e use o comando Redis monitor ou o comando ping.

### comando Redis monitor

```bash
redis-cli monitor
```

Exemplo de saída de armazenamento em cache de página:

```terminal
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### comando ping Redis

```bash
redis-cli ping
```

A resposta esperada é: `PONG`

Se ambos os comandos tiverem êxito, o Redis será configurado corretamente.

### Como inspecionar dados compactados

Para inspecionar os dados compactados da Sessão e o Cache da Página, a variável [RESP.app](https://flathub.org/apps/details/app.resp.RESP) O suporta a descompactação automática do Cache de Sessão e Página do Commerce 2 e exibe os dados de sessão PHP em um formulário legível.
