---
title: Gerenciar filas de mensagens
description: Saiba como gerenciar filas de mensagens na linha de comando do Adobe Commerce.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Gerenciar filas de mensagens

Você pode gerenciar filas de mensagens da linha de comando usando tarefas cron ou um gerenciador de processos externo para garantir que os consumidores estejam recuperando mensagens.

## Gerenciamento de processos

Empregos Cron são o mecanismo padrão para reiniciar os consumidores. Processos iniciados por `cron` consumir o número especificado de mensagens e depois terminar. Executando novamente `cron` reinicia o consumidor.

O exemplo a seguir mostra o `crontab` configuração para executar consumidores:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>A frequência com que você verifica as filas de mensagens depende da lógica comercial e dos recursos disponíveis do sistema. Em geral, você pode querer verificar se há novos clientes e enviar emails de boas-vindas com mais frequência do que um processo que consome muitos recursos, como atualizar o catálogo. Você deve definir `cron` programações de acordo com suas necessidades comerciais.
>
>Ele pode ser configurado nas opções de configuração Admin Stores > Configurações > Configuração > Avançado > Sistema > Cron para o grupo: consumidores.
>
>Consulte [Configurar e executar o cron](../cli/configure-cron-jobs.md) para obter mais informações sobre como usar `cron` com Comércio.

Você também pode usar um gerenciador de processos como [Supervisor](http://supervisord.org/index.html) para monitorar o status dos processos. O gerente pode usar a linha de comando para reiniciar os processos, conforme necessário.

## Configuração

### Comportamento por padrão

- Trabalho Cron `consumers_runner` está ativado
- Trabalho Cron `consumers_runner` executa todos os consumidores definidos
- Cada consumidor processa 10000 mensagens e depois finaliza

>[!INFO]
>
>Se a loja da Adobe Commerce estiver hospedada na plataforma do Cloud, use a [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) para configurar o `consumers_runner` trabalho do cron.

### Configuração específica

Edite o `/app/etc/env.php` arquivo para configurar o trabalho do cron `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Um valor booleano que ativa ou desativa a variável `consumers_runner` trabalho cron (padrão = `true`).
- `max_messages` - O número máximo de mensagens que cada consumidor deve processar antes de terminar (padrão = `10000`). Embora não o recomendemos, você pode usar 0 para impedir que o consumidor termine. Consulte [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) para configurar como os consumidores processam mensagens da fila de mensagens.
- `consumers` - Uma matriz de strings especificando quais consumidores serão executados. Uma matriz vazia é executada *all* consumidores.
- `multiple_processes` - Uma matriz de pares de valores-chave que especifica o consumidor que deve ser executado em quantos processos.

   >[!INFO]
   >
   >Não é recomendado executar vários consumidores em uma fila operada pelo MySQL. Consulte [Alterar fila de mensagens do MySQL para AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) para obter mais informações.

   >[!INFO]
   >
   >Se a loja da Adobe Commerce estiver hospedada na plataforma do Cloud, use a [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) para configurar como os consumidores processam mensagens da fila de mensagens.

Consulte [Iniciar consumidores de fila de mensagens](../cli/start-message-queues.md).
