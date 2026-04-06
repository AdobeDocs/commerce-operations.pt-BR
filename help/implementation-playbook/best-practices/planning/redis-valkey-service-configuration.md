---
title: Práticas recomendadas para a configuração do serviço Redis e Valkey
description: Saiba como configurar os serviços Redis e Valkey para o Adobe Commerce. Melhore o desempenho do cache com cache L2, conexões slave, cache obsoleto e separação de sessões.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Práticas recomendadas para a configuração do serviço Redis e Valkey

Use essas recomendações para configurar o Redis ou o Valkey para cache e sessões do Adobe Commerce.

- Configurar cache L2
- Habilitar conexão subordinada
- Pré-carregar chaves
- Habilitar cache obsoleto
- Separar cache e sessão
- Compactar o cache
- Exemplos de configuração

>[!NOTE]
>
>Para ambientes de infraestrutura do Commerce na nuvem, verifique se você está usando a versão mais recente do pacote `ece-tools`. Caso contrário, [atualize para a versão mais recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Você pode verificar a versão instalada em seu ambiente local usando o comando da CLI do `composer show magento/ece-tools`.

## Configurar cache L2

Configure o cache L2 definindo a variável de implantação `REDIS_BACKEND` ou `VALKEY_BACKEND` no arquivo de configuração `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configuração Redis]

Para Redis, use:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obter a configuração do ambiente na infraestrutura em nuvem, consulte a referência de configuração [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) no _Guia do Commerce na Infraestrutura em Nuvem_.

Para instalações locais, consulte [Configurar o cache de página do Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) no _Guia de Configuração_.

>[!TAB Configuração de Valkey]

Para Valkey, use:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obter a configuração do ambiente na infraestrutura em nuvem, consulte a referência de configuração [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) no _Guia do Commerce na Infraestrutura em Nuvem_.

Para instalações locais, consulte [Configurar Valkey](../../../configuration/cache/config-valkey.md) no _Guia de Configuração_.

>[!ENDTABS]


### Dimensionamento da memória cache L2 para a Adobe Commerce Cloud

O cache L2 usa um [sistema de arquivos temporário](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) como seu mecanismo de armazenamento. Diferentemente dos armazenamentos de valores-chave especializados, o tmpfs não tem uma política de remoção de chaves, portanto o uso da memória pode crescer sem limites. Para evitar a exaustão, o Adobe Commerce limpa automaticamente o armazenamento L2 quando o uso atinge um limite configurável (95% por padrão). Você pode controlar o consumo de memória solicitando uma montagem `/dev/shm` maior ou reduzindo o limite de limpeza.

Ajuste o uso máximo da memória cache L2 com base nos requisitos do seu projeto. Use um dos seguintes métodos:

- Crie um tíquete de suporte para ajustar o tamanho de montagem `/dev/shm`. Para este cenário, a Adobe recomenda definir o tamanho de montagem do `/dev/shm` para 15 GB.
- Ajuste a propriedade `cleanup_percentage` no nível do aplicativo para limitar o uso do armazenamento e liberar memória disponível para outros serviços.
Você pode ajustar a configuração na configuração de implantação no grupo de configuração de cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>A opção configurável `cleanup_percentage` foi introduzida no Adobe Commerce 2.4.4.

Os seguintes exemplos mostram o código de configuração no arquivo `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configuração Redis]

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configuração de Valkey]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

Os requisitos de cache variam de acordo com a configuração do seu projeto e o código personalizado de terceiros. Dimensione a memória cache L2 para que o cache possa operar sem ocorrências frequentes de limite.

Idealmente, o uso da memória cache L2 estabiliza abaixo do limite para evitar a limpeza frequente do armazenamento.

Você pode verificar o uso da memória de armazenamento em cache L2 em cada nó do cluster executando o seguinte comando da CLI e revisando a linha `/dev/shm`.

```bash
df -h /dev/shm
```

O uso pode variar entre nós, mas deve convergir para um valor semelhante.

## Configurar diretórios personalizados para o cache L2

Ao otimizar o desempenho do cache L2, você pode optar por armazenar os arquivos do cache local em um diretório personalizado de alto desempenho, como um disco RAM (`/dev/shm/`).

Para garantir a consistência em todo o aplicativo e evitar o armazenamento fragmentado em cache, configure as opções de back-end L2 específicas e o registro do diretório global dentro do arquivo `app/etc/env.php`.

**Prática recomendada:** Defina `local_backend_options['cache_dir']` e o `directories['cache']['path']` global.

