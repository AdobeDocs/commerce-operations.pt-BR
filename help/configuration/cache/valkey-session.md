---
title: Usar Valkey para armazenamento de sessão
description: Saiba como configurar o Valkey para armazenamento de sessão.
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: bc0274074c0254f649af2f9e2b288017ac82ce9b
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---


# Usar Valkey para armazenamento de sessão

>[!IMPORTANT]
>
>Você deve [instalar a Valkey](config-valkey.md#install-valkey) antes de continuar.

O Adobe Commerce fornece opções de linha de comando para configurar o armazenamento de sessão Valkey.

Execute o comando `setup:config:set` e especifique parâmetros específicos de Valkey.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` habilita o armazenamento da sessão Valkey. Se esse recurso já estiver ativado, omita esse parâmetro.

- `--session-save-valkey-<parameter_name>=<parameter_value>` é uma lista de pares parâmetro/valor que configuram o armazenamento da sessão:

| Parâmetro de linha de comando | Nome do parâmetro | Significado | Valor padrão |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | host | Nome de host totalmente qualificado, endereço IP ou caminho absoluto, se estiver usando soquetes UNIX. | localhost |
| session-save-valkey-port | porta | Porta de escuta do servidor Valkey. | 6379 |
| session-save-valkey-password | senha | Especifica uma senha se o servidor Valkey exigir autenticação. | vazio |
| session-save-valkey-timeout | timeout | Tempo limite da conexão, em segundos. | 2,5 |
| session-save-valkey-persistent-id | persistent_identifier | Sequência de caracteres exclusiva para ativar conexões persistentes (por exemplo, sess-db0).<br>[Problemas conhecidos com phpredis e php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-valkey-db | banco de dados | Número exclusivo do banco de dados Valkey, recomendado para proteger contra perda de dados.<br><br>**Importante**: se você usar Valkey para mais de um tipo de cache, os números do banco de dados deverão ser diferentes. É recomendável atribuir o número padrão do banco de dados de cache a `0`, o número do banco de dados de cache da página a `1` e o número do banco de dados de armazenamento da sessão a `2`. | 0 |
| session-save-valkey-compression-threshold | compression_threshold | Defina como `0` para desabilitar a compactação (recomendável quando `suhosin.session.encrypt = On`). | 2048 |
| session-save-valkey-compression-lib | compression_library | Opções: gzip, lzf, lz4 ou snappy. | gzip |
| session-save-valkey-log-level | log_level | Defina como qualquer um dos itens a seguir, listados na ordem do menos detalhado ao mais detalhado:<ul><li>0 (emergência: apenas os erros mais graves)<li>1 (alerta: ação imediata necessária)<li>2 (crítico: componente do aplicativo indisponível)<li>3 (erro: erros de tempo de execução, não críticos, mas que devem ser monitorados)<li>4 (aviso: informações adicionais, recomendado)<li>5 (aviso: condição normal, mas significativa)<li>6 (informações: mensagens informativas)<li>7 (depurar: o máximo de informações somente para desenvolvimento ou teste)</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | Número máximo de processos que podem aguardar um bloqueio em uma sessão. Para grandes clusters de produção, defina como pelo menos 10% do número de processos PHP. | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | Número de segundos a aguardar antes de tentar interromper o bloqueio para uma sessão de front-end (ou seja, loja). | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | Número de segundos a aguardar antes de tentar interromper o bloqueio de uma sessão adminhtml (ou seja, Admin). | 30 |
| session-save-valkey-first-lifetime | first_lifetime | Tempo de vida, em segundos, da sessão para não bots na primeira gravação ou use `0` para desabilitar. | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | Tempo de vida, em segundos, da sessão para bots na primeira gravação ou use `0` para desabilitar. | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | Tempo de vida, em segundos, da sessão para bots em gravações subsequentes, ou use `0` para desabilitar. | 7200 |
| session-save-valkey-disable-locking | disable_locking | Desabilita completamente o bloqueio de sessão. | 0 (falso) |
| session-save-valkey-min-lifetime | min_lifetime | Tempo de vida mínimo da sessão, em segundos. | 60 |
| session-save-valkey-max-lifetime | max_lifetime | Tempo de vida máximo da sessão, em segundos. | 2592000 (720 horas) |
| session-save-valkey-sentinel-master | sentinel_master | Nome principal do Sentinel Valkey. | vazio |
| session-save-valkey-sentinel-servers | sentinel_servers | Lista de servidores Sentinel Valkey, separados por vírgulas. | vazio |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Verifique o sinalizador de status mestre do Sentinel da Valkey. | 0 (falso) |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | Tentativas de conexão para sentinelas. | 5 |

## Exemplo

O exemplo a seguir define Valkey como o armazenamento de dados da sessão, define o host como `127.0.0.1`, define o nível de log como `4` e define o número do banco de dados como `2`. Todos os outros parâmetros são definidos com o valor padrão.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### Resultado

O Commerce adiciona linhas semelhantes às seguintes a `<magento_root>app/etc/env.php`:

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>O TTL para registros de sessão usa o valor para a Vida útil do cookie, que é configurada no Administrador. Se a Vida útil do cookie estiver definida como `0` (o padrão é `3600`), as sessões Valkey expirarão no número de segundos especificado em min_lifetime (o padrão é `60`). Essa discrepância se deve às diferenças em como Valkey e os cookies de sessão interpretam um valor de tempo de vida de `0`. Se esse comportamento não for o desejado, aumente o valor de min_lifetime.

## Verificar conexão Valkey

Para verificar se o Valkey e o Commerce estão funcionando corretamente, faça logon no servidor onde o Valkey está em execução, abra um terminal e use o comando `valkey-cli monitor` ou o comando `redis-cli ping`.

### Comando do monitor Valkey

```bash
valkey-cli monitor
```

Exemplo de saída de armazenamento de sessão:

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### comando Valkey ping

```bash
valkey-cli ping
```

Resposta esperada: `PONG`.

Se ambos os comandos forem bem-sucedidos, Valkey será configurado corretamente.

### Inspeção de dados compactados

Para inspecionar os dados da sessão compactada e o cache de página, o [RESP.app](https://flathub.org/apps/app.resp.RESP) oferece suporte à descompactação automática da sessão do Commerce 2 e do cache de página e exibe os dados da sessão PHP em um formato legível.
