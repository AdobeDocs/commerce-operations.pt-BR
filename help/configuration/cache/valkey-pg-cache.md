---
title: Configurar Valkey para Padrão e Cache de Página
description: Saiba como configurar o Valkey como o padrão e o back-end do cache de página do Adobe Commerce. Descubra os comandos da ILC, as configurações do env.php e a verificação da conexão.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---


# Configurar Valkey para cache padrão e de página

O Commerce fornece opções de linha de comando para configurar o padrão Valkey e o cache de página. Embora você possa configurar o armazenamento em cache editando o arquivo `<Commerce-install-dir>app/etc/env.php`, o uso da linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação, garantindo que a configuração esteja sintaticamente correta.

**Pré-requisito:**

[Instale Valkey](config-valkey.md#install-valkey) antes de continuar.

## Estruturas compatíveis


>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 e anterior)]

- **Zend Cache (2.4.8 e anterior)** — Back-end Valkey herdado para Commerce 2.4.8 e anterior:
   - **Infraestrutura Valkey herdada** — Usa o caminho de classe completo (`Magento\Framework\Cache\Backend\Valkey`)
   - **Chaves de pré-carregamento** — Suporta o pré-carregamento de chaves de cache usadas com frequência
   - **Scripts Lua** — Lua para coleta de lixo
   - **Compactação** — Suporta compactação de dados

>[!TAB Cache do Symfony (2.4.9+)]

- **Symfony Cache (2.4.9+)** — A partir do Commerce 2.4.9, o Symfony Cache fornece uma implementação de cache moderna e compatível com PSR-6 para Valkey, com melhorias significativas de desempenho:
   - **Pipeline automático do Valkey** — agrupa várias operações em solicitações únicas, reduzindo a latência
   - **PSR-6 TagAwareAdapter** — Invalidação eficiente de cache com base em marcas com operações atômicas
   - **Serialização binária** — a serialização binária reduz o tamanho da entrada de cache em 45% e melhora a velocidade em 5-10%
   - **Conexões persistentes aprimoradas** — Pool de conexões mais estável com melhor tratamento de processos bifurcados
   - **Scripts Lua otimizados** — Execução no lado do servidor combinada com pipeline para eficiência máxima

>[!ENDTABS]

## Configurar o armazenamento em cache padrão do Valkey

Execute o comando `setup:config:set` e especifique parâmetros para o cache padrão Valkey.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` habilita o cache padrão Valkey. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-valkey-<parameter>=<value>` é uma lista de pares de valores chave que configuram o cache padrão:

{{valkey-redis-cli-note}}

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de `127.0.0.1` indica que o Valkey está instalado no servidor do Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | porta | Porta de escuta do servidor Valkey | `6379` |
| `cache-backend-valkey-db` | banco de dados | Obrigatório se você usar Valkey para o cache padrão e de página inteira. Especifique o número do banco de dados de um dos caches; o outro cache usa `0` por padrão.<br><br>**Importante**: se você usar Valkey para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. A Adobe recomenda que você atribua o número de banco de dados de cache padrão a `0`, o número de banco de dados de cache de página a `1` e o número de banco de dados de armazenamento de sessão a `2`. | `0` |
| `cache-backend-valkey-password` | senha | A configuração de uma senha Valkey habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração do Valkey: `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | Ative ou desative o LUA. <br><br>**LUA**: Lua permite executar parte da lógica do aplicativo dentro do Valkey, melhorando o desempenho e garantindo a consistência dos dados através de sua execução atômica. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Ative ou desative o LUA para a coleta de lixo. <br><br>**LUA**: Lua permite executar parte da lógica do aplicativo dentro do Valkey, melhorando o desempenho e garantindo a consistência dos dados através de sua execução atômica. | `1` |

## Exemplo de comando (cache padrão)

O exemplo a seguir habilita o cache padrão Valkey, define o host como `127.0.0.1` e atribui o número do banco de dados como `0`. Valkey usa valores padrão para todos os outros parâmetros.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Configurar o armazenamento em cache da página do Valkey

Para configurar o cache da página Valkey no Commerce, execute o comando `setup:config:set` com parâmetros adicionais.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--page-cache=valkey` habilita o cache de página do Valkey. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-valkey-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o armazenamento em cache da página:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de `127.0.0.1` indica que o Valkey está instalado no servidor do Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | porta | Porta de escuta do servidor Valkey. | `6379` |
| `page-cache-valkey-db` | banco de dados | Obrigatório se você usar Valkey para o cache padrão e de página inteira. Especifique o número do banco de dados de um dos caches; o outro cache usa `0` por padrão.<br/>**Importante**: se você usar Valkey para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de cache a `0`, o número do banco de dados de cache da página a `1` e o número do banco de dados de armazenamento da sessão a `2`. | `0` |
| `page-cache-valkey-password` | senha | A configuração de uma senha Valkey habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. Configure a senha no arquivo de configuração Valkey: `/etc/valkey/valkey.conf` | |

