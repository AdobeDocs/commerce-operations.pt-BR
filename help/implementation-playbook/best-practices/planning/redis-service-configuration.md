---
title: Práticas recomendadas para a configuração do serviço Redis
description: Saiba como melhorar o desempenho do cache usando a implementação do cache Redis estendido para Adobe Commerce.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Práticas recomendadas para a configuração do serviço Redis

- Use a implementação do cache Redis estendido, que inclui as seguintes otimizações para minimizar o número de consultas Redis executadas em cada solicitação do Adobe Commerce:
   - Diminui o tamanho das transferências de dados de rede entre Redis e Adobe Commerce
   - Diminui o consumo de Redis dos ciclos da CPU, melhorando a capacidade do adaptador de determinar automaticamente o que precisa ser carregado
   - Reduz as condições de corrida nas operações de gravação do Redis
- Separar o cache Redis da sessão Redis
- Compacte o cache Redis e use `gzip` para melhorar o desempenho

## Implementação do cache Redis estendido

Atualizar sua configuração para usar a implementação do cache Redis estendido `\Magento\Framework\Cache\Backend\Redis`.

### Configurar implantações em nuvem

Configure o cache Redis aprimorado definindo o `REDIS_BACKEND` variável de implantação no `.magento.env.yaml` arquivo de configuração.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Para obter detalhes, consulte [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) descrição da variável no _Guia do Commerce na infraestrutura em nuvem_.

>[!NOTE]
>
> Verifique a `ece-tools` versão instalada no ambiente local a partir da linha de comando usando o `composer show magento/ece-tools` comando. Se necessário, [atualizar para a versão mais recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Fazer _não_ configurar uma conexão slave Redis para projetos de infraestrutura em nuvem com um [arquitetura dimensionada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Isso causa erros de conexão Redis. Consulte [a orientação para a configuração Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) no _Commerce na infraestrutura em nuvem_ guia.

### Configurar implantações locais

Para implantações locais do Adobe Commerce, configure a nova implementação do cache Redis usando o `bin/magento:setup` comandos. Para obter instruções, consulte [Usar Redis para cache padrão](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Instâncias separadas de cache e sessão

A separação do cache Redis da sessão Redis permite gerenciar o cache e as sessões independentemente para evitar que problemas de cache afetem as sessões.

1. Atualize o `.magento/services.yaml` arquivo de configuração.

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

1. Atualize o `.magento.app.yaml` arquivo de configuração.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Enviar um [Tíquete de suporte do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para alterar a configuração do serviço Redis em ambientes de produção e preparo profissionais. Incluir os atualizados `.magento/services.yaml` e `.magento.app.yaml` arquivos de configuração.

1. Verifique se a nova instância está em execução e anote o número da porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Adicione o número da porta à `.magento.env.yaml` arquivo de configuração.

   >[!NOTE]
   >`disable_locking` deve ser definido como `1`.

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

1. Remover sessões do [banco de dados padrão](../../../configuration/cache/redis-pg-cache.md) (`db 0`) na instância do cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante a implantação, você deve ver as seguintes linhas no [criar e implantar log](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

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

Use a compactação de cache, mas esteja ciente de que há um compromisso com o desempenho do lado do cliente. Se você tiver CPUs sobressalentes, ative-as. Consulte [Usar Redis para armazenamento de sessão](../../../configuration/cache/redis-session.md).

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
