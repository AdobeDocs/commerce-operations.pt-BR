---
title: Configuração do cache L2
description: Saiba como configurar o cache L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Configuração do cache L2

O armazenamento em cache permite uma redução no tráfego de rede entre o armazenamento em cache remoto e o aplicativo Commerce. Uma instância padrão do Commerce transfere cerca de 300 kb por solicitação e o tráfego pode crescer rapidamente para mais de ~1000 solicitações em algumas situações.

Para reduzir a largura de banda da rede para Redis, armazene os dados do cache localmente em cada nó da Web e use o cache remoto para duas finalidades:

- Verifique a versão dos dados do cache e certifique-se de que o cache mais recente esteja armazenado localmente
- Transferir o cache mais recente do computador remoto para o computador local

O Commerce armazena a versão de dados com hash em Redis, com o sufixo &quot;:hash&quot; anexado à chave regular. Se houver um cache local desatualizado, os dados serão transferidos para o computador local com um adaptador de cache.

>[!INFO]
>
>Para o Adobe Commerce na infraestrutura em nuvem, é possível usar [implantar variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) para configuração do cache L2.

## Exemplo de configuração

Use o exemplo a seguir para modificar ou substituir a seção de cache existente na `app/etc/env.php` arquivo.

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
- `backend_options` é a configuração do cache L2.
   - `remote_backend` é a implementação do cache remoto: Redis ou MySQL.
   - `remote_backend_options` é a configuração do cache remoto.
   - `local_backend` é a implementação do cache local: `Cm_Cache_Backend_File`
   - `local_backend_options` é a configuração do cache local.
   - `cache_dir` é uma opção específica do cache de arquivos para o diretório onde o cache local está armazenado.

O Adobe recomenda o uso de Redis para cache remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` para o armazenamento local de dados em cache na memória compartilhada, usando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

A Adobe recomenda o uso da [`cache preload`](redis-pg-cache.md#redis-preload-feature) uma vez que diminui drasticamente a pressão sobre o Redis. Não se esqueça de adicionar o sufixo &#39;:hash&#39; para chaves de pré-carregamento.

## Opções de cache obsoletas

Começando com [!DNL Commerce] 2.4, a `use_stale_cache` pode melhorar o desempenho em alguns casos específicos.

Geralmente, a compensação com espera por bloqueio é aceitável do lado do desempenho, mas quanto maior o número de blocos ou cache que o comerciante tem, mais tempo é gasto aguardando bloqueios. Em alguns cenários, você pode aguardar um **números de chaves** \* **tempo limite da pesquisa** quantidade de tempo do processo. Em alguns casos raros, o comerciante pode ter centenas de chaves na `Block/Config` cache, portanto, até mesmo o tempo limite de pesquisa pequeno para bloqueio pode custar segundos.

O cache obsoleto funciona somente com um cache L2. Com um cache obsoleto, você pode enviar um cache desatualizado, enquanto um novo é gerado em um processo paralelo. Para habilitar cache obsoleto, adicione `'use_stale_cache' => true` para configurar o cache L2.

O Adobe recomenda ativar o `use_stale_cache` opção somente para tipos de cache que mais se beneficiam dele, incluindo:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

O Adobe não recomenda ativar o `use_stale_cache` opção para a variável `default` tipo de cache.

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
