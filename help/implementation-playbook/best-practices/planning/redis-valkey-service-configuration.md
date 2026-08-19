---
title: Práticas recomendadas para a configuração do serviço Valkey e Redis
description: Saiba como configurar o cache Redis e Valkey para o Adobe Commerce na nuvem, incluindo conexões de réplica, cache L2, cache obsoleto e armazenamento de sessão.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce na nuvem" type="Informative" url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce na nuvem."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
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
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Práticas recomendadas para a configuração do serviço Valkey e Redis

Use essas recomendações ao configurar o Redis ou o Valkey para o cache de aplicativos do Adobe Commerce, armazenamento de sessão e cache L2 para o Adobe Commerce em implantações de nuvem.

Para obter a configuração do cache local do Adobe Commerce, consulte [Configuração do cache L2 para otimização de desempenho](/help/configuration/cache/level-two-cache.md).

>[!NOTE]
>
>Este tópico aborda o cache de aplicativo do Commerce e os backends de sessão. O armazenamento em cache HTTP de página inteira, como Fastly ou Varnish, é uma camada de armazenamento em cache separada e é configurado independentemente. As alterações no back-end do cache de aplicativos não substituem nem configuram o cache HTTP de página inteira.

Essas recomendações abrangem o seguinte:

- Selecionar um serviço de cache com suporte
- Habilitar conexão de réplica
- Instâncias separadas de cache e sessão
- Configurar compactação de cache
- Habilitar liberação assíncrona
- Habilitar E/S multithread
- Aumentar tempos limite e tentativas do cliente
- Configure o cache L2, incluindo chaves de pré-carregamento, cache obsoleto e cache L2 [!DNL Symfony]
- Revisar exemplos de configuração

## Selecionar um serviço de cache com suporte

| Versão do Adobe Commerce | Serviço de cache recomendado | Implementação de cache L2 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 e anterior, quando suportado pela versão exata | Redis ou Valkey | RemoteSynchronizedCache |
| 2.4.9 e posterior | Valkey | symfony_l2 |

O Redis não é compatível com a configuração de cache no Adobe Commerce 2.4.9 e em versões de patch em que os requisitos do sistema especificam Valkey. Sempre verifique a versão exata do Commerce, o nível de patch e a versão do serviço nas [Opções de back-end do cache e referência de armazenamento](/help/configuration/cache/cache-options.md) e [Requisitos do sistema](/help/installation/system-requirements.md).

>[!NOTE]
>
>Verifique se você está usando a versão mais recente do pacote `ece-tools`. Caso contrário, [atualize para a versão mais recente](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Você pode verificar a versão instalada em seu ambiente local usando o comando da CLI do `composer show magento/ece-tools`.

## Habilitar conexão de réplica

Habilite a conexão de réplica no arquivo `.magento.env.yaml`. Essa alteração permite que o Adobe Commerce use uma conexão de cache adicional para leituras, enquanto continua usando o endpoint principal para gravações. Essa configuração pode reduzir a carga de leitura no serviço de cache principal e distribuir o tráfego de leitura com mais eficiência.

>[!NOTE]
>
>A disponibilidade de uma conexão de réplica depende da topologia do projeto (por exemplo, nó único versus divisão ou arquitetura de alta disponibilidade) e da versão `ece-tools`. Antes de confiar nessa configuração, confirme se existe uma relação de réplica para o serviço executando o `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp` e verificando se há uma entrada `USE_SLAVE_CONNECTION`. Para confirmar se sua topologia provisiona um ponto de extremidade de réplica, atualize o `ece-tools` e reimplante ou entre em contato com o Suporte da Adobe Commerce se nenhuma entrada `USE_SLAVE_CONNECTION` estiver presente.
>
>Para `symfony_l2`, o suporte à conexão de réplica é fornecido por meio de uma atualização de `ece-tools` e Cloud Patches. Nenhuma configuração de cache adicional é necessária além da alteração de `VALKEY_USE_SLAVE_CONNECTION: true`. Atualize para a versão mais recente do `ece-tools` para receber a correção.

>[!BEGINTABS]

>[!TAB Configuração de Valkey]

Para Valkey, use:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obter detalhes sobre a configuração da variável de ambiente, consulte [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) no _Guia de Infraestrutura do Commerce na Nuvem_.

>[!TAB Configuração Redis]

Para Redis, use:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Para obter detalhes sobre a configuração da variável de ambiente, consulte [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) no _Guia de Infraestrutura do Commerce na Nuvem_.

>[!ENDTABS]

## Instâncias separadas de cache e sessão

A configuração de cache e sessão é independente. `SESSION_CONFIGURATION` não afeta o comportamento do cache, independentemente de qual back-end de cache ou implementação de cache L2 você usa. Separar o cache das sessões permite que você as gerencie independentemente. Ele reduz a contenção entre o cache e o tráfego da sessão, impede que a pressão relacionada ao cache afete as sessões e permite que cada instância Redis ou Valkey seja dimensionada e ajustada para sua própria carga de trabalho.

>[!IMPORTANT]
>
>O provisionamento de uma instância de sessão dedicada na Produção e no Armazenamento temporário não é um autoatendimento. É necessário enviar um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) com seus arquivos `.magento/services.yaml` e `.magento.app.yaml` atualizados, conforme descrito na etapa 3 abaixo.