- **`local_backend_options['cache_dir']`**: Direciona o adaptador de cache de back-end (por exemplo, `Cm_Cache_Backend_File`) para armazenar seus arquivos de cache L2 sincronizados no local especificado.
- **`directories['cache']['path']`**: atualiza o Registro `DirectoryList` do Adobe Commerce, estabelecendo o caminho personalizado como o diretório de cache de sistema definitivo para todo o aplicativo.

### Evitar falhas de diretórios de cache dividido e segmentação do GlusterFS

Se você definir o caminho personalizado exclusivamente no `local_backend_options`, o mecanismo de cache L2 funcionará corretamente, mas o registro do aplicativo global continuará a reconhecer o `var/cache` como o local de cache padrão.

Essa incompatibilidade de configuração resulta em um cenário de &quot;divisão de cérebro&quot; em que extensões de terceiros ou processos principais de fallback gravam arquivos temporários no diretório `var/cache` padrão.

**Impacto crítico na Adobe Commerce Cloud:** em arquiteturas Pro, o diretório `var/` é montado em um sistema de arquivos distribuído compartilhado. Forçar a E/S de cache de alta velocidade através dessa montagem de rede sobrecarrega o cliente e é um acionador primário para **falhas de segmentação do GlusterFS e paralisações em todo o cluster**. A definição de ambas as configurações garante que toda a E/S de cache permaneça estritamente no disco local de alto desempenho.

### Exemplo de configuração

Para impor um único diretório de cache unificado, atualize seu arquivo `env.php` para incluir ambas as configurações:

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## Habilitar conexão subordinada

Habilite a conexão subordinada no arquivo `.magento.env.yaml` para permitir que o Adobe Commerce use uma conexão de cache somente leitura adicional para leituras, ao mesmo tempo em que continua usando o ponto de extremidade primário para gravações. Essa configuração pode reduzir a carga de leitura no serviço de cache principal e distribuir o tráfego de leitura com mais eficiência.

>[!BEGINTABS]

>[!TAB Configuração Redis]

Para Redis, use:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Para obter a configuração do ambiente na infraestrutura do Commerce Cloud, consulte [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) no _Guia de Infraestrutura do Commerce na Nuvem_.

Para instalações locais do Adobe Commerce, configure a nova implementação do cache Redis usando os comandos `bin/magento setup`. Consulte [Usar Redis para cache padrão](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) no _Guia de Configuração_.

>[!TAB Configuração de Valkey]

Para Valkey, use:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obter a configuração do ambiente na infraestrutura do Commerce Cloud, consulte [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) no _Guia de Infraestrutura do Commerce na Nuvem_.

Para instalações locais do Adobe Commerce, configure a nova implementação do cache Valkey usando os comandos `bin/magento setup`. Consulte [Configurar Valkey](../../../configuration/cache/config-valkey.md) no _Guia de Configuração_.

>[!ENDTABS]

## Pré-carregar chaves

O Magento geralmente carrega entradas de cache de Redis ou Valkey, uma chave por vez. O recurso de pré-carregamento permite fornecer uma lista de chaves usadas com frequência que o Magento busca em um único pipeline no primeiro acesso durante uma solicitação. O Magento então mantém os valores obtidos na memória PHP para o resto dessa solicitação, o que reduz viagens de ida e volta repetidas para Redis ou Valkey e pode melhorar o desempenho de inicialização da solicitação para essas chaves.

Você pode identificar chaves usadas com frequência monitorando comandos ativos em Redis ou Valkey:

>[!BEGINTABS]

>[!TAB Configuração da chave de pré-carregamento Redis]

As chaves de pré-carregamento estão configuradas no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para listar as chaves, execute o seguinte comando:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Após 10 segundos, pressione **[!UICONTROL Ctrl+C]**. Em seguida, execute o seguinte comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este log lista as chaves que você pode pré-carregar. Para ver o conteúdo de uma chave, execute o seguinte comando:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Para instalações locais, consulte o [recurso de pré-carregamento Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) no _Guia de Configuração_.

>[!TAB Configuração de chave de pré-carregamento de Valkey]

As chaves de pré-carregamento estão configuradas no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para listar as chaves, execute o seguinte comando:

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Após 10 segundos, pressione **[!UICONTROL Ctrl+C]**. Em seguida, execute o seguinte comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este log lista as chaves que você pode pré-carregar. Para ver o conteúdo de uma chave, execute o seguinte comando:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Para instalações locais, consulte [Recurso de pré-carregamento de Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) no _Guia de Configuração_.

>[!ENDTABS]

## Habilitar cache obsoleto

O cache obsoleto é um recurso de cache L2 de `RemoteSynchronizedCache`. Quando habilitada, a Adobe Commerce pode fornecer um valor de cache local existente de `/dev/shm` enquanto outra solicitação já está regenerando a mesma entrada, em vez de fazer com que cada solicitação simultânea aguarde. Isso reduz os carimbos do cache e a contenção de bloqueio durante a regeneração de entradas de cache caras.

