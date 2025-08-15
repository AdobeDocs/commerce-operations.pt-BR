---
title: A guia [!UICONTROL [!DNL RabbitMQ]
description: Saiba mais sobre a guia [!UICONTROL [!DNL RabbitMQ] do  [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# A guia [!UICONTROL [!DNL RabbitMQ]]

A guia **[!UICONTROL [!DNL RabbitMQ]]** tem informações que estão focadas nos sinais [!DNL RabbitMQ].

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Eventos de infraestrutura](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

O quadro **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** mostra eventos de Infraestrutura que envolvem [!DNL RabbitMQ] que ocorreram no período selecionado:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) como `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) como `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) como `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) como `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) como `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) como `node2_timeout_exceeded`
* `%401 Unauthorized%`) como `401_unauth`
* `%401 Unauthorized%`) como `401_unauth`
* `%Service restarted: rabbitmq-server%`) como `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) como `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) como `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) como `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) como `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) como `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) como `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) como `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) como `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) como `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) como `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] sinais de início/parada do serviço](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Este quadro mostra [!DNL RabbitMQ] sinais de início/parada de serviço que ocorreram durante o período selecionado:

* `%RabbitMQ is asked to stop...%`) como `rabbitmq_stop`
* `%Starting RabbitMQ%`) como `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] erros](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Este quadro mostra [!DNL RabbitMQ] erros que ocorreram durante o período selecionado:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` como `exit_timeout`
* `%client unexpectedly closed TCP connection%`) como `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) como `undef_exit`
* `%Connection attempt from disallowed node%`) como `disallowed_node`
* `%closing AMQP connection%`) como `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

Status do nó ![[!DNL RabbitMQ]](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) como `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) como `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) como `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) como `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) como `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) como `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Status do Resumo de Alto Nível da Mensagem por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** mostra o número de mensagens publicadas pela fila [!DNL RabbitMQ] para o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Resumo detalhado da mensagem](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) como `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) como `queue_err`
* `%authenticated and granted access to vhost%`) como `auth`
* `%closing AMQP connection%`) como `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] MB de Consumo da Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** mostra o número de bytes consumidos por cada fila [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Mensagens Publicadas por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** mostra o número de bytes consumidos por cada fila [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Taxa de Transferência de Mensagem Publicada por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** mostra o número médio de mensagens publicadas por segundo por cada fila [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Taxa de Transferência Total de Mensagens por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** mostra o número total médio de mensagens por segundo por cada fila [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Consumidores por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

O gráfico **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** mostra o número total médio de consumidores por cada fila [!DNL RabbitMQ] durante o período selecionado.
