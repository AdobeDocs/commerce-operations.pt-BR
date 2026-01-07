---
title: Usar Redis para cache padrão
description: Saiba como configurar o Redis como cache padrão para o Adobe Commerce. Descubra técnicas de configuração, de configuração e de validação da linha de comando.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: ee4a873a73e8fd747e7d4c8e157327fab1074cc9
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# Usar Redis para cache padrão

O Commerce fornece opções de linha de comando para configurar a página Redis e o cache padrão. Embora você possa configurar o armazenamento em cache editando o arquivo `<Commerce-install-dir>app/etc/env.php`, o uso da linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação, garantindo que a configuração esteja sintaticamente correta.

Você deve [instalar o Redis](config-redis.md#install-redis) antes de continuar.

>[!NOTE]
>
>Para instâncias do Commerce hospedadas no EC2, você pode usar o AWS ElastiCache no lugar de uma instância local do Redis. Consulte [Configurar Elasticache para instâncias EC2](redis-elasticache-for-ec2.md).

## Configurar cache padrão do Redis

Execute o comando `setup:config:set` e especifique parâmetros específicos para o cache padrão Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--cache-backend=redis` habilita o cache padrão Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o cache padrão:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `cache-backend-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache padrão e de página inteira. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br><br>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `cache-backend-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração do Redis: `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | Ative ou desative o LUA. <br><br>**LUA**: Lua permite executar parte da lógica do aplicativo dentro do Redis, melhorando o desempenho e garantindo a consistência dos dados através de sua execução atômica. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Ative ou desative o LUA para a coleta de lixo. <br><br>**LUA**: Lua permite executar parte da lógica do aplicativo dentro do Redis, melhorando o desempenho e garantindo a consistência dos dados através de sua execução atômica. | `1` |

### Exemplo de comando

O exemplo a seguir habilita o cache padrão Redis, define o host como `127.0.0.1` e atribui o número do banco de dados como 0. Redis usa valores padrão para todos os outros parâmetros.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar cache de página Redis

Para configurar o cache da página Redis no Commerce, execute o comando `setup:config:set` com parâmetros adicionais.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--page-cache=redis` habilita o cache de página Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o armazenamento em cache da página:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `page-cache-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache de página padrão e completo. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br/>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `page-cache-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. Configure a senha no arquivo de configuração Redis: `/etc/redis/redis.conf` | |

### Exemplo de comando

O exemplo a seguir habilita o cache de página Redis, define o host como `127.0.0.1` e atribui o número do banco de dados como 1. Todos os outros parâmetros são definidos com o valor padrão.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Revisar a configuração do ambiente do Commerce

Executando os comandos para configurar o cache Redis, atualiza a configuração do ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

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

## Configurar opções adicionais de cache

Esta seção descreve como ativar as definições de configuração opcionais que são desativadas por padrão.

### Recurso de pré-carregamento Redis

Como o Commerce armazena dados de configuração no cache Redis, podemos pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise os dados transferidos de Redis para Commerce. Sugerimos pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

O Redis usa o `pipeline` para compor solicitações de carga. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento será semelhante a: `061_SYSTEM_DEFAULT`

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

Caso esteja usando o recurso de pré-carregamento com o cache L2, não se esqueça de adicionar o sufixo `:hash` às chaves, já que o cache L2 transfere apenas o hash dos dados, não os dados em si:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Geração paralela

Elimine a espera por bloqueios habilitando a opção `allow_parallel_generation`.

Essa opção está desativada por padrão e a Adobe recomenda desativá-la até que você tenha um grande número de configurações ou blocos.

**Para habilitar a geração paralela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Como essa opção é um sinalizador, não é possível desabilitá-lo com um comando. Você deve definir manualmente o valor de configuração como `false`:

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

Para verificar se o Redis e o Commerce estão trabalhando juntos, faça login no servidor executando o Redis, abra um terminal e use o comando Redis monitor ou o comando ping.

### Comando do monitor Redis

```bash
redis-cli monitor
```

Exemplo de saída de cache de página:

```
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

### comando Redis ping

```bash
redis-cli ping
```

A resposta esperada é: `PONG`

Se ambos os comandos forem bem-sucedidos, o Redis será configurado corretamente.

### Inspeção de dados compactados

Para inspecionar os dados de Sessão compactados e o Cache de Página, o [RESP.app](https://flathub.org/apps/details/app.resp.RESP) oferece suporte à descompactação automática do cache de Sessão e Página do Commerce 2 e exibe os dados de sessão do PHP de forma legível.