### Exemplo de comando (cache de página)

O exemplo a seguir habilita o cache da página Valkey, define o host como `127.0.0.1` e atribui o número do banco de dados como `1`. Todos os outros parâmetros são definidos com o valor padrão.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Revisar a configuração do ambiente do Commerce

A execução dos comandos para configurar o armazenamento em cache do Valkey atualiza a configuração do ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 e anterior)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

>[!TAB Cache do Symfony (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>A partir do Commerce 2.4.9, use o tipo de back-end simplificado `'backend' => 'valkey'` em vez do caminho de classe completo. O Symfony Cache é usado automaticamente quando o nome simplificado é especificado.

>[!ENDTABS]

## Configurar opções adicionais de cache

### Recurso de pré-carregamento do Valkey

Como o Commerce armazena dados de configuração no cache Valkey, você pode pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise os dados transferidos do Valkey para o Commerce. A Adobe sugere pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

Valkey usa `pipeline` para solicitações de carregamento compostas. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento será semelhante a: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Cache Zend]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!TAB Cache do Symfony]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!ENDTABS]

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

>[!BEGINTABS]

>[!TAB Cache Zend]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Cache do Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Otimização do desempenho do Symfony Cache

Se você estiver usando o Symfony Cache, poderá otimizar ainda mais o desempenho configurando o serializador Igbinary, instalando a extensão igbinary PHP e a extensão phpredis e ativando conexões persistentes.

### Serializador igbinary

O serializador Igbinary fornece melhorias significativas de desempenho sobre a serialização padrão do PHP. Deve ser configurado manualmente em `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Instalar a extensão Igbinary do PHP

Para usar a serialização igbinary, você deve instalar a extensão Igbinary do PHP.

**Usando apt (recomendado para Debian/Ubuntu)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Usando pecl (método alternativo)**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### Extensões do PHP Redis: phpredis vs Predis

O Commerce 2.4.9+ inclui fallback automático entre phpredis (extensão nativa C) e Predis (biblioteca PHP pura). Para obter o desempenho ideal, instale o phpredis:

**Usando apt (recomendado para Debian/Ubuntu)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Usando pecl (método alternativo)**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Comparação de desempenho**:

| Operação | Predis | phpredis | Melhoria |
|-----------|--------|----------|-------------|
| GET de cache | 1 a 5 ms | 0,5 a 2 ms | De 2 a 3 vezes mais rápido |
| CONJUNTO DE cache | 2 a 6 ms | 0,8 a 2,5 ms | De 2 a 3 vezes mais rápido |
| Marcar operações | 10-30 ms | 3 a 10 ms | De 3 a 4 vezes mais rápido |

### Conexões persistentes

Conexões persistentes reutilizam conexões Valkey existentes em solicitações, fornecendo operações de cache de 5 a 15% mais rápidas. Configurar em `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Use um `persistent_id` exclusivo para cada tipo de cache para evitar conflitos de conexão.

### Concluir a configuração otimizada

Esta é uma configuração pronta para produção combinando todas as otimizações de desempenho:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Verificar conexão Valkey

Para verificar se Valkey e Commerce estão trabalhando juntos corretamente:

1. Faça logon no servidor que executa o Valkey e o Commerce.
1. Abra um terminal.
1. Verifique a conexão usando o comando `valkey-cli monitor` ou `valkey-cli ping`.

Se os comandos forem bem-sucedidos, o Valkey estará em execução e poderá se comunicar com o aplicativo do Commerce. Se falharem, há um problema de conexão entre o Valkey e o Commerce que você precisa resolver.

### Comando do monitor Valkey

```shell
valkey-cli monitor
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### comando Valkey ping

```shell
valkey-cli ping
```

A resposta esperada é: `PONG`

Se ambos os comandos forem bem-sucedidos, Valkey será configurado corretamente.

### Inspecionar dados compactados

Para inspecionar dados de sessão compactados e cache de página, use a ferramenta [RESP.app](https://flathub.org/apps/app.resp.RESP). Ele suporta a descompactação automática de dados de sessão e cache de página do Commerce 2 e exibe os dados da sessão PHP em um formato legível.

