---
title: Usar Valkey para cache padrão
description: Saiba como configurar o Valkey como cache padrão para o Adobe Commerce. Descubra técnicas de configuração, de configuração e de validação da linha de comando.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: e9f1bef9f97a0e1d738f1221758f1b9a0a238da1
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# Usar Valkey para cache padrão

O Commerce fornece opções de linha de comando para configurar a página Valkey e o cache padrão. Embora você possa configurar o armazenamento em cache editando o arquivo `<Commerce-install-dir>app/etc/env.php`, o uso da linha de comando é o método recomendado, especialmente para configurações iniciais. A linha de comando fornece validação, garantindo que a configuração esteja sintaticamente correta.

Você deve [instalar a Valkey](config-redis.md#install-redis) antes de continuar.

## Configurar o armazenamento em cache padrão do Valkey

Execute o comando `setup:config:set` e especifique parâmetros para o cache padrão Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` habilita o cache padrão valkey. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--cache-backend-valkey-<parameter>=<value>` é uma lista de pares de valores chave que configuram o cache padrão:

>[!NOTE]
>
>A partir do **Adobe Commerce 2.4.9-alpha2**, o **Valkey** substituiu oficialmente o Redis em ferramentas CLI devido a alterações no licenciamento. Valkey é uma bifurcação de Redis e mantém funcionalidade quase idêntica. Para **versões 2.4.8 e anteriores**, os comandos da CLI usados para configurar o Valkey permanecem os mesmos do Redis, garantindo compatibilidade com versões anteriores e simplificando a migração ou o suporte a ambientes duplos. O exemplo a seguir mostra o comando Valkey-specific.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de `127.0.0.1` indica que o Valkey está instalado no servidor do Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | porta | Porta de escuta do servidor Valkey | `6379` |
| `cache-backend-valkey-db` | banco de dados | Obrigatório se você usar Valkey para o cache padrão e de página inteira. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa `0` por padrão.<br><br>**Importante**: se você usar Valkey para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. A Adobe recomenda que você atribua o número de banco de dados de cache padrão a `0`, o número de banco de dados de cache de página a `1` e o número de banco de dados de armazenamento de sessão a `2`. | `0` |
| `cache-backend-valkey-password` | senha | A configuração de uma senha Valkey habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. A senha é configurada diretamente no arquivo de configuração &#39;Valkey&#39;: `/etc/valkey/valkey.conf` | |

### Exemplo de comando

O exemplo a seguir habilita o cache padrão Valkey, define o host como `127.0.0.1` e atribui o número do banco de dados como `0`. Valkey usa valores padrão para todos os outros parâmetros.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>A partir do **Adobe Commerce 2.4.9-alpha2**, o **Valkey** substituiu oficialmente o Redis em ferramentas CLI devido a alterações no licenciamento. Valkey é uma bifurcação de Redis e mantém funcionalidade quase idêntica. Para **versões 2.4.8 e anteriores**, os comandos da CLI usados para configurar o Valkey permanecem os mesmos do Redis, garantindo compatibilidade com versões anteriores e simplificando a migração ou o suporte a ambientes duplos. O exemplo a seguir mostra o comando Valkey-specific.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar armazenamento em cache da página

Para configurar o cache da página Valkey no Commerce, execute o comando `setup:config:set` com parâmetros adicionais.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Com os seguintes parâmetros:

- `--page-cache=valkey` habilita o cache de página do Valkey. Se esse recurso já tiver sido ativado, omita esse parâmetro.

- `--page-cache-valkey-<parameter>=<value>` é uma lista de pares de chave-e-valor que configuram o armazenamento em cache da página:

>[!NOTE]
>
>A partir do **Adobe Commerce 2.4.9-alpha2**, o **Valkey** substituiu oficialmente o Redis em ferramentas CLI devido a alterações no licenciamento. Valkey é uma bifurcação de Redis e mantém funcionalidade quase idêntica. Para **versões 2.4.8 e anteriores**, os comandos da CLI usados para configurar o Valkey permanecem os mesmos do Redis, garantindo compatibilidade com versões anteriores e simplificando a migração ou o suporte a ambientes duplos. O exemplo a seguir mostra o comando Valkey-specific.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| Parâmetro de linha de comando | Valor | Significado | Valor padrão |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nome de host totalmente qualificado, endereço IP ou um caminho absoluto para um soquete UNIX. O valor padrão de `127.0.0.1` indica que o Valkey está instalado no servidor do Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | porta | Porta de escuta do servidor Valkey. | `6379` |
| `page-cache-valkey-db` | banco de dados | Obrigatório se você usar Valkey para o cache padrão e de página inteira. Você deve especificar o número do banco de dados de um dos caches; o outro cache usa `0` por padrão.<br/>**Importante**: se você usar Valkey para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de cache a `0`, o número do banco de dados de cache da página a `1` e o número do banco de dados de armazenamento da sessão a `2`. | `0` |
| `page-cache-valkey-password` | senha | A configuração de uma senha Valkey habilita um de seus recursos de segurança internos: o comando `auth`, que requer que os clientes se autentiquem para acessar o banco de dados. Configure a senha no arquivo de configuração Valkey: `/etc/valkey/valkey.conf` | |

### Exemplo de comando

O exemplo a seguir habilita o cache da página Valkey, define o host como `127.0.0.1` e atribui o número do banco de dados como `1`. Todos os outros parâmetros são definidos com o valor padrão.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>A partir do **Adobe Commerce 2.4.9-alpha2**, o **Valkey** substituiu oficialmente o Redis em ferramentas CLI devido a alterações no licenciamento. Valkey é uma bifurcação de Redis e mantém funcionalidade quase idêntica. Para **versões 2.4.8 e anteriores**, os comandos da CLI usados para configurar o Valkey permanecem os mesmos do Redis, garantindo compatibilidade com versões anteriores e simplificando a migração ou o suporte a ambientes duplos. O exemplo a seguir mostra o comando Valkey-specific.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## Resultados

Como resultado dos dois comandos de exemplo, o Commerce adiciona linhas semelhantes ao seguinte a `<Commerce-install-dir>app/etc/env.php`:

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

## Nova implementação do cache Valkey

[!BADGE 2.4.9-alpha]{type=Negative tooltip="Disponível somente na versão 2.4.9-alpha."}

A partir do Adobe Commerce 2.4.9, a Adobe recomenda usar a implementação do cache Valkey: `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Recurso de pré-carregamento do Valkey

Como o Commerce armazena dados de configuração no cache Valkey, você pode pré-carregar dados que são reutilizados entre páginas. Para encontrar chaves que devem ser pré-carregadas, analise os dados transferidos do Valkey para o Commerce. A Adobe sugere pré-carregar dados que são carregados em todas as páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

Valkey usa `pipeline` para solicitações de carregamento compostas. As chaves devem incluir o prefixo do banco de dados; por exemplo, se o prefixo do banco de dados for `061_`, a chave de pré-carregamento será semelhante a: `061_SYSTEM_DEFAULT`

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

Ao usar o recurso de pré-carregamento com um cache L2, você deve adicionar o sufixo `:hash` às chaves. O cache L2 transfere apenas o hash dos dados, não os dados reais.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Geração paralela

A partir da versão 2.4.0 do Commerce, a Adobe apresentou a opção `allow_parallel_generation` para usuários que desejam eliminar a espera por bloqueios.
Ela está desativada por padrão e a Adobe recomenda desativá-la até que você tenha configurações e/ou blocos em excesso.

**Para habilitar a geração paralela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Como é um sinalizador, não é possível desabilitá-lo com um comando. Você deve definir manualmente o valor de configuração como `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Verificar conexão Valkey

Para verificar se Valkey e Commerce estão trabalhando juntos corretamente, faça logon no servidor que executa Valkey, abra um terminal e use o comando `valkey-cli monitor` ou o comando `redis-cli ping`.

### Comando do monitor Valkey

```bash
valkey-cli monitor
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

### comando Valkey ping

```bash
valkey-cli ping
```

A resposta esperada é: `PONG`

Se ambos os comandos forem bem-sucedidos, Valkey será configurado corretamente.

### Inspeção de dados compactados

Para inspecionar os dados da sessão compactada e o cache de página, o [RESP.app](https://flathub.org/apps/app.resp.RESP) oferece suporte à descompactação automática da sessão do Commerce 2 e do cache de página e exibe os dados da sessão PHP em um formato legível.
