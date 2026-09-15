---
title: Configuração de cache L2 para otimização de desempenho
description: Saiba como configurar o cache L2 no Adobe Commerce no local para reduzir o tráfego de rede e melhorar o desempenho. Compare a implementação herdada do RemoteSynchronizedCache com a implementação moderna do Symfony L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce no local."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# Configuração do cache L2 para otimização do desempenho

O cache L2 (de dois níveis) reduz o tráfego de rede entre o serviço de cache remoto e o aplicativo Commerce, adicionando uma camada de cache local em cada nó da Web. Uma instância padrão do Commerce pode transferir cerca de 300 KB por solicitação. Em grandes volumes de solicitação, o tráfego de rede resultante pode ser substancial.

Com o cache L2, cada nó da Web armazena os dados acessados com frequência localmente e usa o cache remoto para duas finalidades:

- Verificando a versão dos dados do cache para garantir que o cache mais recente esteja armazenado localmente
- Transferindo dados atualizados do cache do serviço de cache remoto para o computador local

O Commerce armazena a versão de dados com hash no cache remoto, com o sufixo `:hash` anexado à chave regular. Quando o cache local está desatualizado, os dados são obtidos do serviço de cache remoto por meio de um adaptador de cache.

A implementação do cache L2 disponível depende da versão e do nível de patch do Commerce:

