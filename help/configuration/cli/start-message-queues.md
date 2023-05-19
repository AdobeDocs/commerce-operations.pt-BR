---
title: Iniciar consumidores da fila de mensagens
description: Saiba como iniciar um consumidor de fila de mensagens.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Iniciar consumidores da fila de mensagens

{{file-system-owner}}

Você deve iniciar um [consumidor de fila de mensagens](../queues/consumers.md) para habilitar operações assíncronas, como ações em massa do Inventory management e pontos de extremidade ASSÍNCRONOS e em massa REST. Para habilitar a funcionalidade B2B, você deve iniciar vários consumidores. Módulos de terceiros também podem exigir que você inicie um consumidor personalizado.

Para exibir uma lista de todos os consumidores:

```bash
bin/magento queue:consumers:list
```

Para iniciar consumidores de fila de mensagens:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Depois de consumir todas as mensagens disponíveis, o comando é encerrado. Você pode executar o comando novamente manualmente ou com um trabalho cron. Você também pode executar várias instâncias do `magento queue:consumers:start` comando para processar grandes filas de mensagens. Por exemplo, você pode anexar `&` para executar o comando em segundo plano, retorne a um prompt e continue executando os comandos:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulte [fila:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) na seção Comércio do _Referência de ferramentas de linha de comando_ para obter detalhes sobre as opções, os parâmetros e os valores do comando.

>[!INFO]
>
>A variável `--multi-process` está presente na variável `queue:consumers:start` comando, mas para executar consumidores com processos paralelos, configure o [`multiple_processes`](../queues/manage-message-queues.md#configuration) opção em `/app/etc/env.php`. Caso contrário, se `queue:consumers:start` é chamado com o `--multi-process` funciona somente em um único thread.