### Como funciona

Com `RemoteSynchronizedCache`, o Magento mantém duas cópias de cada entrada de cache: uma cópia local em `/dev/shm` e uma cópia remota em Redis ou Valkey. Quando a cópia remota não está disponível e já existe um bloqueio de regeneração para essa chave, as solicitações simultâneas podem receber o valor local anterior em vez de aguardar até que o valor novo seja gravado.

Para habilitar o cache obsoleto, configure-o no arquivo `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configurar cache obsoleto para Redis]

Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Configurar cache obsoleto para Valkey]

Para Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>O tipo de cache `full_page` não é relevante para projetos de infraestrutura do Adobe Commerce na nuvem porque eles usam [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

Para instalações locais, consulte [Opções de cache obsoleto](../../../configuration/cache/level-two-cache.md#stale-cache-options) no _Guia de Configuração_.

>[!WARNING]
>
>A configuração acima habilita o cache obsoleto no front-end do cache `default`, o que aplica o comportamento de cache obsoleto a todas as entradas de cache que usam esse front-end. Os principais tipos de cache do Magento geralmente funcionam como esperado com essa configuração. No entanto, se o seu projeto incluir código personalizado ou extensões que gravam no cache por meio da API `\Magento\Framework\App\Cache` genérica (por exemplo, `$this->cache->save()`) sem um front-end de cache dedicado, essas entradas também poderão servir valores obsoletos durante a regeneração.
>
>
>Se isso resultar em um comportamento inesperado em suas personalizações, deixe o cache obsoleto desabilitado no front-end do `default` e habilite-o somente para os tipos de cache selecionados, como geralmente [é feito no local](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Habilitando cache obsoleto por tipo de cache individualmente

Você pode habilitar o cache obsoleto apenas para os tipos de cache selecionados definindo um front-end de cache dedicado no `.magento.env.yaml` e mapeando os tipos de cache selecionados para ele.

Para funcionar corretamente, o front-end personalizado deve ser definido como um front-end completo em `CACHE_CONFIGURATION.frontend`. Definir apenas `use_stale_cache: true` para um novo nome de front-end não é suficiente.

**Exemplo de configurações**

>[!BEGINTABS]

>[!TAB Configurar cache obsoleto para Redis]

Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Configurar cache obsoleto para Valkey]

Para Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Se o front-end de origem estiver configurado com opções de back-end adicionais, como compactação, tentativas, chaves de pré-carregamento ou outros valores de ajuste, copie essas opções para `stale_cache_enabled` para que o novo front-end mantenha o mesmo comportamento.


## Instâncias separadas de cache e sessão

Separar o cache das sessões permite que você as gerencie independentemente. Ele reduz a contenção entre o cache e o tráfego da sessão, impede que a pressão relacionada ao cache afete as sessões e permite que cada instância Redis ou Valkey seja dimensionada e ajustada para sua própria carga de trabalho.

Siga as etapas abaixo para provisionar uma instância dedicada para sessões:

>[!BEGINTABS]

>[!TAB Redis]

1. Atualize o arquivo de configuração `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
     type: redis:6.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Atualize o arquivo de configuração `.magento.app.yaml`.

   ```yaml
      relationships:
        database: "mysql:mysql"
        redis: "redis:redis"
        redis-session: "redis-session:redis"   # Relationship of the new Redis instance
        search: "search:elasticsearch"
        rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Solicite uma nova instância de Redis dedicada às sessões nos ambientes de produção e preparo.

   Envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Inclua os arquivos de configuração `.magento/services.yaml` e `.magento.app.yaml` atualizados.

   Essa atualização não causa tempo de inatividade, mas requer uma implantação para ativar o novo serviço.

1. Verifique se a nova instância está em execução e observe o número da porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Adicione o número da porta ao arquivo de configuração `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configure a porta da sessão Redis somente se `ece-tools` não puder detectá-la automaticamente na definição do serviço de sessão Redis `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Defina `disable_locking` como `1` para obter o melhor desempenho. Em casos raros em que as condições de corrida ocorrem devido à alta atividade de sessão simultânea, defina como `0` para habilitar o bloqueio.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Remover sessões do [banco de dados padrão](../../../configuration/cache/redis-pg-cache.md) (`db 0`) na instância de cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Chave de valor]

1. Atualize o arquivo de configuração `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Atualize o arquivo de configuração `.magento.app.yaml`.

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Solicite uma nova instância do Valkey dedicada às sessões nos ambientes de Produção e Preparo.

   Envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Inclua os arquivos de configuração `.magento/services.yaml` e `.magento.app.yaml` atualizados.

   Essa atualização não causa tempo de inatividade, mas requer uma implantação para ativar o novo serviço.

