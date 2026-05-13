---
title: Configurar Redis para Cache Padrão e de Página
description: Saiba como configurar o Redis como padrão e o back-end do cache de página para o Adobe Commerce. Descubra os comandos da ILC, as configurações do env.php e a verificação da conexão.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---

# Configurar Redis para cache padrão e de páginas

O Commerce fornece opções de linha de comando para configurar a página Redis e o cache padrão. Embora você possa configurar o armazenamento em cache editando o arquivo `<Commerce-install-dir>app/etc/env.php`, a linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação para garantir que a configuração esteja sintaticamente correta.

**Pré-requisito:**

[Instale o Redis](config-redis.md#install-redis) antes de continuar.

>[!NOTE]
>
>Para instâncias do Commerce hospedadas no EC2, você pode usar o AWS ElastiCache no lugar de uma instância local do Redis. Consulte [Configurar Elasticache para instâncias EC2](redis-elasticache-for-ec2.md).

## Estruturas compatíveis

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 e anterior)]

- **Zend Cache (2.4.8 e anterior)** — Back-end Redis herdado para Commerce 2.4.8 e anterior:
   - **Infraestrutura Redis herdada** — Usa o caminho de classe completo (`Magento\Framework\Cache\Backend\Redis`)
   - **Chaves de pré-carregamento** — Suporta o pré-carregamento de chaves de cache usadas com frequência
   - **Scripts Lua** — Lua para coleta de lixo
   - **Compactação** — Suporta compactação de dados

>[!TAB Cache do Symfony (2.4.9+)]

- **Symfony Cache (2.4.9+)** — a partir do Commerce 2.4.9, o Symfony Cache fornece uma implementação de cache moderna e compatível com PSR-6 para Redis, com melhorias significativas no desempenho:
   - **Pipeline Redis Automático** — Agrupa várias operações em solicitações únicas, reduzindo a latência
   - **PSR-6 TagAwareAdapter** — Invalidação eficiente de cache com base em marcas com operações atômicas
   - **Serialização binária** — a serialização binária reduz o tamanho da entrada de cache em 45% e melhora a velocidade em 5-10%
   - **Conexões persistentes aprimoradas** — Pool de conexões mais estável com melhor tratamento de processos bifurcados
   - **Scripts Lua otimizados** — Execução no lado do servidor combinada com pipeline para eficiência máxima

>[!ENDTABS]


## Configurar cache padrão do Redis

Execute o comando `setup:config:set` e especifique parâmetros específicos para o cache padrão Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--cache-backend=redis` habilita o cache padrão Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o cache padrão:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `cache-backend-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache padrão e de página inteira. Especifique o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br><br>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `cache-backend-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração do Redis: `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | Ative ou desative Lua. <br><br>**Lua**: Lua permite executar parte da lógica do aplicativo dentro de Redis, melhorando o desempenho e garantindo a consistência dos dados através da execução atômica. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Ative ou desative Lua para a coleta de lixo. <br><br>**Lua**: Lua permite executar parte da lógica do aplicativo dentro de Redis, melhorando o desempenho e garantindo a consistência dos dados através da execução atômica. | `1` |

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

Com os seguintes parâmetros:

- `--page-cache=redis` habilita o cache de página Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-redis-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o armazenamento em cache da página:

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de 127.0.0.1 indica que o Redis está instalado no servidor do Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta de escuta do servidor Redis | `6379` |
| `page-cache-redis-db` | banco de dados | Obrigatório se você usar Redis para o cache de página padrão e completo. Especifique o número do banco de dados de um dos caches; o outro cache usa 0 por padrão.<br/>**Importante**: se você usar Redis para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número do banco de dados de cache padrão a 0, o número do banco de dados de cache da página a 1 e o número do banco de dados de armazenamento da sessão a 2. | `0` |
| `page-cache-redis-password` | senha | A configuração de uma senha Redis habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. Configure a senha no arquivo de configuração Redis: `/etc/redis/redis.conf` | |

O exemplo a seguir habilita o cache de página Redis, define o host como `127.0.0.1` e atribui o número do banco de dados como `1`. Todos os outros parâmetros são definidos com o valor padrão.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Revisar a configuração do ambiente do Commerce

A execução dos comandos para configurar o cache Redis atualiza a configuração do ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 e anterior)]

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

>[!TAB Cache do Symfony (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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
>A partir do Commerce 2.4.9, use o tipo de back-end simplificado `'backend' => 'redis'` em vez do caminho de classe completo. O Symfony Cache é usado automaticamente quando o nome simplificado é especificado.

>[!ENDTABS]

## Configurar opções adicionais de cache

### Recurso de pré-carregamento Redis

Como o Commerce armazena dados de configuração no cache Redis, você pode pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise os dados transferidos de Redis para Commerce. A Adobe sugere pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

O Redis usa `pipeline` para solicitações de carga compostas. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento será semelhante a: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Cache Zend]

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

>[!TAB Cache do Symfony]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'redis',
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

>[!TAB Cache do Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
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
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
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

As conexões persistentes reutilizam as conexões Redis existentes em todas as solicitações, fornecendo operações de cache de 5 a 15% mais rápidas. Configurar em `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
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
                'server' => 'redis',
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

Esta é uma configuração Symfony pronta para produção combinando todas as otimizações de desempenho:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
