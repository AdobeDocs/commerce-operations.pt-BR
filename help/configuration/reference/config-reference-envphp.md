---
title: referência env.php
description: Consulte uma lista de valores para o arquivo env.php.
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# referência env.php

O `env.php` O arquivo contém as seguintes seções:

| Nome | Descrição |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Configurações da área de Administração |
| `cache` | Configurar página de redirecionamento e cache padrão |
| `cache_types` | Configurações de armazenamento de cache |
| `consumers_wait_for_messages` | Configurar como os consumidores processam mensagens da fila de mensagens |
| `cron` | Ative ou desative as tarefas do cron |
| `crypt` | A chave de criptografia para funções criptográficas |
| `db` | Configurações de conexão de banco de dados |
| `default_connection` | Conexão padrão das filas de mensagens |
| `directories` | Configurações de mapeamento de diretórios de comércio |
| `downloadable_domains` | Lista de domínios baixáveis |
| `install` | A data de instalação |
| `lock` | Bloquear configurações do provedor |
| `MAGE_MODE` | O [modo de aplicativo](../bootstrap/application-modes.md) |
| `queue` | [Filas de mensagens](../queues/manage-message-queues.md) configurações |
| `resource` | Mapeamento do nome do recurso para uma conexão |
| `session` | Dados de armazenamento da sessão |
| `system` | Desativa o campo para edição no administrador |
| `x-frame-options` | Configuração de [x-frame-options][x-frame-options] |

## backend

Configure o **frontName** para o url de administração do Commerce usando o `backend` nó em env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configure a página de revisão e o armazenamento em cache padrão usando `cache` no nó `env.php` arquivo.

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

Saiba mais em [Configuração de Redis](../cache/redis-pg-cache.md).

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

Saiba mais sobre diferentes [Tipos de cache](../cli/manage-cache.md).

## consumer_wait_for_messages

Especifique se os consumidores devem continuar a pesquisa de mensagens se o número de mensagens processadas for menor que a variável `max_messages` valor. O valor padrão é `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

As seguintes opções estão disponíveis:

- `1`—Os consumidores continuam a processar mensagens da fila de mensagens até atingirem o `max_messages` valor especificado na variável `env.php` antes de fechar a conexão TCP e encerrar o processo do consumidor. Se a fila ficar vazia antes de chegar à `max_messages` , o consumidor aguarda mais mensagens para chegar.

   Recomendamos essa configuração para grandes comerciantes, pois um fluxo de mensagem constante é esperado e os atrasos no processamento não são desejados.

- `0`—Consumidores processam mensagens disponíveis na fila, fecham a conexão TCP e encerram. Os consumidores não esperam mensagens adicionais para entrar na fila, mesmo se o número de mensagens processadas for menor que o `max_messages` valor especificado na variável `env.php` arquivo. Isso pode ajudar a evitar problemas com trabalhos cron causados por longos atrasos no processamento da fila de mensagens.

   Recomendamos essa configuração para comerciantes menores que não esperam um fluxo de mensagens constante e preferem conservar recursos de computação em troca de atrasos menores de processamento quando não houver mensagens por dias.

## cron

Ative ou desative trabalhos do cron para o aplicativo Commerce. Por padrão, as tarefas cron são ativadas. Para desativá-los, adicione o `cron` para a `env.php` e defina o valor como `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Tenha cuidado ao desativar trabalhos do cron. Quando estiverem desativados, os processos essenciais exigidos pelo aplicativo Commerce não serão executados.

Saiba mais sobre [Crons](../cli/configure-cron-jobs.md).

## criptografia

O Commerce usa uma chave de criptografia para proteger senhas e outros dados confidenciais. Essa chave é gerada durante o processo de instalação.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Saiba mais sobre [Chave de criptografia](https://docs.magento.com/user-guide/system/encryption-key.html) no _Guia do usuário do Commerce_.

## db

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

Define a conexão padrão para filas de mensagens. O valor pode ser `db`, `amqp`ou um sistema de fila personalizado como `redismq`. Se você especificar qualquer valor diferente de `db`, o software da fila de mensagens deve ser instalado e configurado primeiro. Caso contrário, as mensagens não serão processadas corretamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

If `queue/default_connection` é especificado no sistema `env.php` , essa conexão é usada para todas as filas de mensagens pelo sistema, a menos que uma conexão específica seja definida em um `queue_topology.xml`, `queue_publisher.xml` ou `queue_consumer.xml` arquivo.
Por exemplo, se `queue/default_connection` é `amqp` em `env.php` mas um `db` conexão especificada nos arquivos XML de configuração de fila de um módulo, o módulo usará o MySQL como um mediador de mensagens.

## diretórios

Opções opcionais de mapeamento de diretório que precisam ser definidas quando o servidor da Web estiver configurado para servir o aplicativo do Commerce na `/pub` diretório para [segurança aprimorada](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## domínios_baixáveis

Uma lista de domínios baixáveis disponíveis neste nó. Domínios adicionais podem ser adicionados, removidos ou listados usando comandos CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Saiba mais sobre [Domínios Baixáveis](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## instalar

A data de instalação do aplicativo Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## bloqueio

As configurações de bloqueio do provedor são configuradas usando o `lock` nó .

Saiba mais sobre [Bloquear configuração do provedor](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

O modo de implantação pode ser configurado neste nó.

```conf
'MAGE_MODE' => 'developer'
```

Saiba mais sobre [Modos de aplicativo](../cli/set-mode.md).

## fila

As configurações de fila de mensagens estão disponíveis neste nó.

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

As configurações de recursos estão disponíveis neste nó.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## sessão

As configurações de sessão são armazenadas na variável `session` nó .

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

Usando esse nó, o Commerce bloqueia os valores de configuração no `env.php` e então desativa o campo no administrador.

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
