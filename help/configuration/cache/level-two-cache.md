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
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# Configuração do cache L2 para otimização do desempenho

O cache L2 (de dois níveis) reduz o tráfego de rede entre o armazenamento remoto em cache (Redis ou Valkey) e o aplicativo Commerce, adicionando uma camada de cache local em cada nó da Web. Uma instância padrão do Commerce transfere cerca de 300 KB por solicitação, e o tráfego pode aumentar rapidamente para mais de 1000 solicitações em algumas situações.

Com o cache L2, cada nó da Web armazena os dados acessados com frequência localmente e usa o cache remoto para duas finalidades:

- Verificando a versão dos dados do cache para garantir que o cache mais recente seja armazenado localmente
- Transferindo dados atualizados do cache do armazenamento remoto para o computador local

O Commerce armazena a versão de dados com hash no cache remoto, com o sufixo `:hash` anexado à chave regular. Quando o cache local está desatualizado, os dados são obtidos da máquina remota por meio de um adaptador de cache.

Há duas implementações de cache L2 disponíveis no Adobe Commerce:

| Implementação | Versão | Descrição |
| -------------- | ------- | ----------- |
| [Herdados (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Cache de dois níveis baseado em Zend com `Cm_Cache_Backend_File` para armazenamento local |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 baseado em cache Symfony com conformidade PSR-6 e desempenho aprimorado. Suporta Valkey. |

O cache L2 do Symfony é a implementação recomendada para o Adobe Commerce 2.4.9 e versões posteriores. Ele fornece uma implementação de cache moderna e compatível com PSR-6, com melhorias significativas de desempenho em relação ao `RemoteSynchronizedCache` tradicional.

## Configuração herdada do cache L2 (RemoteSynchronizedCache)

As instruções de configuração do cache L2 herdado se aplicam às versões mais antigas do Adobe Commerce. Se você estiver na versão 2.4.9 ou posterior do Adobe Commerce, use o Valkey com a [implementação do cache Modern Symfony L2](#modern-symfony-l2-cache-implementation).

>[!NOTE]
>
>Esta página aborda somente a configuração local. Para o Adobe Commerce na Nuvem, consulte [Configurar cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Para versões locais do Adobe Commerce que oferecem suporte a Redis, use o exemplo a seguir para modificar ou substituir a seção de cache existente no arquivo `app/etc/env.php`.

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
]
```

Onde:

- `backend` é a implementação do cache L2.
- `backend_options` é a configuração de cache L2.
  - `remote_backend` é a implementação de cache remoto: Redis ou MySQL.
  - `remote_backend_options` é a configuração de cache remoto.
  - `local_backend` é a implementação de cache local: `Cm_Cache_Backend_File`.
  - `local_backend_options` é a configuração de cache local.
  - `cache_dir` é uma opção específica de cache de arquivo para o diretório onde o cache local está armazenado.

Para versões do Adobe Commerce anteriores à 2.4.9 que oferecem suporte a Redis, a Adobe recomenda o uso de Redis para cache remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` para o cache local de dados na memória compartilhada, usando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`.

A Adobe recomenda o uso do recurso [`cache preload`](redis-pg-cache.md#redis-preload-feature), pois ele diminui drasticamente a pressão sobre o Redis. Não se esqueça de adicionar o sufixo `:hash` para chaves de pré-carregamento.

## Opções de cache obsoletas

A partir do Commerce 2.4, a opção `use_stale_cache` pode melhorar o desempenho em casos específicos, disponibilizando dados armazenados em cache anteriormente enquanto novos dados de cache são gerados em um processo paralelo. Os tipos de cache recomendados e as compensações descritas nesta seção se aplicam às implementações `RemoteSynchronizedCache` e `symfony_l2` herdadas. Para obter um exemplo de configuração `symfony_l2`, consulte [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

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

O código a seguir mostra um exemplo de configuração para o back-end herdado `RemoteSynchronizedCache`. Para um exemplo de `symfony_l2`, consulte [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

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

Nas versões 2.4.9+ do Commerce, use a implementação de cache L2 baseada em cache Symfony (back-end do `symfony_l2`) em vez do cache L2 herdado. O cache L2 do Symfony fornece uma implementação de cache moderna e compatível com PSR-6, com melhorias significativas de desempenho em relação ao `RemoteSynchronizedCache` tradicional.

>[!IMPORTANT]
>
>O Redis não é suportado como back-end de cache remoto que começa com:
>
>- Adobe Commerce 2.4.9 e posterior
>- Patches 2.4.8-p4 e posteriores
>- Patches 2.4.7-p9 e posteriores
>- Patches 2.4.6-p14 e posteriores
>- Patches 2.4.5-p16 e posteriores
>
>Se você estiver atualizando versões anteriores a essas, configure a Valkey e atualize sua configuração de cache para usar o `symfony_l2`. Consulte [configurar Valkey](config-valkey.md) e [Requisitos do Sistema](../../installation/system-requirements.md).

### Benefícios do cache Symfony L2

- **Arquitetura moderna:** baseada em componentes do Symfony Cache (compatível com PSR-6)
- **Melhor desempenho:** suporte nativo para serialização Igbinary, compactação gzip e scripts Lua
- **Conexões persistentes:** reduz a sobrecarga da conexão Valkey com o pool de conexões
- **Chaves de pré-carregamento:** dá suporte ao pré-carregamento da chave de cache para dados críticos
- **Suporte a cache obsoleto:** compatibilidade total com a opção `use_stale_cache`
- **Configuração simplificada:** nomes de tipo de back-end de limpeza (`valkey`, `file`)

### Migração de RemoteSynchronizedCache para Symfony L2

Se você estiver atualizando uma instalação local do back-end herdado `RemoteSynchronizedCache` para `symfony_l2`, revise o seguinte antes de atualizar `app/etc/env.php`. Não é suficiente alterar apenas o valor `backend`. A estrutura de configuração, os nomes de chave e alguns comportamentos padrão são diferentes.

- **A estrutura de configuração foi alterada.** `remote_backend`, `remote_backend_options` e `local_backend` usam valores diferentes em `symfony_l2`. Por exemplo, `remote_backend` torna-se `'valkey'` em vez de um nome de classe totalmente qualificado. Use o [exemplo de configuração](#configuration-example-with-symfony-l2-cache) abaixo como ponto de partida, em vez de editar a configuração herdada existente.

- **`preload_keys`não é recomendado com `symfony_l2`.** Se sua configuração herdada inclui `preload_keys`, remova-a como parte da migração. O pré-carregamento de chaves não melhora o desempenho em `symfony_l2` e pode aumentar a carga em Valkey acionando pesquisas de chave adicionais e desnecessárias.

- **A compactação requer um sinalizador explícito.** A configuração `compression_lib` sozinha não habilita a compactação em `symfony_l2`. Consulte [Opções de back-end para o cache L2 do Symfony](#backend-options-for-symfony-l2-cache) para a configuração `compress_data` necessária.

- **Por padrão, o cache obsoleto não está habilitado para implantações locais configuradas manualmente.** O padrão de `use_stale_cache` é `false` em `symfony_l2` (consulte a [tabela de opções de back-end](#backend-options-for-symfony-l2-cache)). Se sua configuração herdada usou o front-end do `stale_cache_enabled`, você deve recriá-lo explicitamente usando o padrão no [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>Os ambientes do Adobe Commerce na nuvem que definem a variável de implantação `VALKEY_BACKEND: symfony_l2` têm sua configuração L2 completa, incluindo o front-end `stale_cache_enabled`, gerada automaticamente pelo `ece-tools`. Consulte [Configurar o cache L2 do Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) para ver o comportamento específico da Nuvem.

- **Redis não é um back-end remoto com suporte para `symfony_l2`.** Migrar para o Valkey como parte dessa alteração. Consulte [configurar Valkey](config-valkey.md).

### Exemplo de configuração com o cache L2 do Symfony

>[!NOTE]
>
>Este exemplo é para a configuração `app/etc/env.php` local. Para o Adobe Commerce na Nuvem, a configuração do cache é gerenciada automaticamente por `ece-tools`. Em vez de editar diretamente `env.php`, consulte [Configurar cache L2 do Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

No arquivo `app/etc/env.php`, use o tipo de back-end `symfony_l2` simplificado para cache L2. Este exemplo não inclui a configuração `preload_keys`, que não é recomendada com `symfony_l2`. Para obter detalhes, consulte [Migrando de RemoteSynchronizedCache para Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

Consulte [Opções de cache obsoleto](#stale-cache-options) para saber quais tipos de cache se beneficiam do cache obsoleto e por quê.

Use o exemplo a seguir para configurar front-ends separados para o suporte a cache obsoleto do `symfony_l2`:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | string | `'valkey'` | Tipo de back-end remoto: `valkey` ou `file`. Use `valkey` para cache L2. |
| `remote_backend_options` | matriz | `[]` | Configuração de back-end remoto (consulte a documentação do Valkey) |
| `local_backend` | string | `'file'` | Tipo de infraestrutura local: `file` ou `apcu` |
| `local_backend_options` | matriz | `[]` | Configuração da infraestrutura local |
| `cleanup_percentage` | inteiro | `95` | Limite de limpeza do cache L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Habilitar cache obsoleto para alta disponibilidade |
| `compress_data` | booleano | `false` | Habilita a compactação quando combinada com `compression_lib`. A configuração `compression_lib` sozinha não habilita a compactação. |
| `persistent` | booleano | `true` | Controla conexões persistentes com o back-end remoto. Defina como `false` (`'0'`) para corresponder ao comportamento do cache Zend herdado, que assume o padrão de conexões não persistentes. |


>[!NOTE]
>
>- A opção `remote_backend` também aceita um valor de `redis`, mas não há suporte oficial para Redis (consulte a observação acima em [Implementação de cache Modern Symfony L2](#modern-symfony-l2-cache-implementation)).
>
>- `frontend_options.write_control`, usado na configuração `RemoteSynchronizedCache` herdada, não se aplica a `symfony_l2`.

### Desempenho e confiabilidade aprimorados do cache Symfony L2

>[!NOTE]
>
>Essas melhorias se aplicam às implantações do Adobe Commerce 2.4.9 que usam o `symfony_l2` e estão disponíveis no patch ACP2E-5132. Para o Adobe Commerce no local, aplique este patch usando a Ferramenta de correções de qualidade (QPT). Para o Adobe Commerce na Nuvem, este patch é entregue automaticamente via [Patches da Nuvem para o Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest).

As atualizações mais recentes melhoram a escalabilidade do cache L2 do Symfony, reduzem a E/S desnecessária do sistema de arquivos e melhoram a consistência e a confiabilidade do cache.

#### Armazenamento otimizado de tags de cache do Symfony L2

Otimização do comportamento do cache do Symfony L2 para implantações com suporte da Valkey, eliminando gravações redundantes de índice de tags no sistema de arquivos. As tags de cache agora são armazenadas exclusivamente no Valkey, alinhando o comportamento do cache Symfony L2 com a implementação do cache herdado. Isso reduz a E/S de disco desnecessária, melhora o desempenho de gravação de cache e impede o crescimento do diretório `var/cache/symfony/tags/`.

#### Comportamento aprimorado do cache baseado em arquivos

Para implantações que usam o cache baseado em arquivos (sem Valkey), o índice de tag local continua sendo mantido para oferecer suporte à invalidação do cache. O índice de tag agora é gravado no `cache_dir` configurado, em vez do local `var/cache` previamente codificado, garantindo um uso consistente do diretório de cache e melhor suporte para configurações de cache personalizadas.

#### Correção de associação de tag obsoleta após a remarcação

A remarcação de uma entrada de cache pode deixá-la associada a tags às quais ela não pertencia mais. As associações de tag obsoletas agora são limpas na remarcação, portanto, as entradas de cache são invalidadas somente pelas tags atribuídas a elas no momento.

#### Correção de gravação remota redundante para salvamentos inalterados

Salvar uma entrada de cache com conteúdo inalterado ainda acionava uma gravação no back-end remoto (Valkey). Os salvamentos agora são ignorados quando o conteúdo não é alterado, reduzindo as gravações remotas desnecessárias.

#### Correção de remoção baseada em tamanho N1 (cleanup_percentage)

O limite `cleanup_percentage` usado para remoção baseada no tamanho L1 não disparou a limpeza de forma consistente. A remoção do cache L1 agora respeita corretamente o `cleanup_percentage` configurado.

#### Bloqueio de regeneração para cache obsoleto

Quando `use_stale_cache` está habilitado e a cópia remota de uma entrada está temporariamente indisponível, apenas um processo agora adquire um bloqueio de vida curta para regenerar essa entrada. Outras solicitações simultâneas para a mesma entrada continuam a servir o valor local existente em vez de regenerá-lo, reduzindo os carimbos de regeneração e a carga de back-end redundante.

#### Impacto

- Elimina gravações redundantes de índice de tags do sistema de arquivos para implantações de cache do Symfony L2 com suporte da Valkey, reduzindo a E/S de disco e evitando o crescimento desnecessário do diretório `var/cache/symfony/tags/`.
- Garante que as implantações de cache baseadas em arquivo usem consistentemente o `cache_dir` configurado para o índice de tag local, preservando o comportamento de invalidação do cache.
- Evita a invalidação incorreta do cache causada por associações de tag obsoletas deixadas para trás após a remarcação.
- Reduz gravações remotas desnecessárias para salvamentos inalterados de cache, diminuindo a carga de rede e back-end.
- Garante que a remoção do cache L1 acione de forma confiável no limite `cleanup_percentage` configurado.
- Reduz os carimbos de regeneração para `use_stale_cache` entradas ao selecionar um único regenerador por chave, em vez de cada solicitação simultânea para recriá-lo.

Para obter opções de configuração detalhadas, consulte:

- [Configuração do cache Valkey com o Symfony Cache](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [Visão geral do armazenamento em cache e opções de configuração](caching-overview.md)
>- [Opções de back-end do cache e referência de armazenamento](cache-options.md)
>- [Configurar front-ends e tipos de cache](cache-types.md)
>- [Configurar Redis para cache padrão e de página](redis-pg-cache.md)