1. Verifique se a nova instância está em execução e observe o número da porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Adicione o número da porta ao arquivo de configuração `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configure a porta da sessão Valkey apenas se `ece-tools` não puder detectá-la automaticamente a partir da definição do serviço de sessão Valkey `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Defina `disable_locking` como `1` para obter o melhor desempenho. Em casos raros em que as condições de corrida ocorrem devido à alta atividade de sessão simultânea, defina como `0` para habilitar o bloqueio.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Remover sessões do [banco de dados padrão](../../../configuration/cache/redis-pg-cache.md) (`db 0`) na instância de cache Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compactação de cache

Se você usar mais de 6 GB de Redis ou Valkey `maxmemory`, poderá habilitar a compactação de cache para reduzir o espaço consumido pelas chaves. Esteja ciente de que essa configuração troca o desempenho do lado do cliente por economia de memória. Se você tiver capacidade extra do CPU, considere ativá-la. Consulte [Usar Redis para armazenamento de sessão](../../../configuration/cache/redis-session.md) ou [Usar Valkey para armazenamento de sessão](../../../configuration/cache/valkey-session.md) no _Guia de Configuração_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Habilitar liberação assíncrona

Para habilitar `lazyfree` no Adobe Commerce na infraestrutura em nuvem, envie um [tíquete de Suporte Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando que a seguinte configuração Redis ou Valkey seja aplicada aos seus ambientes:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Quando `lazyfree` está habilitado, Redis ou Valkey descarrega a recuperação de memória em threads em segundo plano para remoções, expirações, exclusões iniciadas pelo servidor, exclusões de usuário e liberações de conjunto de dados de réplica. Isso reduz o bloqueio do thread principal e pode reduzir a latência da solicitação.

>[!NOTE]
>
>A opção `lazyfree-lazy-user-del yes` faz com que o comando `DEL` se comporte como `UNLINK`, o que desvincula as chaves imediatamente e libera sua memória de forma assíncrona.

>[!WARNING]
>
>Como a liberação ocorre em segundo plano, a memória usada por chaves excluídas, expiradas ou removidas permanece alocada até que as threads em segundo plano concluam o trabalho. Se sua instância Redis ou Valkey já estiver sob pressão de memória estreita, teste com cuidado e considere reduzir a pressão da memória primeiro. Por exemplo, desative o Cache de bloco para casos específicos e separe as instâncias de cache e Redis de sessão conforme descrito acima.

## Habilitar E/S multithread

Para habilitar a thread de E/S do Redis na Adobe Commerce na infraestrutura em nuvem, envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando a configuração da thread de E/S abaixo. Essa configuração pode melhorar o throughput descarregando leituras e gravações de soquete e análise de comandos do thread principal, ao custo de um maior uso do CPU. Valide o sob o carregamento e monitore seus hosts.

>[!BEGINTABS]

>[!TAB Configurar threads de E/S para Redis]

Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Configurar threads de E/S para Valkey]

Para Valkey:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>As threads de E/S paralelizam somente a E/S do cliente e a análise. A execução do comando Redis permanece com um único thread.

>[!WARNING]
>
>A ativação de threads de E/S pode aumentar o uso do CPU e não beneficia todas as cargas de trabalho. Comece com um valor e referencial conservadores. Se a latência aumentar ou o CPU ficar saturado, reduza `io-threads` ou desabilite leituras em threads de E/S.


## Aumentar tempos limite e tentativas do cliente

Aumente a tolerância do cliente de cache Redis ou Valkey para períodos curtos de saturação ajustando as opções de back-end em `.magento.env.yaml`.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Essas configurações podem reduzir erros intermitentes de conexão e tempo limite de leitura durante picos curtos, repetindo a configuração da conexão e permitindo mais tempo para respostas do Redis ou Valkey.

>[!NOTE]
>
>Essas configurações podem ajudar com o congestionamento breve, mas não corrigem a sobrecarga persistente.

## Exemplos de configuração

Use os exemplos a seguir como ponto de partida para as configurações do serviço Redis ou Valkey.


### Aplicar todas as recomendações de práticas recomendadas

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Exemplo de configuração de Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Aplicar todas as recomendações de práticas recomendadas e separar o cache obsoleto por tipo de cache

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Chave de valor]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Informações adicionais

Consulte os seguintes tópicos relacionados:

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para armazenamento de sessão](../../../configuration/cache/redis-session.md)
- [Usar Valkey para cache padrão](../../../configuration/cache/valkey-pg-cache.md)
- [Usar Valkey para armazenamento de sessão](../../../configuration/cache/valkey-session.md)
