---
title: Iniciar consumidores da fila de mensagens
description: Saiba como iniciar um consumidor de fila de mensagens.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Iniciar consumidores da fila de mensagens

{{file-system-owner}}

Você deve iniciar um [consumidor da fila de mensagens](../queues/consumers.md) para habilitar operações assíncronas, como ações em massa do Inventory management e pontos de extremidade ASSÍNCRONOS e em massa REST. Para habilitar a funcionalidade B2B, você deve iniciar vários consumidores. Módulos de terceiros também podem exigir que você inicie um consumidor personalizado.

Para exibir uma lista de todos os consumidores:

```bash
bin/magento queue:consumers:list
```

Para iniciar consumidores de fila de mensagens:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Depois de consumir todas as mensagens disponíveis, o comando é encerrado. Você pode executar o comando novamente manualmente ou com um trabalho cron. Você também pode executar várias instâncias do comando `magento queue:consumers:start` para processar grandes filas de mensagens. Por exemplo, você pode anexar `&` ao comando para executá-lo em segundo plano, retornar a um prompt e continuar a executar comandos:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulte [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) na seção Commerce da _Referência de ferramentas de linha de comando_ para obter detalhes sobre opções, parâmetros e valores de comandos.

>[!INFO]
>
>A opção `--multi-process` está presente no comando `queue:consumers:start`, mas, para executar consumidores com processos paralelos, configure a opção [`multiple_processes`](../queues/manage-message-queues.md#configuration) em `/app/etc/env.php`. Caso contrário, se `queue:consumers:start` for chamado com a opção `--multi-process`, ele só funcionará em um único thread.