Para provisionar uma instância dedicada para sessões, siga as etapas abaixo:

>[!BEGINTABS]

>[!TAB Chave de valor]

1. Atualize o arquivo de configuração `.magento/services.yaml`, substituindo `<version>` pelas versões de serviço que você está usando. Consulte [Requisitos do sistema](/help/installation/system-requirements.md) para obter as versões do serviço com suporte por versão.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Inclua os arquivos de configuração `.magento/services.yaml` e `.magento.app.yaml` atualizados.

   Essa atualização não causa tempo de inatividade, mas requer uma implantação para ativar o novo serviço.

1. Verifique se a nova instância está em execução e observe o número da porta.

   ```shell
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

1. Remover sessões do [banco de dados padrão](/help/configuration/cache/redis-pg-cache.md) (`db 0`) na instância de cache Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis]

1. Atualize o arquivo de configuração `.magento/services.yaml`, substituindo `<version>` pelas versões de serviço que você está usando.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Inclua os arquivos de configuração `.magento/services.yaml` e `.magento.app.yaml` atualizados.

   Essa atualização não causa tempo de inatividade, mas requer uma implantação para ativar o novo serviço.

1. Verifique se a nova instância está em execução e observe o número da porta.

   ```shell
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

1. Remover sessões do [banco de dados padrão](/help/configuration/cache/redis-pg-cache.md) (`db 0`) na instância de cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compactação de cache

Se você usar mais de 6 GB de Redis ou Valkey `maxmemory`, poderá habilitar a compactação de cache para reduzir o espaço consumido pelas chaves. Observe que essa configuração troca o desempenho do lado do cliente pela economia de memória. Se você tiver capacidade extra do CPU, considere ativá-la. Consulte [Usar Redis para armazenamento de sessão](/help/configuration/cache/redis-session.md) ou [Usar Valkey para armazenamento de sessão](/help/configuration/cache/valkey-session.md) no _Guia de Configuração_.

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

Para habilitar `lazyfree` na infraestrutura em nuvem da Adobe Commerce, envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) solicitando que a seguinte configuração Redis ou Valkey seja aplicada aos seus ambientes:

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

Para habilitar a thread de E/S do Redis na infraestrutura em nuvem da Adobe Commerce, envie um [tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) solicitando a configuração da thread de E/S abaixo. Essa configuração pode melhorar o throughput descarregando leituras, gravações e análise de comandos do thread principal, ao custo de um maior uso do CPU. Valide o sob o carregamento e monitore seus hosts.

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

## Configurar cache L2

Configure o cache L2 definindo a variável de implantação `VALKEY_BACKEND` ou `REDIS_BACKEND` no arquivo de configuração `.magento.env.yaml`.

Há duas implementações de cache L2 disponíveis para o Adobe Commerce na infraestrutura em nuvem.

- A implementação herdada usa `RemoteSynchronizedCache` com `Cm_Cache_Backend_File` para armazenamento local
- A implementação moderna usa o `symfony_l2` com conformidade com PSR-6 e desempenho aprimorado. A implementação moderna é compatível somente com o Valkey.

