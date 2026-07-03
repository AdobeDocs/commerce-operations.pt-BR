---
title: Configurar Redis para Cache Padrão e de Página
description: Saiba como configurar o Redis como padrão e o back-end do cache de página para o Adobe Commerce. Descubra os comandos da ILC, as configurações do env.php e a verificação da conexão.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 1261
ht-degree: 0%

---

# Configurar Redis para cache padrão e de páginas

{{cloud-cache-config}}

O Commerce fornece opções de linha de comando para configurar a página Redis e o cache padrão. Embora você possa configurar o armazenamento em cache editando o arquivo `<Commerce-install-dir>app/etc/env.php`, o uso da linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação, garantindo que a configuração esteja sintaticamente correta.

**Pré-requisito:**

[Instale o Redis](config-redis.md#install-redis) antes de continuar.

>[!NOTE]
>
>Para instâncias do Commerce hospedadas no EC2, você pode usar o AWS ElastiCache no lugar de uma instância local do Redis. Consulte [Configurar Elasticache para instâncias EC2](redis-elasticache-for-ec2.md).

## Implementações do cache Redis

A Adobe Commerce usou estas implementações de back-end do cache Redis:

- **Infraestrutura Redis herdada** (`Cm_Cache_Backend_Redis`) - Implementação obsoleta usada em configurações Redis mais antigas.
- **Infraestrutura Redis** (`Magento\Framework\Cache\Backend\Redis`) - Infraestrutura usada pela configuração de linha de comando neste tópico para cache padrão e de página.
- **Back-end do cache L2** (`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`) - Implementação de cache de dois níveis que usa Redis como back-end remoto e armazenamento de cache de arquivo local para sincronizar dados de cache entre nós. Consulte [Configuração de cache de dois níveis](level-two-cache.md).

## Configurar cache padrão do Redis

Execute o comando `setup:config:set` e especifique parâmetros específicos para o cache padrão Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Parâmetros comuns incluem:

- `--cache-backend=redis` habilita o cache padrão Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o cache padrão:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `cache-backend-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache padrão e de página inteira. Especifique o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br><br>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `cache-backend-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração do Redis: `/etc/redis/redis.conf` | |
| `cache-backend-redis-compress-data` | compress_data | Defina como `0` para desabilitar a compactação. | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | Biblioteca de compactação a ser usada. Os valores suportados incluem `snappy`, `lzf`, `l4z`, `zstd` e `gzip`. Deixe em branco para determinar automaticamente. | |
| `cache-backend-redis-use-lua` | use_lua | Ative ou desative scripts Lua para todas as operações Redis. <br><br>**Padrão: manter em `0`.** O modo Lua é desativado por padrão para evitar regressões de desempenho conhecidas e problemas de perda de cache do GraphQL introduzidos pela biblioteca Redis agrupada (1.17.x) quando Lua foi ativada. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Habilite ou desabilite scripts Lua para a coleta de lixo (o trabalho cron `backend_clean_cache`). <br><br>**Padrão: manter em `1`.** Ativado intencionalmente para garantir a limpeza atômica do conjunto de tags durante o GC. Sem ela, uma condição de corrida pode ocorrer quando o cron `backend_clean_cache` é executado ao mesmo tempo que uma operação de salvamento de cache, deixando entradas de cache sem um registro correspondente no índice de tag de cache. Isso faz com que a invalidação baseada em tags falhe silenciosamente — por exemplo, atualizar um preço de produto pode não invalidar o cache do produto, exigindo uma liberação de cache completa. | `1` |

### Modo Lua

Quando habilitado, o modo Lua agrupa várias operações Redis (gravações em cache, atualizações de tags, coleta de lixo) em um único script atômico executado no lado do servidor via `EVALSHA`. Isso impede a intercalação de solicitações simultâneas, por exemplo, garantir que uma entrada de cache e sua associação de tag sejam gravadas juntas.

>[!WARNING]
>
>Não altere os valores padrão de `use_lua` e `use_lua_on_gc` sem entender as implicações para sua versão do Adobe Commerce:
>
>- **`use_lua`**: habilitar isso no Adobe Commerce 2.4.7 ou 2.4.8 (biblioteca `colinmollenhour/cache-backend-redis` 1.17.1) pode causar corrupção de cache e problemas de perda de cache do GraphQL.
>- **`use_lua_on_gc`**: desabilitar isso no Adobe Commerce 2.4.8 remove a proteção atômica durante a coleta de lixo e pode fazer com que a invalidação do cache com base em marcas falhe silenciosamente, exigindo uma limpeza completa do cache para se recuperar.

## Exemplo de comando (cache padrão)

O exemplo a seguir habilita o cache padrão Redis, define o host como `127.0.0.1` e atribui o número do banco de dados como 0. Redis usa valores padrão para todos os outros parâmetros.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar cache de página Redis

Para configurar o cache da página Redis no Commerce, execute o comando `setup:config:set` com parâmetros adicionais.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Parâmetros comuns incluem:

- `--page-cache=redis` habilita o cache de página Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o armazenamento em cache da página:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| --- | --- | --- | --- |
| `page-cache-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `page-cache-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache de página padrão e completo. Especifique o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br/>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `page-cache-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. Configure a senha no arquivo de configuração Redis: `/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | Defina como `1` para compactar o cache de página inteira. Use `0` para desabilitar a compactação. | `0` |
| `page-cache-redis-compression-lib` | compression_lib | Biblioteca de compactação a ser usada. Os valores suportados incluem `snappy`, `lzf`, `l4z`, `zstd` e `gzip`. Deixe em branco para determinar automaticamente. | |

O exemplo a seguir habilita o cache de página Redis, define o host como `127.0.0.1` e atribui o número do banco de dados como `1`. Todos os outros parâmetros são definidos com o valor padrão.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Revisar a configuração do ambiente do Commerce

A execução dos comandos para configurar o cache Redis atualiza a configuração do ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

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

### Recurso de pré-carregamento Redis

Como o Commerce armazena dados de configuração no cache Redis, você pode pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise os dados transferidos de Redis para Commerce. A Adobe sugere pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

O Redis usa `pipeline` para solicitações de carga compostas. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento será semelhante a: `061_SYSTEM_DEFAULT`

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

Ao usar o recurso de pré-carregamento com um cache L2, você deve adicionar o sufixo `:hash` às chaves. O cache L2 transfere apenas o hash dos dados, não os dados reais.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Geração paralela

A partir da versão 2.4.0 do Commerce, a Adobe apresentou a opção `allow_parallel_generation` para usuários que desejam eliminar a espera por bloqueios. Ela está desativada por padrão e a Adobe recomenda desativá-la até que você tenha configurações e/ou blocos em excesso.

**Para habilitar a geração paralela**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Como é um sinalizador, não é possível desabilitá-lo com um comando. Defina manualmente o valor de configuração como `false`:

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

### Extensão PHP Redis

Use a extensão nativa do PHP Redis (`phpredis`) quando seu ambiente permitir:

#### Usar apt

Para Debian ou Ubuntu, use `apt`:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### Usar pecl

Como alternativa, use `pecl`:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

## Verifique a conexão Redis

Para verificar se o Redis e o Commerce estão funcionando corretamente:

1. Faça logon no servidor que executa o Redis e o Commerce.
1. Abra um terminal.
1. Verifique a conexão usando o comando `redis-cli monitor` ou `redis-cli ping`.

Se os comandos forem bem-sucedidos, o Redis estará em execução e poderá se comunicar com o aplicativo do Commerce. Se falharem, há um problema de conexão entre o Redis e o Commerce que você precisa resolver.

### Comando do monitor Redis

```shell
redis-cli monitor
```

Exemplo de saída de cache de página:

```text
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
...
```

Se ambos os comandos forem bem-sucedidos, o Redis será configurado corretamente.

### Inspecionar dados compactados

Para inspecionar dados de sessão compactados e cache de página, use a ferramenta [RESP.app](https://flathub.org/apps/details/app.resp.RESP). Ele suporta a descompressão automática de dados de sessão e cache de página do Commerce 2 e exibe os dados da sessão PHP em um formato legível.
