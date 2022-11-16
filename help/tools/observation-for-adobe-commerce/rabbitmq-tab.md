---
title: "O [!UICONTROL [!DNL RabbitMQ]] tab"
description: Saiba mais sobre o [!UICONTROL [!DNL RabbitMQ]] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# O [!UICONTROL [!DNL RabbitMQ]] guia

O **[!UICONTROL [!DNL RabbitMQ]]** A guia tem informações focadas em [!DNL RabbitMQ] sinais.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Eventos de infraestrutura](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** quadro mostra eventos de infraestrutura que envolvem [!DNL RabbitMQ] que ocorreu ao longo do período de tempo selecionado:

* %Response [erro] para nó [rabbit@host1]: resposta http inesperada de%&#39;) como &#39;unknown_resp_node1&#39;
* &#39;%Response [erro] para nó [rabbit@host2]: resposta http inesperada de%&#39;) como &#39;unknown_resp_node2&#39;
* &#39;%Response [erro] para nó [rabbit@host3]: resposta http inesperada de%&#39;) como &#39;unknown_resp_node3&#39;
* &#39;%Response [erro] para nó [rabbit@host3]: Obtenha &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;: limite de contexto excedido%&#39;) como &#39;node3_timeout_aded&#39;
* &#39;%Response [erro] para nó [rabbit@host1]: Obtenha &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;: limite de contexto excedido%&#39;) como &#39;node1_timeout_aded&#39;
* &#39;%Response [erro] para nó [rabbit@host2]: Obtenha &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;: limite de contexto excedido%&#39;) como &#39;node2_timeout_aded&#39;
* ‘%401 Unauthorized%’) como &#39;401_unauth&#39;
* &#39;%401 Unauthorized%&#39;) como &#39;401_unauth&#39;
* %Service reiniciado: rabbitmq-server%&#39;) como &#39;rmq_service_restart&#39;
* &#39;%Response [falha] para nó [rabbit@host1]: nodedown%&#39;) como &#39;rmq_node1_down&#39;
* &#39;%Response [falha] para nó [rabbit@host2]: nodedown%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%Response [falha] para nó [rabbit@host2]: nodedown%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%Entidade modificada: exchange/bindings.destination%&#39;) como &#39;rmq_entity_modified&#39;
* &#39;%Entidade modificada: exchange/bindings.destination%&#39;) como &#39;rmq_entity_modified&#39;
* &#39;%Entidade modificada: queue/unique%&#39;) como &#39;rmq_entity_created_q_unique&#39;&#39;%Entity modified: queue/auto_delete%&#39;) como &#39;rmq_entity_q_delete&#39;
* &#39;%Entidade modificada: queue/durável%&#39;) como &#39;rmq_entity_modified_q_durável&#39;
* &#39;%Entidade modificada: version/management%&#39;) como &#39;rmq_entity_modified_ver_mgt&#39;
* &#39;%Entidade modificada: version/management%&#39;) como &#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] sinais de início/paragem do serviço](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Este quadro mostra [!DNL RabbitMQ] sinais de início/paragem do serviço que ocorreram durante o período de tempo selecionado:

* &#39;%[!DNL RabbitMQ] é solicitado a parar...%&#39;) como &#39;rabbitmq_stop&#39;
* &#39;%Iniciando [!DNL RabbitMQ]%&#39;) como &#39;rabbitmq_start&#39;

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] erros](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Este quadro mostra [!DNL RabbitMQ] erros que ocorreram durante o período de tempo selecionado:

* &#39;%exit com razão {case_cláusula,timeout} e stacktrace {rabbit_mgmt_wm_health check%&#39;} como &#39;exit_timeout&#39;
* &#39;%client fechada inesperadamente TCP connection%&#39;) como &#39;client_closed_tcp_conn&#39;
* &#39;%at undefined exit with reason shutdown in context shutdown_error%&#39;) como &#39;undef_exit&#39;
* &#39;%Tentativa de conexão de nó não permitido%&#39;) como &#39;disallowed_node&#39;
* &#39;%fechando conexão AMQP%&#39;) como &#39;rmq_err_amqp_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] status do nó](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &#39;%rabbit no nó rabbit@host1 down%&#39;) como &#39;rmq_node1_down&#39;
* &#39;%rabbit no nó rabbit@host2 down%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%rabbit no nó rabbit@host3 down%&#39;) como &#39;rmq_node3_down&#39;
* &#39;%rabbit no nó rabbit@host1 up%&#39;) como &#39;rmq_node1_up&#39;
* &#39;%rabbit no nó rabbit@host2 up%&#39;) como &#39;rmq_node2_up&#39;
* &#39;%rabbit no nó rabbit@host3 up%&#39;) como &#39;rmq_node3_up&#39;

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Status do Resumo de Alto Nível da Mensagem por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** gráfico mostra o número de mensagens publicadas pelo [!DNL RabbitMQ] fila para o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Resumo de detalhes da mensagem](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* &#39;%report.ERROR: Cron Job consumer_runner tem um erro: NOT_FOUND - sem fila%&#39;) como &#39;queue_err&#39;
* &#39;%report.ERROR: Cron Job consumer_runner tem um erro: NOT_FOUND - sem fila%&#39;) como &#39;queue_err&#39;
* &#39;%autenticado e com acesso a vhost%&#39;) como &#39;auth&#39;
* &#39;%fechando conexão AMQP%&#39;) como &#39;close_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Consumo da Fila MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** gráfico mostra o número de bytes consumidos por cada [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Mensagens publicadas por fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** gráfico mostra o número de bytes consumidos por cada [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Throughput de Mensagens Publicadas por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** gráfico mostra o número médio de mensagens publicadas por segundo em cada [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Throughput Total da Mensagem por Fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** gráfico mostra o número total médio de mensagens por segundo para cada [!DNL RabbitMQ] durante o período selecionado.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Consumidores por fila](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

O **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** gráfico mostra o número total médio de consumidores por cada [!DNL RabbitMQ] durante o período selecionado.