| Versão do Commerce | RemoteSynchronizedCache com Valkey | Configuração recomendada |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 e anterior<br> (se houver suporte para Valkey) | Caminho L2 herdado compatível | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 e posterior | Não suportado | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>O cache Redis não é suportado para o Adobe Commerce 2.4.9 ou para versões de patch posteriores a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 e 2.4.8-p4. Use Valkey para configuração de cache, onde Redis não é suportado. Consulte [Requisitos do sistema](/help/installation/system-requirements.md) para obter os serviços de cache com suporte por versão.

>[!BEGINTABS]

>[!TAB Configuração de Valkey]

No Commerce 2.4.8 e em versões anteriores que sejam compatíveis com o Valkey, use esta configuração:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

No Commerce 2.4.9 e posterior, use a seguinte configuração com a implementação L2 [!DNL Symfony]:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Configuração Redis]

Na versão 2.4.8 e versões anteriores do Commerce que oferecem suporte ao Redis, use:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obter detalhes sobre a configuração do ambiente, consulte [`REDIS_BACKEND`](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) no _Guia de Infraestrutura do Commerce on Cloud_.

>[!ENDTABS]

### Migrar para Valkey com cache L2 [!DNL Symfony]

Se você estiver migrando um projeto existente do Adobe Commerce na Nuvem de `RemoteSynchronizedCache` (Redis ou Valkey) para `symfony_l2`, revise o seguinte antes de atualizar `.magento.env.yaml`.