| Implementação | Versão do Commerce | Serviço de cache remoto | Descrição |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | Antes do 2.4.9, quando suportado | Redis ou Valkey, dependendo do nível de versão e patch | Cache de dois níveis baseado em Zend com `Cm_Cache_Backend_File` para armazenamento local |
| [Symfony L2 (`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9 e posterior | Valkey | Implementação moderna do Symfony Cache com conformidade com o PSR-6 |

## Configuração do cache L2 RemoteSynchronizedCache


>[!NOTE]
>
>Esta seção aborda a configuração L2 do `RemoteSynchronizedCache` para versões do Adobe Commerce no local anteriores à versão 2.4.9, onde há suporte na versão exata do Commerce e na matriz de suporte em nível de patch.
>
>Para o Adobe Commerce 2.4.9 e posterior, use Valkey com o [cache L2 do Symfony](#symfony-l2-cache-implementation).
>
>Para a infraestrutura do Adobe Commerce na nuvem, configure o cache L2 por meio de variáveis de implantação no `.magento.env.yaml`. Não edite `app/etc/env.php` diretamente. Consulte [Configurar cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

As instruções de configuração de cache dependem da versão do Commerce:

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
  - `remote_backend` é a implementação de cache remoto: Redis ou Valkey, dependendo da versão do Commerce e do suporte no nível de patch.
  - `remote_backend_options` é a configuração de cache remoto.
  - `local_backend` é a implementação de cache local: `Cm_Cache_Backend_File`.
  - `local_backend_options` é a configuração de cache local.
  - `cache_dir` é uma opção específica do cache de arquivos que define o diretório onde o cache local está armazenado.

Para versões do Adobe Commerce anteriores à 2.4.9 que oferecem suporte a Redis ou Valkey, a Adobe recomenda o uso de Redis ou Valkey para cache remoto, conforme suportado pela versão exata, e `Cm_Cache_Backend_File` para cache local. O cache local é normalmente armazenado em um sistema de arquivos temporário, como `/dev/shm/`:

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

A Adobe recomenda usar o recurso `[cache preload](redis-pg-cache.md#redis-preload-feature)`, pois ele reduz a carga em Redis. Adicione o sufixo `:hash` para chaves de pré-carregamento.

## Opções de cache obsoletas

A partir do Commerce 2.4, a opção `use_stale_cache` pode melhorar o desempenho em casos específicos, disponibilizando dados armazenados em cache anteriormente enquanto novos dados de cache são gerados em um processo paralelo. Os tipos de cache recomendados e as compensações descritas nesta seção se aplicam às implementações do `RemoteSynchronizedCache` e do `symfony_l2`. Para obter um exemplo de configuração `symfony_l2`, consulte [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

Geralmente, a compensação com a espera por bloqueio é aceitável de uma perspectiva de desempenho. No entanto, à medida que o número de blocos ou entradas de cache aumenta, as esperas de bloqueio demoram mais tempo. Em alguns cenários, a espera pode ser de até **o número de chaves** x **tempo limite de pesquisa** para o processo. Em casos raros, um usuário pode ter centenas de chaves no cache do `Block/Config`, portanto, mesmo um pequeno tempo limite de pesquisa para um bloqueio pode custar segundos.

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

O código a seguir mostra um exemplo de configuração para o back-end do `RemoteSynchronizedCache`. Para um exemplo de `symfony_l2`, consulte [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

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

## Implementação do cache Symfony L2

Nas versões 2.4.9+ do Commerce, use a implementação de cache L2 do Symfony (back-end do `symfony_l2`) em vez de `RemoteSynchronizedCache`. O cache L2 do Symfony fornece uma implementação de cache compatível com o PSR-6 usando o Valkey.

>[!IMPORTANT]
>
>O Redis não é compatível com a configuração de cache nas seguintes versões do Adobe Commerce:
>
>- Adobe Commerce 2.4.9 e posterior
>- Patches do Adobe Commerce 2.4.8-p4 e posteriores
>- Adobe Commerce 2.4.7-p9 e patches posteriores
>- Patches do Adobe Commerce 2.4.6-p14 e posteriores
>- Patches do Adobe Commerce 2.4.5-p16 e posteriores
>
>Para essas versões, configure o Valkey.
>
>Se você configurar o `symfony_l2` para cache L2 no Adobe Commerce 2.4.9 ou posterior, deverá usar o Valkey para o serviço de cache remoto. Consulte [configurar Valkey](config-valkey.md).

### Migração de RemoteSynchronizedCache para Symfony L2

Se você estiver atualizando uma instalação local do back-end do `RemoteSynchronizedCache` para o `symfony_l2`, revise o seguinte antes de atualizar o `app/etc/env.php`. Não é suficiente alterar apenas o valor `backend`. A estrutura de configuração, os nomes de chave e alguns comportamentos padrão são diferentes.

- **A estrutura de configuração foi alterada.** `remote_backend`, `remote_backend_options` e `local_backend` usam valores diferentes em `symfony_l2`. Por exemplo, `remote_backend` torna-se `'valkey'` em vez de um nome de classe totalmente qualificado. Use o [exemplo de configuração](#configuration-example-with-symfony-l2-cache) abaixo como ponto de partida, em vez de editar sua configuração existente do `RemoteSynchronizedCache` no local.

- **`preload_keys`não é recomendado com `symfony_l2`.** Se a configuração do `RemoteSynchronizedCache` incluir o `preload_keys`, remova-o como parte da migração. O pré-carregamento de chaves não melhora o desempenho em `symfony_l2` e pode aumentar a carga em Valkey acionando pesquisas de chave adicionais e desnecessárias.

- **A compactação requer um sinalizador explícito.** A configuração `compression_lib` sozinha não habilita a compactação em `symfony_l2`. Consulte [Opções de back-end para o cache L2 do Symfony](#backend-options-for-symfony-l2-cache) para a configuração `compress_data` necessária.

- **As implantações locais configuradas manualmente não habilitam o cache obsoleto por padrão.** O padrão de `use_stale_cache` é `false` em `symfony_l2` (consulte a [tabela de opções de back-end](#backend-options-for-symfony-l2-cache)). Se a configuração do `RemoteSynchronizedCache` usou o front-end `stale_cache_enabled`, você deverá recriá-lo explicitamente usando o padrão no [cache L2 do Symfony com cache obsoleto](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>Os ambientes do Adobe Commerce na nuvem que definem a variável de implantação `VALKEY_BACKEND: symfony_l2` têm sua configuração L2 completa, incluindo o front-end `stale_cache_enabled`, gerada automaticamente pelo `ece-tools`. Consulte [Configurar o cache L2 do Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) para ver o comportamento específico da Nuvem.

- **Redis não é um back-end remoto com suporte para `symfony_l2`.** Migrar para o Valkey como parte dessa alteração. Consulte [configurar Valkey](config-valkey.md).

### Exemplo de configuração com o cache L2 do Symfony

>[!IMPORTANT]
>
>Este exemplo de `app/etc/env.php` se aplica somente a instalações locais. Para Adobe Commerce na infraestrutura em nuvem, não edite `app/etc/env.php` diretamente. Defina `VALKEY_BACKEND: symfony_l2` em `.magento.env.yaml`. `ece-tools` gera e mantém a configuração do cache L2 durante a implantação. Consulte [Configurar cache L2 do Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

No arquivo `app/etc/env.php`, use o tipo de back-end `symfony_l2` simplificado para cache L2. Este exemplo não inclui a configuração `preload_keys`, que não é recomendada com `symfony_l2`. Para obter detalhes, consulte [Migrando de RemoteSynchronizedCache para Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

O exemplo define `cleanup_percentage` como `90`. O valor padrão é `95`. Ajuste esse valor de acordo com o armazenamento de cache local disponível e com os requisitos de sua implantação do Commerce.

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
| -------- | ------ | --------- | ----------- |
| `remote_backend` | string | `'valkey'` | Back-end do cache remoto. Use `valkey` com Symfony L2. O Redis não é oficialmente compatível. |
| `remote_backend_options` | matriz | `[]` | Configuração de back-end do Valkey remoto |
| `local_backend` | string | `'file'` | Tipo de infraestrutura local: `file` ou `apcu` |
| `local_backend_options` | matriz | `[]` | Configuração da infraestrutura local |
| `cleanup_percentage` | inteiro | `95` | Limite de limpeza do cache L1, expresso como uma porcentagem de 1 a 100 |
| `use_stale_cache` | booleano | `false` | Habilita o cache obsoleto para o front-end |
| `compress_data` | booleano | `false` | Habilita a compactação quando combinada com `compression_lib`. Defina esta opção nas opções de back-end remotas do Valkey. |
| `persistent` | booleano | `true` | Controla conexões persistentes com o back-end remoto. Defina como `false` (`'0'`) para corresponder ao comportamento do cache Zend, que assume o padrão de conexões não persistentes. |

>[!NOTE]
>
>A opção `frontend_options.write_control` se aplica à configuração `RemoteSynchronizedCache` e não se aplica a `symfony_l2`.

### Desempenho e confiabilidade aprimorados do cache Symfony L2

>[!NOTE]
>
>Essas melhorias se aplicam às implantações do Adobe Commerce 2.4.9 que usam o `symfony_l2` e estão disponíveis no patch ACP2E-5132.
>
>Para o Adobe Commerce no local, aplique este patch usando a Ferramenta de correções de qualidade (QPT). Para a infraestrutura do Adobe Commerce na nuvem, o patch está incluído no pacote Cloud Patches for Commerce, que é uma dependência de `ece-tools`. Atualize para a versão mais recente do `ece-tools` para receber os patches de nuvem mais recentes durante a implantação.

As atualizações mais recentes melhoram a escalabilidade do cache L2 do Symfony, reduzem a E/S desnecessária do sistema de arquivos e melhoram a consistência e a confiabilidade do cache.

#### Armazenamento otimizado de tags de cache do Symfony L2

Para implantações de cache do Symfony L2 com suporte do Valkey, as tags de cache são armazenadas exclusivamente no Valkey. Isso elimina gravações redundantes no índice de tags do sistema de arquivos, reduz a E/S de disco e impede o crescimento desnecessário do diretório `var/cache/symfony/tags/`.

#### Comportamento aprimorado do cache baseado em arquivos

Para implantações que usam o cache baseado em arquivos (sem Valkey), o índice de tag local continua sendo mantido para oferecer suporte à invalidação do cache. O índice de tag agora é gravado no `cache_dir` configurado, em vez do local `var/cache` previamente codificado, garantindo um uso consistente do diretório de cache e melhor suporte para configurações de cache personalizadas.

#### Correção de associação de tag obsoleta após a remarcação

A remarcação de uma entrada de cache pode deixá-la associada a tags às quais ela não pertence mais. As associações de tag obsoletas agora são limpas na remarcação, portanto, as entradas de cache são invalidadas somente pelas tags atribuídas a elas no momento.

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
- Reduz os carimbos de regeneração para `use_stale_cache` entradas ao selecionar um único regenerador por chave em vez de cada solicitação simultânea recompilar a entrada.

Para obter opções de configuração detalhadas, consulte:

- [Configuração do cache Valkey com o Symfony Cache](valkey-pg-cache.md)
