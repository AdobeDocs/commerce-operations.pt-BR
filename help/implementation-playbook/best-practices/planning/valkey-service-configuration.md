---
title: Práticas recomendadas para a configuração do serviço Valkey
description: Saiba como melhorar o desempenho do cache usando a implementação de cache estendida do Valkey para o Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 1ab977bf2b30c2851609f0bfcc636978e974f07a
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Práticas recomendadas para a configuração do serviço Valkey

A Adobe recomenda as seguintes práticas recomendadas ao configurar o serviço Valkey:

## Configurar o cache L2 do Valkey

Configure o cache L2 Valkey definindo a variável de implantação `VALKEY_BACKEND` no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obter a configuração do ambiente na infraestrutura em nuvem, consulte o [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) no _Guia do Commerce na Infraestrutura em Nuvem_.

Para instalações locais, consulte [Configurar o cache da página Valkey](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) no _Guia de Configuração_.

>[!NOTE]
>
>Verifique se você está usando a versão mais recente do pacote `ece-tools`. Caso contrário, [atualize para a versão mais recente](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Você pode verificar a versão instalada em seu ambiente local usando o comando da CLI do `composer show magento/ece-tools`.

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
>A opção de configuração `cleanup_percentage` foi introduzida no Adobe Commerce 2.4.4.

O exemplo a seguir mostra um `CACHE_CONFIGURATION` no arquivo `.magento.env.yaml`:

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

Os requisitos de cache podem variar com base na configuração do projeto e no código personalizado de terceiros. O escopo de dimensionamento da memória cache L2 permite que o cache L2 funcione sem ocorrências desnecessárias de limite.
Idealmente, o uso da memória cache L2 deve se estabilizar em um determinado nível abaixo do limite, para evitar a limpeza frequente do armazenamento.

Você pode verificar o uso da memória de armazenamento em cache L2 em cada nó do cluster usando o seguinte comando da CLI e procurando a linha `/dev/shm`.
O uso pode variar em diferentes nós, mas deve convergir para o mesmo valor.

```bash
df -h
```

## Habilitar conexão subordinada do Valkey

Habilite uma conexão do escravo Valkey no arquivo de configuração `.magento.env.yaml` para permitir que apenas um nó manipule o tráfego de leitura-gravação, enquanto os outros nós manipulam o tráfego somente leitura.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obter mais detalhes, consulte [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) no _Guia de Infraestrutura do Commerce na Nuvem_.

Para instalações locais do Adobe Commerce, configure a nova implementação do cache Valkey usando os comandos `bin/magento:setup`. Para obter mais informações, consulte [Usar Valkey para cache padrão](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) no _Guia de Configuração_.

>[!WARNING]
>
>_não_ configure uma conexão slave Valkey para projetos de infraestrutura em nuvem com uma [arquitetura dimensionada/dividida](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Isso causa erros de conexão do Valkey. Para obter mais informações, consulte a [Orientação para configuração da Valkey](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) no guia do _Commerce na Infraestrutura de Nuvem_.

## Chaves de pré-carregamento

Para reutilizar dados entre páginas, liste as chaves para pré-carregamento no arquivo de configuração `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Para instalações locais, consulte [Recurso de pré-carregamento de Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) no _Guia de Configuração_.

## Habilitar cache obsoleto

Reduza os tempos de espera de bloqueio e melhore o desempenho, especialmente ao lidar com vários blocos e chaves de cache, usando um cache desatualizado e gerando um novo cache em paralelo. Habilite o cache obsoleto e defina tipos de cache no arquivo de configuração `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

>[!NOTE]
>
>No exemplo anterior, o cache `full_page` não é relevante para o Adobe Commerce em projetos de infraestrutura em nuvem, pois eles usam [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly).

Para configurar instalações locais, consulte [Opções de cache obsoletas](../../../configuration/cache/level-two-cache.md#stale-cache-options) no _Guia de Configuração_.

Durante a implantação, você deve ver as seguintes linhas no [log de compilação e implantação](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Compactação de cache

Se estiver usando mais de 6 GB de Valkey `maxmemory`, você poderá usar a compactação de cache para reduzir o espaço consumido pelas chaves. Esteja ciente de que há um compromisso com o desempenho do lado do cliente. Se você tiver CPUs sobressalentes, a Adobe sugere ativá-las. Consulte [Usar Valkey para armazenamento de sessão](../../../configuration/cache/valkey-session.md) no _Guia de Configuração_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