- **Alterar a variável de implantação é suficiente para habilitar `symfony_l2`.** A definição de `VALKEY_BACKEND: symfony_l2` sozinho cria a configuração completa do cache L2 automaticamente. Não é necessário recriar manualmente a estrutura `backend_options` usada pela configuração `RemoteSynchronizedCache` anterior. Consulte [Configurar [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

- **Remover `preload_keys` da sua configuração existente.** Se a configuração do `RemoteSynchronizedCache` incluir `preload_keys` em `CACHE_CONFIGURATION`, remova-a como parte da migração. Consulte [Chaves de pré-carregamento](#preload-keys) para obter detalhes.

- **O comportamento do cache obsoleto muda automaticamente.** Em `symfony_l2`, o `ece-tools` habilita automaticamente o cache obsoleto para tipos de cache comuns (como `layout`, `block_html`, `full_page` e `translate`) sem exigir a configuração de front-end manual necessária para o `RemoteSynchronizedCache`. Se você configurou o cache obsoleto manualmente e deseja manter o comportamento anterior exato, revise [Habilitar cache obsoleto](#enable-stale-cache) antes de migrar.

- **A compactação requer um sinalizador explícito.** Se você personalizar a compactação de `symfony_l2` até `CACHE_CONFIGURATION`, configurar apenas `compression_lib` não habilitará a compactação — `compress_data` também deve ser definido. Consulte [Compactação de cache](#cache-compression).

- **Redis não é um back-end remoto com suporte para `symfony_l2`.** Migrar para o Valkey como parte dessa alteração. Consulte [Configurar o serviço Valkey](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/valkey).

- **A configuração da sessão não é afetada por esta migração.** `SESSION_CONFIGURATION` é independente do back-end do cache e não precisa ser alterado ao mudar para `symfony_l2`. Consulte [Instâncias separadas de cache e sessão](#separate-cache-and-session-instances).

>[!IMPORTANT]
>
>Não configure o `symfony_l2` manualmente no `app/etc/env.php`. Configure-a por meio de `.magento.env.yaml` para que `ece-tools` aplique e mantenha a configuração durante a implantação. Consulte [Configurar [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

### Pré-carregar chaves

As chaves de pré-carregamento podem ser aplicadas a uma configuração `symfony_l2` se você usar o posicionamento correto (em `backend_options` ou `remote_backend_options`). No entanto, a Adobe não recomenda usar chaves de pré-carregamento com `symfony_l2`. A implementação de pré-carregamento `symfony_l2` busca chaves uma de cada vez, de modo que não reduz viagens de ida e volta da mesma forma que faz para `RemoteSynchronizedCache`, e pode aumentar a carga no Valkey sem um benefício de desempenho.

O recurso de pré-carregamento permite fornecer uma lista de chaves usadas com frequência que o Magento busca em um único pipeline no primeiro acesso durante uma solicitação. O Magento então mantém os valores obtidos na memória PHP para o resto dessa solicitação, o que reduz viagens de ida e volta repetidas para Redis ou Valkey e pode melhorar o desempenho de inicialização da solicitação para essas chaves.

Você pode identificar chaves usadas com frequência monitorando comandos ativos em Redis ou Valkey:

As chaves de pré-carregamento estão configuradas no arquivo de configuração `.magento.env.yaml`. Este exemplo mostra a configuração do Adobe Commerce 2.4.8 e versões anteriores que oferecem suporte a `RemoteSynchronizedCache`.

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

Após 10 segundos, pressione **Ctrl+C**. Em seguida, execute o seguinte comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este log lista as chaves que você pode pré-carregar. Para ver o conteúdo de uma chave, execute o seguinte comando:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### Habilitar cache obsoleto

O cache obsoleto é um recurso de cache L2 que permite ao Adobe Commerce fornecer um valor de cache local existente de `/dev/shm` enquanto outra solicitação já está regenerando a mesma entrada. Isso impede que solicitações simultâneas aguardem. Isso reduz os carimbos do cache e a contenção de bloqueio durante a regeneração de entradas de cache caras.

Para o Adobe Commerce 2.4.9 e posterior, defina `VALKEY_BACKEND: symfony_l2` no arquivo `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

O `ece-tools` gera automaticamente um front-end `default` e um front-end `stale_cache_enabled` e mapeia os seguintes tipos de cache para o front-end habilitado para obsoletos: `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` e `translate`. Nenhuma configuração manual `use_stale_cache` ou de front-end é necessária para esses tipos. Esse mapeamento automático é um exemplo de habilitação seletiva de cache obsoleto. Somente tipos de cache específicos usam o front-end habilitado para obsoletos, não todos eles. Para personalizar quais tipos são mapeados para `stale_cache_enabled`, ou para adicionar tipos além dos padrões, consulte [Personalizar a [!DNL Symfony] configuração do cache L2](#customize-the-symfony-l2-cache-configuration).

>[!NOTE]
>
>O tipo de cache `full_page` não é relevante para projetos de infraestrutura do Adobe Commerce na nuvem porque eles usam o Fastly para armazenamento em cache de página inteira. Os exemplos de configuração manual nesta seção omitem `full_page` por esse motivo, mesmo que `ece-tools` o inclua no mapeamento `symfony_l2` padrão.

A configuração herdada a seguir se aplica ao Adobe Commerce 2.4.8 e versões anteriores, que usam `RemoteSynchronizedCache` e exigem cache obsoleto manual e configuração de front-end. A mesma recomendação seletiva sobre global se aplica aqui.

#### Como funciona o back-end herdado do RemoteSynchronizedCache

Com `RemoteSynchronizedCache`, o Magento mantém duas cópias de cada entrada de cache: uma cópia local em `/dev/shm` e uma cópia remota em Redis ou Valkey. Quando a cópia remota não está disponível e já existe um bloqueio de regeneração para essa chave, as solicitações simultâneas podem receber o valor local anterior em vez de aguardar até que o valor novo seja gravado.

Para habilitar o cache obsoleto para a versão 2.4.8 e versões anteriores, configure-o no arquivo `.magento.env.yaml`.

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

>[!WARNING]
>
>A configuração acima habilita o cache obsoleto no front-end do cache `default`, o que aplica o comportamento de cache obsoleto a todas as entradas de cache que usam esse front-end. Os principais tipos de cache do Magento funcionam conforme esperado com essa configuração. No entanto, se o seu projeto incluir código personalizado ou extensões que gravam no cache por meio da API `\Magento\Framework\App\Cache` genérica (por exemplo, `$this->cache->save()`) sem um front-end de cache dedicado, essas entradas também poderão servir valores obsoletos durante a regeneração.
>
>
>Se isso resultar em um comportamento inesperado em suas personalizações, deixe o cache obsoleto desabilitado no front-end do `default` e habilite-o somente para os tipos de cache selecionados, conforme mostrado abaixo.

#### Habilitar cache obsoleto por tipo de cache individualmente (herdado)

Você pode habilitar o cache obsoleto apenas para os tipos de cache selecionados definindo um front-end de cache dedicado no `.magento.env.yaml` e mapeando os tipos de cache selecionados para ele. Essa abordagem manual se aplica ao back-end herdado `RemoteSynchronizedCache`; o `symfony_l2` executa esse mapeamento automaticamente, conforme descrito acima.

Para funcionar corretamente, o front-end personalizado deve ser definido como um front-end completo em `CACHE_CONFIGURATION.frontend`. Definir apenas `use_stale_cache: true` para um novo nome de front-end não é suficiente.

**Exemplo de configurações**

Para Redis nas versões 2.4.8 e anteriores, a seguinte configuração habilita o cache obsoleto para os tipos de cache `layout`, `reflection`, `config_integration`, `config_integration_api` e `translate`, enquanto deixa outros que usam o front-end padrão com cache obsoleto desabilitado:

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

>[!NOTE]
>
>Se o front-end de origem estiver configurado com opções de back-end adicionais, copie essas opções para `stale_cache_enabled` para que o novo front-end mantenha o mesmo comportamento.

### Configurar cache L2 do [!DNL Symfony]

O Adobe Commerce 2.4.9 e versões posteriores oferecem suporte ao back-end do cache `symfony_l2`. O back-end do `symfony_l2` é a implementação de cache que o Adobe Commerce usa para gerenciar o comportamento dos caches L1 e L2. **Ele não substitui Redis ou Valkey como o serviço de cache remoto.**

>[!IMPORTANT]
>
>Configure `symfony_l2` por meio da variável de implantação `.magento.env.yaml` para que `ece-tools` aplique e mantenha a configuração durante a implantação. Não configure `symfony_l2` manualmente em `app/etc/env.php`, pois a implantação pode substituir as alterações manuais de `env.php`. Se `ece-tools` não aplicar `symfony_l2`, o Commerce poderá recorrer ao cache baseado em arquivos, o que pode aumentar a E/S de disco, adicionar sobrecarga de replicação do sistema de arquivos em ambientes de vários nós e reduzir o desempenho.

Para usar o cache do `symfony_l2` para o Adobe Commerce 2.4.9, siga estas etapas:

- Verifique se o projeto de nuvem está usando o pacote [`ece-tools` v2002.2.12](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) ou posterior.

- Definir a variável de implantação no arquivo `.magento.env.yaml`: `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

Definir a variável de implantação `VALKEY_BACKEND` como `symfony_l2` cria automaticamente a configuração completa do cache L2 com base nos detalhes de conexão do serviço Valkey, incluindo os front-ends `default` e `stale_cache_enabled`, com tipos comuns de cache já mapeados. A definição de `CACHE_CONFIGURATION` é opcional e necessária somente se você quiser personalizar opções específicas de back-end.

>[!NOTE]
>
>Patch ACP2E-5132 para Adobe Commerce 2.4.9 melhora o desempenho e a confiabilidade do cache L2 [!DNL Symfony] otimizando o armazenamento de tags, adicionando um bloqueio de regeneração de cache obsoleto e corrigindo problemas com associações de tags obsoletas, gravações remotas redundantes e remoção baseada em tamanho L1 (`cleanup_percentage`). Isso reduz a carga de I/O de disco e de back-end, além de melhorar a consistência do cache. Consulte [Desempenho e confiabilidade aprimorados do cache Symfony L2](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability) no _Guia de Configuração do Adobe Commerce_.
>
>O patch está incluído no [pacote de Patches da Nuvem para o Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches) (uma dependência de `ece-tools`) e é aplicado automaticamente durante a implantação quando você atualiza para a versão mais recente do `ece-tools`. Atualize para a versão mais recente do `ece-tools` para receber o patch.

#### Personalizar a configuração do cache L2 [!DNL Symfony]

`ece-tools` deriva automaticamente os detalhes de conexão Valkey (`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`) para os front-ends `default` e `stale_cache_enabled`. Para personalizar outras opções de back-end, como o diretório de cache local, defina `CACHE_CONFIGURATION` com `_merge: true` junto com `VALKEY_BACKEND: symfony_l2`. Os valores definidos aqui substituem os padrões correspondentes gerados automaticamente; todas as opções omitidas continuam a usar os valores que `ece-tools` deriva automaticamente.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>Ao definir `CACHE_CONFIGURATION` para `symfony_l2`, substitua `server` ou `port` somente se estiver apontando intencionalmente para um ponto de extremidade de cache diferente do serviço Valkey do seu projeto. O pacote `ece-tools` deriva esses valores automaticamente de sua relação de serviço Valkey.
>
>Se você substituir `server`, seu valor deverá ser `localhost` ao conectar-se ao serviço Valkey do projeto. Fornecer um valor incorreto de `server` ou `port` faz com que a implantação falhe com um erro de conexão de cache.

### Dimensionamento da memória cache L2 para a Adobe Commerce Cloud

O cache L2 usa um [sistema de arquivos temporário](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) como seu mecanismo de armazenamento. Diferentemente dos armazenamentos de valores-chave especializados, o tmpfs não tem uma política de remoção de chaves, portanto o uso da memória pode crescer sem limites. Para evitar a exaustão, o Adobe Commerce limpa automaticamente o armazenamento L2 quando o uso atinge um limite configurável (95% por padrão). Você pode controlar o consumo de memória solicitando uma montagem `/dev/shm` maior ou reduzindo o limite de limpeza.

Ajuste o uso máximo da memória cache L2 com base nos requisitos do seu projeto. Use um dos seguintes métodos:

- Para ajustar o tamanho de montagem `/dev/shm`, crie um tíquete de suporte. Para este cenário, a Adobe recomenda definir o tamanho de montagem do `/dev/shm` para 15 GB.
- Ajuste a propriedade `cleanup_percentage` no nível do aplicativo para limitar o uso do armazenamento e liberar memória disponível para outros serviços.
Você pode ajustar a configuração na configuração de implantação no grupo de configuração de cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>A opção configurável `cleanup_percentage` foi introduzida no Adobe Commerce 2.4.4.

Os seguintes exemplos mostram o código de configuração no arquivo `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configuração de Valkey]

Para o Commerce 2.4.9 e posterior, use a seguinte configuração para definir o limite de limpeza como 90%:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configuração Redis]

Para o Commerce 2.4.8 e versões anteriores, use a seguinte configuração para definir o limite de limpeza como 90%:

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

>[!ENDTABS]

Os requisitos de cache variam de acordo com a configuração do seu projeto e o código personalizado de terceiros. Dimensione a memória cache L2 para que o cache possa operar sem ocorrências frequentes de limite.

Idealmente, o uso da memória cache L2 estabiliza abaixo do limite para evitar a limpeza frequente do armazenamento.

Você pode verificar o uso da memória de armazenamento em cache L2 em cada nó do cluster executando o seguinte comando da CLI e revisando a linha `/dev/shm`.

```shell
df -h /dev/shm
```

O uso varia entre os nós, mas converge para um valor semelhante.

## Exemplos de configuração

Use os exemplos a seguir como ponto de partida para as configurações do serviço Redis ou Valkey.


### Aplicar todas as recomendações de práticas recomendadas

>[!BEGINTABS]

>[!TAB Exemplo de configuração de Valkey]

Para `VALKEY_BACKEND: symfony_l2`, deixe `ece-tools` gerar os front-ends `default` e `stale_cache_enabled` e seus mapeamentos do tipo cache. Não defina `use_stale_cache` no front-end `default` amplo. O bloco `CACHE_CONFIGURATION` abaixo contém somente substituições de opção de back-end explícitas.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB Exemplo de configuração Redis]

Use a seguinte configuração para o Redis no Adobe Commerce 2.4.8 e versões anteriores:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!ENDTABS]

### Separar cache obsoleto por tipo de cache

>[!BEGINTABS]

>[!TAB Chave de valor]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
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

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [Configurar o serviço Valkey](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Configurar o serviço Redis](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [Implantar variáveis](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
