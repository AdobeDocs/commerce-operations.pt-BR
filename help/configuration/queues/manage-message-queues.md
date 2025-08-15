---
title: Gerenciar filas de mensagens
description: Saiba como gerenciar filas de mensagens na linha de comando do Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Gerenciar filas de mensagens

Você pode gerenciar filas de mensagens a partir da linha de comando usando tarefas cron ou um gerenciador de processo externo para garantir que os consumidores estejam recuperando mensagens.

## Gerenciamento de processos

Os trabalhos do Cron são o mecanismo padrão para reiniciar os consumidores. Processos iniciados por `cron` consomem o número especificado de mensagens e terminam. Executar novamente `cron` reinicia o consumidor.

O exemplo a seguir mostra a configuração `crontab` para consumidores em execução:

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
>A frequência com que você verifica as filas de mensagens pode depender da lógica de negócios e dos recursos de sistema disponíveis. Em geral, você pode verificar se há novos clientes e enviar emails de boas-vindas com mais frequência do que um processo que consome mais recursos, como a atualização do catálogo. Você deve definir `cron` agendamentos de acordo com suas necessidades comerciais.
>
>Ele pode ser configurado nas Admin Stores > Settings > Configuration > Advanced > System > Cron configuration options for group: consumer.
>
>Consulte [Configurar e executar o cron](../cli/configure-cron-jobs.md) para obter mais informações sobre como usar o `cron` com o Commerce.

Você também pode usar um gerenciador de processos, como o [Supervisor](https://supervisord.readthedocs.io/en/latest/), para monitorar o status dos processos. O gerenciador pode usar a linha de comando para reiniciar os processos conforme necessário.

## Configuração

### Comportamento por padrão

- Trabalho Cron `consumers_runner` habilitado
- O trabalho Cron `consumers_runner` executa todos os consumidores definidos
- Cada consumidor processa 10.000 mensagens e depois finaliza

>[!INFO]
>
>Se sua loja da Adobe Commerce estiver hospedada na plataforma Cloud, use o [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) para configurar o trabalho cron do `consumers_runner`.

### Configuração específica

Edite o arquivo `/app/etc/env.php` para configurar o trabalho cron `consumers_runner`.

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

- `cron_run` - Um valor booleano que habilita ou desabilita o trabalho cron `consumers_runner` (padrão = `true`).
- `max_messages` - O número máximo de mensagens que cada consumidor deve processar antes de terminar (padrão = `10000`). Embora não o recomendemos, você pode usar 0 para impedir que o consumidor seja encerrado. Consulte [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) para configurar como os consumidores processam mensagens da fila de mensagens.
- `consumers` - Uma matriz de cadeias de caracteres especificando quais consumidores executar. Uma matriz vazia executa *todos* consumidores.
- `multiple_processes` - Uma matriz de pares de valores chave especificando qual consumidor executar em quantos processos. Compatível com o Commerce 2.4.4 ou superior.

  >[!INFO]
  >
  >Não é recomendável executar vários consumidores em uma fila operada pelo MySQL. Consulte [Alterar fila de mensagens do MySQL para AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) para obter mais informações.

  >[!INFO]
  >
  >Se o armazenamento do Adobe Commerce estiver hospedado na plataforma de nuvem, use o [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) para configurar como os consumidores processam mensagens da fila de mensagens.

Consulte [Iniciar consumidores da fila de mensagens](../cli/start-message-queues.md).
