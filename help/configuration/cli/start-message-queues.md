---
title: Iniciar consumidores de fila de mensagens
description: Saiba como iniciar um consumidor de fila de mensagens.
source-git-commit: 3e3dac0c75622b210cf1168639b8804003f3c538
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Iniciar consumidores de fila de mensagens

{{file-system-owner}}

Você deve iniciar um [consumidor da fila de mensagens](../queues/consumers.md) para permitir operações assíncronas, como ações em massa do Inventory management e endpoints REST em massa e assíncronos. Para habilitar a funcionalidade B2B, você deve iniciar vários consumidores. Módulos de terceiros também podem exigir que você inicie um consumidor personalizado.

Para exibir uma lista de todos os consumidores:

```bash
bin/magento queue:consumers:list
```

Para iniciar consumidores de fila de mensagens:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Depois de consumir todas as mensagens disponíveis, o comando é encerrado. Você pode executar o comando novamente manualmente ou com um trabalho cron. Você também pode executar várias instâncias do `magento queue:consumers:start` comando para processar filas de mensagens grandes. Por exemplo, você pode anexar `&` para executar o comando em segundo plano, retorne a um prompt e continue executando os comandos:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulte [fila:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) na seção Comércio da _Referência de ferramentas de linha de comando_ para obter detalhes sobre as opções, parâmetros e valores do comando.

>[!INFO]
>
>O `--multi-process` está presente no `queue:consumers:start` , mas para executar consumidores com processos paralelos, configure a variável [`multiple_processes`](../queues/manage-message-queues.md#configuration) em `/app/etc/env.php`. Caso contrário, se `queue:consumers:start` é chamado com o `--multi-process` , ele só funciona em um único thread.
