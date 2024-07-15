---
title: referência env.php
description: Veja uma lista de valores para o arquivo env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# referência env.php

O arquivo `env.php` contém as seguintes seções:

| Nome | Descrição |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Configurações para a área de administração |
| `cache` | Configurar página redis e cache padrão |
| `cache_types` | Configurações de armazenamento em cache |
| `consumers_wait_for_messages` | Configurar como os consumidores processam mensagens da fila de mensagens |
| `cron` | Habilitar ou desabilitar os trabalhos cron |
| `crypt` | A chave de criptografia para funções criptográficas |
| `db` | Configurações de conexão de banco de dados |
| `default_connection` | Conexão padrão de filas de mensagens |
| `directories` | configurações de mapeamento de diretórios do Commerce |
| `downloadable_domains` | Lista de domínios baixáveis |
| `install` | A data de instalação |
| `lock` | Bloquear configurações do provedor |
| `MAGE_MODE` | O [modo de aplicativo](../bootstrap/application-modes.md) |
| `queue` | Configurações de [filas de mensagens](../queues/manage-message-queues.md) |
| `resource` | Mapeamento do nome do recurso para uma conexão |
| `session` | Dados de armazenamento da sessão |
| `system` | Desabilita o campo para edição no administrador |
| `x-frame-options` | Configuração de [x-frame-options][x-frame-options] |

## back-end

Configure o **frontName** para a url de administrador do Commerce usando o nó `backend` em env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configure a página redis e o cache padrão usando o nó `cache` no arquivo `env.php`.

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

Saiba mais em [Configuração Redis](../cache/redis-pg-cache.md).

## tipos_de_cache

Todas as configurações de tipos de cache estão disponíveis neste nó.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Saiba mais sobre os [Tipos de Cache](../cli/manage-cache.md) diferentes.

## consumer_wait_for_messages

Especifique se os consumidores devem continuar a sondar mensagens se o número de mensagens processadas for menor que o valor `max_messages`. O valor padrão é `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

As seguintes opções estão disponíveis:

- `1` — Os consumidores continuam a processar mensagens da fila de mensagens até atingir o valor `max_messages` especificado no arquivo `env.php` antes de fechar a conexão TCP e encerrar o processo do consumidor. Se a fila ficar vazia antes de atingir o valor `max_messages`, o consumidor aguardará mais mensagens chegarem.

  Recomendamos essa configuração para grandes comerciantes, pois é esperado um fluxo de mensagens constante e não são desejáveis atrasos no processamento.

- `0` — Os consumidores processam as mensagens disponíveis na fila, fecham a conexão TCP e terminam. Os consumidores não esperam que mensagens adicionais entrem na fila, mesmo se o número de mensagens processadas for menor que o valor `max_messages` especificado no arquivo `env.php`. Isso pode ajudar a evitar problemas com tarefas cron causados por longos atrasos no processamento da fila de mensagens.

  Recomendamos essa configuração para comerciantes menores que não esperam um fluxo constante de mensagens e preferem conservar recursos de computação em troca de pequenos atrasos de processamento, quando não poderia haver mensagens por dias.

## cron

Habilite ou desabilite os trabalhos cron para o aplicativo Commerce. Por padrão, os trabalhos cron são ativados. Para desabilitá-los, adicione a configuração `cron` ao arquivo `env.php` e defina o valor como `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Tenha cuidado ao desativar tarefas cron. Quando desativados, os processos essenciais exigidos pelo aplicativo do Commerce não serão executados.

Saiba mais sobre [Crons](../cli/configure-cron-jobs.md).

## criptografar

O Commerce usa uma chave de criptografia para proteger senhas e outros dados confidenciais. Essa chave é gerada durante o processo de instalação.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Saiba mais sobre [Chave de criptografia](https://docs.magento.com/user-guide/system/encryption-key.html) no _Guia do usuário do Commerce_.

## bd

Todas as configurações de banco de dados estão disponíveis neste nó.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Define a conexão padrão para filas de mensagens. O valor pode ser `db`, `amqp` ou um sistema de fila personalizado, como `redismq`. Se você especificar qualquer valor diferente de `db`, o software de fila de mensagens deve ser instalado e configurado primeiro. Caso contrário, as mensagens não serão processadas corretamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Se `queue/default_connection` estiver especificado no arquivo `env.php` do sistema, essa conexão será usada para todas as filas de mensagens pelo sistema, a menos que uma conexão específica seja definida em um arquivo `queue_topology.xml`, `queue_publisher.xml` ou `queue_consumer.xml`.
Por exemplo, se `queue/default_connection` for `amqp` em `env.php`, mas uma conexão `db` for especificada nos arquivos XML de configuração de fila de um módulo, o módulo usará MySQL como um agente de mensagens.

## diretórios

Opções opcionais de mapeamento de diretório que precisam ser definidas quando o servidor Web é configurado para atender ao aplicativo Commerce a partir do diretório `/pub` para [segurança aprimorada](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

Uma lista de domínios para download disponíveis neste nó. Domínios adicionais podem ser adicionados, removidos ou listados usando comandos CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Saiba mais sobre [Domínios baixáveis](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## instalar

A data de instalação do aplicativo Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## bloquear

As configurações do provedor de bloqueio são definidas usando o nó `lock`.

Saiba mais sobre [Configuração do Provedor de Bloqueio](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

O modo de implantação pode ser configurado neste nó.

```conf
'MAGE_MODE' => 'developer'
```

Saiba mais sobre [Modos de aplicativo](../cli/set-mode.md).

## fila

As configurações da fila de mensagens estão disponíveis neste nó.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Saiba mais sobre [Fila de Mensagens][message-queue].

## recurso

As configurações de recurso estão disponíveis neste nó.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

As configurações de sessão são armazenadas no nó `session`.

```conf
'session' => [
  'save' => 'files'
],
```

Saiba mais sobre [Sessão](../storage/sessions.md).

## x-frame-options

o cabeçalho x-frame-options pode ser configurado usando esse nó.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Saiba mais sobre [x-frame-options](../security/xframe-options.md).

## sistema

Usando este nó, o Commerce bloqueia os valores de configuração no arquivo `env.php` e desabilita o campo no administrador.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Saiba mais em [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
