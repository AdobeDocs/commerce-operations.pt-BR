---
title: Configuração do cache L2
description: Saiba como configurar o cache L2.
source-git-commit: e5e4cf0b3979a457e706823dd16c88508ec4abd8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Configuração do cache L2

O armazenamento em cache permite uma redução no tráfego de rede entre o armazenamento de cache remoto e o aplicativo Commerce. Uma instância padrão do Commerce transfere cerca de 300 kb por solicitação e o tráfego pode crescer rapidamente para mais de ~1000 solicitações em algumas situações.

Para reduzir a largura de banda da rede para o Redis, armazene os dados de cache localmente em cada nó da Web e use o cache remoto para dois propósitos:

- Verifique a versão dos dados do cache e garanta que o cache mais recente seja armazenado localmente
- Transferir o cache mais recente da máquina remota para a máquina local

O Commerce armazena a versão de dados com hash em Redis, com o sufixo &#39;:hash&#39; anexado à chave regular. Se houver um cache local desatualizado, os dados serão transferidos para a máquina local com um adaptador de cache.

>[!INFO]
>
>Para o Adobe Commerce na infraestrutura de nuvem, considere as práticas recomendadas na [Implementação de cache estendida do Redis](https://support.magento.com/hc/en-us/articles/360049292532) artigo de suporte.

## Exemplo de configuração

Use o exemplo a seguir para modificar ou substituir a seção de cache existente no `app/etc/env.php` arquivo.

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
                ],
                'use_stale_cache' => false,
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

Em que:

- `backend` é a implementação do cache L2.
- `backend_options` é a configuração do cache L2.
   - `remote_backend` é a implementação de cache remoto: Redis ou MySQL.
   - `remote_backend_options` é a configuração de cache remoto.
   - `local_backend` é a implementação de cache local: `Cm_Cache_Backend_File`
   - `local_backend_options` é a configuração de cache local.
      - `cache_dir` é uma opção específica para o cache de arquivos do diretório em que o cache local está armazenado.
   - `use_stale_cache` é um sinalizador que ativa ou desativa o uso de cache obsoleto.

O Adobe recomenda o uso de Redis para armazenamento em cache remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` para o armazenamento de dados em cache local na memória compartilhada, usando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

O Adobe recomenda o uso da variável [`cache preload`](redis-pg-cache.md#redis-preload-feature) , uma vez que diminui drasticamente a pressão sobre Redis. Não esqueça de adicionar o sufixo &#39;:hash&#39; para chaves de pré-carregamento.

## Opções de cache obsoletas

Primeiros passos com o [!DNL Commerce] 2.4. `use_stale_cache` pode melhorar o desempenho em alguns casos específicos.

Geralmente, a compensação com o bloqueio de espera é aceitável do lado do desempenho, mas quanto maior o número de Blocos ou Cache o comerciante tiver, mais tempo será gasto esperando por bloqueios. Em alguns cenários, você pode aguardar uma **número de chaves** \* **tempo limite de pesquisa** quantidade de tempo do processo. Em alguns casos raros, o comerciante pode ter centenas de chaves na `Block/Config` cache, portanto, até mesmo o pequeno tempo limite de pesquisa para bloqueio pode custar segundos.

O cache obsoleto só funciona com um cache L2. Com um cache obsoleto, você poderia enviar um cache desatualizado, enquanto um novo está gerando em um processo paralelo. Para ativar o cache obsoleto, adicione `'use_stale_cache' => true` para a configuração superior do cache L2.

O Adobe recomenda habilitar a variável `use_stale_cache` opção somente para tipos de cache que mais se beneficiam dele, incluindo:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
