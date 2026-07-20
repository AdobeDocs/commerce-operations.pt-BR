---
title: Configuração de cache L2 para otimização de desempenho
description: Saiba como configurar o cache L2 no Adobe Commerce para reduzir o tráfego de rede e melhorar o desempenho. Conheça as opções de implementação herdadas e do Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce no local."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 5f20ef1b6e40728e38d06f5c9f90f72ba1eb43e0
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 0%

---

# Configuração do cache L2 para otimização do desempenho

O cache L2 (de dois níveis) reduz o tráfego de rede entre o armazenamento remoto em cache (Redis ou Valkey) e o aplicativo Commerce, adicionando uma camada de cache local em cada nó da Web. Uma instância padrão do Commerce transfere cerca de 300 KB por solicitação, e o tráfego pode aumentar rapidamente para mais de 1000 solicitações em algumas situações.

Com o cache L2, cada nó da Web armazena os dados acessados com frequência localmente e usa o cache remoto para duas finalidades:

- Verificando a versão dos dados do cache para garantir que o cache mais recente seja armazenado localmente
- Transferindo dados atualizados do cache do armazenamento remoto para o computador local

O Commerce armazena a versão de dados com hash no cache remoto, com o sufixo `:hash` anexado à chave regular. Quando o cache local está desatualizado, os dados são obtidos da máquina remota por meio de um adaptador de cache.

Há duas implementações de cache L2 disponíveis:

| Implementação | Versão | Descrição |
| -------------- | ------- | ----------- |
| [Herdados (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2.4.x | Cache de dois níveis baseado em Zend com `Cm_Cache_Backend_File` para armazenamento local |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 baseado em cache Symfony com conformidade PSR-6 e desempenho aprimorado |

>[!NOTE]
>
>Para o Adobe Commerce na Nuvem, configure o cache L2 definindo a variável de implantação [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=pt-BR#redis_backend) ou [`VALKEY_BACKEND`](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) em `.magento.env.yaml`. Consulte [Configurar cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache) para obter exemplos de configuração.

## Configuração herdada do cache L2 (RemoteSynchronizedCache)

Use o exemplo a seguir para modificar ou substituir a seção de cache existente no arquivo `app/etc/env.php`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Onde:

- `backend` é a implementação do cache L2.
- `backend_options` é a configuração de cache L2.
  - `remote_backend` é a implementação de cache remoto: Redis ou MySQL.
  - `remote_backend_options` é a configuração de cache remoto.
  - `local_backend` é a implementação de cache local: `Cm_Cache_Backend_File`
  - `local_backend_options` é a configuração de cache local.
  - `cache_dir` é uma opção específica de cache de arquivo para o diretório onde o cache local está armazenado.

A Adobe recomenda usar Redis para cache remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` para o cache local de dados na memória compartilhada, usando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

A Adobe recomenda o uso do recurso [`cache preload`](redis-pg-cache.md#redis-preload-feature), pois ele diminui drasticamente a pressão sobre o Redis. Não se esqueça de adicionar o sufixo &#39;:hash&#39; para chaves de pré-carregamento.

## Opções de cache obsoletas

A partir do Commerce 2.4, a opção `use_stale_cache` pode melhorar o desempenho em casos específicos, disponibilizando dados armazenados em cache anteriormente enquanto novos dados de cache são gerados em um processo paralelo.

Geralmente, a compensação com a espera por bloqueio é aceitável de uma perspectiva de desempenho. No entanto, à medida que o número de blocos ou entradas de cache aumenta, as esperas de bloqueio demoram mais tempo. Em alguns cenários, a espera pode ser de até **o número de chaves** x **tempo limite de pesquisa** para o processo. Em casos raros, um comerciante pode ter centenas de chaves no cache do `Block/Config`, portanto, mesmo um pequeno tempo limite de pesquisa para um bloqueio pode custar segundos.

>[!IMPORTANT]
>
>O cache obsoleto funciona somente com o cache L2. Para habilitá-lo, adicione `'use_stale_cache' => true` à configuração de nível superior do front-end do cache L2.

A Adobe recomenda habilitar a opção `use_stale_cache` somente para os tipos de cache que mais se beneficiarem dela, incluindo:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

A Adobe não recomenda habilitar a opção `use_stale_cache` para o tipo de cache `default`.

O código a seguir mostra um exemplo de configuração:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Implementação do cache Modern Symfony L2

A partir do Commerce 2.4.9, você pode usar a implementação de cache L2 baseada em cache Symfony (back-end do `symfony_l2`) que fornece uma implementação de cache moderna e compatível com PSR-6, com melhorias significativas de desempenho em relação ao `RemoteSynchronizedCache` tradicional.

>[!NOTE]
>
>No momento, essa funcionalidade está disponível somente para clientes do Adobe Commerce no local 2.4.9. Ele será ativado para o Adobe Commerce na nuvem posteriormente em julho de 2026.

### Benefícios do cache Symfony L2

- **Arquitetura Moderna**: baseada em componentes do Symfony Cache (compatível com PSR-6)
- **Melhor Desempenho**: suporte nativo para serialização Igbinary, compactação gzip e scripts Lua
- **Conexões Persistentes**: reduz a sobrecarga de conexão Redis ou Valkey com o pool de conexões
- **Chaves de pré-carregamento**: suporta o pré-carregamento de chaves de cache para dados críticos
- **Suporte a Cache Obsoleto**: compatibilidade total com a opção `use_stale_cache`
- **Configuração simplificada**: nomes de tipo de back-end de limpeza (`redis`, `valkey`, `file`)

### Exemplo de configuração com o cache L2 do Symfony

Use o tipo de back-end simplificado `symfony_l2` para cache L2:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Cache Symfony L2 com cache obsoleto

Configure front-ends separados para suporte a cache obsoleto:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Opções de back-end para o cache do Symfony L2

| Opção | Tipo | Padrão | Descrição |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | string | `'redis'` | Tipo de back-end remoto: `redis`, `valkey` ou `file` |
| `remote_backend_options` | matriz | `[]` | Configuração de back-end remoto (consulte a documentação do Redis/Valkey) |
| `local_backend` | string | `'file'` | Tipo de infraestrutura local: `file` ou `apcu` |
| `local_backend_options` | matriz | `[]` | Configuração da infraestrutura local |
| `cleanup_percentage` | inteiro | `90` | Limite de limpeza do cache L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Habilitar cache obsoleto para alta disponibilidade |

### Suporte ao Valkey

O back-end `symfony_l2` também oferece suporte a Valkey como back-end remoto:

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

Para obter opções de configuração detalhadas, consulte:
- [Configuração do cache Redis com o Symfony Cache](redis-pg-cache.md)
- [Configuração do cache Valkey com o Symfony Cache](valkey-pg-cache.md)
