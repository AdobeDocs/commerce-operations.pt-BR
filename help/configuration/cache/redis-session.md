---
title: Use Redis para armazenamento de sessão
description: Saiba como configurar o Redis para armazenamento de sessão.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---


# Use Redis para armazenamento de sessão

>[!IMPORTANT]
>
>Você deve [instalar o Redis](config-redis.md#install-redis) antes de continuar.


O Commerce agora fornece opções de linha de comando para configurar o armazenamento de sessão Redis. Em versões anteriores, você editava o `<Commerce install dir>app/etc/env.php` arquivo. A linha de comando fornece validação e é o método de configuração recomendado, mas você ainda pode editar a variável `env.php` arquivo.

Execute o `setup:config:set` e especifique parâmetros específicos de Redis.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

em que

`--session-save=redis` habilita o armazenamento da sessão Redis. Se esse recurso já tiver sido ativado, omita esse parâmetro.

`--session-save-redis-<parameter_name>=<parameter_value>` é uma lista de pares de parâmetros/valores que configuram o armazenamento de sessão:

| Parâmetro de linha de comando | Nome do parâmetro | Significado | Valor padrão |
|--- |--- |--- |--- |
| session-save-redis-host | host | Nome do host, endereço IP ou caminho absoluto totalmente qualificado, se estiver usando soquetes UNIX. | localhost |
| session-save-redis-port | porta | Redis porta de escuta do servidor. | 6379 |
| session-save-redis-password | senha | Especifica uma senha se o servidor Redis requer autenticação. | empty |
| session-save-redis-timeout | timeout | Tempo limite da conexão, em segundos. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Sequência de caracteres exclusiva para ativar conexões persistentes (por exemplo, sess-db0).<br>[Problemas conhecidos com phpredis e php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | banco de dados | Número exclusivo do banco de dados Redis, recomendado para proteção contra perda de dados.<br><br>**Importante**: Se você usar Redis para mais de um tipo de armazenamento em cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de armazenamento em cache a 0, o número do banco de dados de armazenamento em cache de página a 1 e o número do banco de dados de armazenamento de sessão a 2. | 0 |
| session-save-redis-compression-threshold | compression_threshold | Defina como 0 para desativar a compactação (recomendado quando `suhosin.session.encrypt = On`).<br>[Problema conhecido com strings de mais de 64 KB](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | Opções: gzip, lzf, lz4 ou snappy. | gzip |
| session-save-redis-log-level | log_level | Defina como qualquer um dos seguintes, listado em ordem de menos detalhado a mais detalhado:<ul><li>0 (emergência: apenas os erros mais graves)<li>1 (alerta: ação imediata necessária)<li>2 (crítico: componente de aplicativo indisponível)<li>3 (erro: erros de tempo de execução, não críticos, mas devem ser monitorados)<li>4 (aviso: informações adicionais, recomendado)<li>5 (anúncio: estado normal, mas significativo)<li>6 (informações: mensagens informativas)<li>7 (depurar: as mais informações somente para desenvolvimento ou teste)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Número máximo de processos que podem aguardar um bloqueio em uma sessão. Para grandes clusters de produção, defina isso como pelo menos 10% do número de processos PHP. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Número de segundos para aguardar antes de tentar quebrar o bloqueio para a sessão de frontend (ou seja, vitrine). | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Número de segundos para aguardar antes de tentar quebrar o bloqueio de uma sessão de adminhtml (ou seja, Admin). | 30º |
| session-save-redis-first-lifetime | first_lifetime | Duração, em segundos, da sessão para não bots na primeira gravação ou use 0 para desativar. | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | Duração, em segundos, da sessão para bots na primeira gravação ou use 0 para desativar. | 60º |
| session-save-redis-bot-lifetime | bot_lifetime | Duração, em segundos, da sessão para bots em gravações subsequentes ou use 0 para desativar. | 7200 |
| session-save-redis-disable-locking | disable_locking | Desative totalmente o bloqueio de sessão. | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | Duração mínima da sessão, em segundos. | 60º |
| session-save-redis-max-lifetime | max_lifetime | Duração máxima da sessão, em segundos. | 2592000 (720 horas) |
| session-save-redis-sentinel-principal | sentinel_principal | Nome principal de Redis Sentinel | empty |
| session-save-redis-sentinel-servers | sentinel_servers | Lista de servidores Redis Sentinel, separados por vírgulas | empty |
| session-save-redis-sentinel-verify-principal | sentinel_verify_principal | Verificar sinalizador de status principal do Redis Sentinel | 0 (false) |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | Tentativas de conexão para sentinelas | 5 |

## Exemplo

O exemplo a seguir define Redis como armazenamento de dados da sessão, define o host como `127.0.0.1`, define o nível de log como 4 e define o número do banco de dados como 2. Todos os outros parâmetros são definidos com o valor padrão.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Resultado

O Commerce adiciona linhas semelhantes às seguintes a `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>O TTL para registros de sessão usa o valor para Vida útil do cookie, que é configurado no Administrador. Se a Vida útil do cookie estiver definida como 0 (o padrão é 3600), as sessões de Redis expirarão no número de segundos especificado em min_lifetime (o padrão é 60). Essa discrepância se deve às diferenças em como o Redis e os cookies de sessão interpretam um valor vitalício de 0. Se esse comportamento não for desejado, aumente o valor de min_lifetime.

## Verifique a conexão Redis

Para verificar se o Redis e o Commerce estão funcionando juntos, faça logon no servidor que executa o Redis, abra um terminal e use o comando Redis monitor ou o comando ping.

### comando Redis monitor

```bash
redis-cli monitor
```

Exemplo de saída de armazenamento de sessão:

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### comando ping Redis

```bash
redis-cli ping
```

`PONG` deve ser a resposta.

Se ambos os comandos tiverem êxito, o Redis será configurado corretamente.

### Como inspecionar dados compactados

Para inspecionar os dados compactados da Sessão e o Cache da Página, a variável [RESP.app](https://flathub.org/apps/details/app.resp.RESP) O suporta a descompactação automática do Cache de Sessão e Página do Commerce 2 e exibe os dados de sessão PHP em um formulário legível.

