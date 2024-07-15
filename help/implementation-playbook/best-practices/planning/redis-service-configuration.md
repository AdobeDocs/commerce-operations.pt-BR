---
title: Práticas recomendadas para a configuração do serviço Redis
description: Saiba como melhorar o desempenho do cache usando a implementação do cache Redis estendido para Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 6772c4fe31cfcd18463b9112f12a2dc285b39324
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Práticas recomendadas para a configuração do serviço Redis

- Configuração do cache Redis L2
- Habilitar conexão Redis slave
- Chaves de pré-carregamento
- Habilitar cache obsoleto
- Separar o cache Redis da sessão Redis
- Compactar o cache Redis e usar `gzip` para maior compactação

## Configuração do cache Redis L2

Configure o cache L2 do Redis definindo a variável de implantação `REDIS_BACKEND` no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obter a configuração do ambiente na infraestrutura em nuvem, consulte o [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) no _Guia do Commerce na Infraestrutura em Nuvem_.

Para instalações locais, consulte [Configurar o cache de página do Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) no _Guia de Configuração_.

>[!NOTE]
>
>Verifique se você está usando a versão mais recente do pacote `ece-tools`. Caso contrário, [atualize para a versão mais recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Você pode verificar a versão instalada em seu ambiente local usando o comando da CLI do `composer show magento/ece-tools`.


### Dimensionamento da memória cache L2 (Adobe Commerce Cloud)

O cache L2 usa um [sistema de arquivos temporário](https://en.wikipedia.org/wiki/Tmpfs) como mecanismo de armazenamento. Comparado com sistemas de banco de dados de valores-chave especializados, um sistema de arquivos temporário não tem uma política de remoção de chaves para controlar o uso de memória.

A falta de controle do uso da memória pode fazer com que o uso da memória cache L2 cresça com o tempo, acumulando o cache obsoleto.

Para evitar o esgotamento da memória das implementações de cache L2, o Adobe Commerce limpa o armazenamento quando um determinado limite é atingido. O valor de limite padrão é 95%.

É importante ajustar o uso máximo da memória cache L2 com base nos requisitos do projeto para armazenamento em cache. Use um dos seguintes métodos para configurar o dimensionamento do cache de memória:

- Crie um tíquete de suporte para solicitar alterações de tamanho da montagem `/dev/shm`.
- Ajuste a propriedade `cleanup_percentage` no nível do aplicativo para limitar a porcentagem máxima de preenchimento do armazenamento. A memória livre restante pode ser usada por outros serviços.
Você pode ajustar a configuração na configuração de implantação no grupo de configuração de cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>A opção configurável `cleanup_percentage` foi introduzida no Adobe Commerce 2.4.4.

O código a seguir mostra um exemplo de configuração no arquivo `.magento.env.yaml`:

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

Os requisitos de cache podem variar com base na configuração do projeto e no código personalizado de terceiros. O escopo de dimensionamento da memória cache L2 permite que o cache L2 funcione sem muitas ocorrências de limite.
Idealmente, o uso da memória cache L2 deve estabilizar em um determinado nível abaixo do limite, apenas para evitar a limpeza frequente do armazenamento.

Você pode verificar o uso da memória de armazenamento em cache L2 em cada nó do cluster usando o seguinte comando da CLI e procurando a linha `/dev/shm`.
O uso pode variar em diferentes nós, mas deve convergir para o mesmo valor.

```bash
df -h
```

## Habilitar conexão Redis slave

Habilite uma conexão slave Redis no arquivo de configuração `.magento.env.yaml` para permitir que apenas um nó manipule o tráfego de leitura-gravação, enquanto os outros nós manipulam o tráfego somente leitura.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Consulte [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) no _Guia do Commerce na Infraestrutura de Nuvem_.

Para instalações locais do Adobe Commerce, configure a nova implementação do cache Redis usando os comandos `bin/magento:setup`. Consulte [Usar Redis para cache padrão](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) no _Guia de Configuração_.

>[!WARNING]
>
>_não_ configure uma conexão slave Redis para projetos de infraestrutura em nuvem com uma [arquitetura dimensionada/dividida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Isso causa erros de conexão Redis. Consulte a [orientação sobre a configuração do Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) no guia do _Commerce na Infraestrutura na Nuvem_.

## Chaves de pré-carregamento

Para reutilizar dados entre páginas, liste as chaves para pré-carregamento no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para instalações locais, consulte o [recurso de pré-carregamento Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) no _Guia de Configuração_.

## Habilitar cache obsoleto

Reduza os tempos de espera de bloqueio e melhore o desempenho — especialmente ao lidar com vários blocos e chaves de cache — usando um cache desatualizado e gerando um novo cache em paralelo. Habilite o cache obsoleto e defina tipos de cache no arquivo de configuração `.magento.env.yaml`:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

Para configurar instalações locais, consulte [Opções de cache obsoletas](../../../configuration/cache/level-two-cache.md#stale-cache-options) no _Guia de Configuração_.

## Instâncias separadas do cache Redis e da sessão

A separação do cache Redis da sessão Redis permite gerenciar o cache e as sessões independentemente. Isso evita que problemas de cache afetem as sessões, o que pode afetar a receita. Cada instância do Redis é executada em seu próprio núcleo, o que melhora o desempenho.

1. Atualize o arquivo de configuração `.magento/services.yaml`.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
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

1. Envie um [tíquete de Suporte Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para solicitar o provisionamento de uma nova instância Redis dedicada às sessões nos ambientes de Produção e Preparo. Inclua os arquivos de configuração `.magento/services.yaml` e `.magento.app.yaml` atualizados. Isso não causará tempo de inatividade, mas requer uma implantação para ativar o novo serviço.

1. Verifique se a nova instância está em execução e anote o número da porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Adicione o número da porta ao arquivo de configuração `.magento.env.yaml`.

   >[!NOTE]
   >`disable_locking` deve ser definido como `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Remover sessões do [banco de dados padrão](../../../configuration/cache/redis-pg-cache.md) (`db 0`) na instância de cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante a implantação, você deve ver as seguintes linhas no [log de compilação e implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Compactação de cache

Se você estiver usando mais de 6 GB de Redis `maxmemory`, poderá usar a compactação de cache para reduzir o espaço consumido pelas chaves. Esteja ciente de que há um compromisso com o desempenho do lado do cliente. Se você tiver CPUs sobressalentes, ative-as. Consulte [Usar Redis para armazenamento de sessão](../../../configuration/cache/redis-session.md) no _Guia de Configuração_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Informações adicionais

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para armazenamento de sessão](../../../configuration/cache/redis-session.md)
