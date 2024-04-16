---
title: Visão geral das filas de mensagens
description: Leia sobre a estrutura da fila de mensagens e como ela funciona com o aplicativo do Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Visão geral das filas de mensagens

O Message Queue Framework (MQF) é um sistema que permite que um módulo publique mensagens em filas. Define também o [consumidores](consumers.md) que receberá as mensagens de forma assíncrona. O MQF utiliza [[!DNL RabbitMQ]](https://www.rabbitmq.com) como o agente de mensagens, que fornece uma plataforma escalável para enviar e receber mensagens. Também inclui um mecanismo para armazenar mensagens não entregues. [!DNL RabbitMQ] é baseado na especificação do protocolo AMQP 0.9.1.

O diagrama a seguir ilustra a Estrutura da fila de mensagens:

![Estrutura da fila de mensagens](../../assets/configuration/mq-framework.png)

- Um editor é um componente que envia mensagens para uma troca. Ele sabe para qual troca publicar e o formato das mensagens enviadas.

- Um Exchange recebe mensagens de editores e as envia para filas. Embora [!DNL RabbitMQ] O oferece suporte a vários tipos de trocas, o Commerce usa somente trocas de tópicos. Um tópico inclui uma chave de roteamento, que contém strings de texto separadas por pontos. O formato para um nome de tópico é `string1.string2`: por exemplo, `customer.created` ou `customer.sent.email`.

  O broker permite usar curingas ao definir regras para o encaminhamento de mensagens. Você pode usar um asterisco (`*`) para substituir _um_ sequência de caracteres ou um sinal de libra (`#`) para substituir 0 ou mais strings. Por exemplo, `customer.*` filtraria em `customer.create` e `customer.delete`, mas não `customer.sent.email`. No entanto `customer.#` filtraria em `customer.create`,  `customer.delete`, e `customer.sent.email`.

- Uma fila é um buffer que armazena mensagens.

- Um consumidor recebe mensagens. Ele sabe qual fila consumir. Ele pode mapear processadores da mensagem para uma fila específica.

Um sistema básico de fila de mensagens também pode ser configurado sem usar [!DNL RabbitMQ]. Neste sistema, um adaptador MySQL armazena mensagens no banco de dados. Três tabelas de banco de dados (`queue`, `queue_message`, e `queue_message_status`) gerenciar a carga de trabalho da fila de mensagens. Os trabalhos da Cron garantem que os consumidores possam receber mensagens. Essa solução não é muito escalável. [!DNL RabbitMQ] deve ser utilizada sempre que possível.
