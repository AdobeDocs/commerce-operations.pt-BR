---
title: Visão geral das filas de mensagens
description: Leia sobre a estrutura da fila de mensagens e como ela funciona com o aplicativo do Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 6f15a24e650a7138bae6d0b40f230e6970a943b0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Visão geral das filas de mensagens

O Message Queue Framework (MQF) é um sistema que permite que um módulo publique mensagens em filas. Também define os [consumidores](consumers.md) que receberão as mensagens de forma assíncrona. O MQF é compatível com vários agentes de mensagens:

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** - O agente de mensagens principal, que fornece uma plataforma escalável para enviar e receber mensagens. Ele inclui um mecanismo para armazenar mensagens não entregues e se baseia na especificação Advanced Message Queuing Protocol (AMQP) 0.9.1.
- **[Artemis do Apache AtiveMQ](https://activemq.apache.org/components/artemis/)** - Um agente de mensagens alternativo que usa o STOMP (Simple Text Oriented Messaging Protocol) para mensagens confiáveis e escalonáveis. Introduzido no Adobe Commerce 2.4.6 e versões posteriores.

## RabbitMQ (AMQP)

O diagrama a seguir ilustra a Estrutura da fila de mensagens:

![Estrutura da Fila de Mensagens](../../assets/configuration/mq-framework.png)

- Um editor é um componente que envia mensagens para uma troca. Ele sabe para qual troca publicar e o formato das mensagens enviadas.

- Um Exchange recebe mensagens de editores e as envia para filas. Embora o [!DNL RabbitMQ] ofereça suporte a vários tipos de trocas, o Commerce usa somente trocas de tópicos. Um tópico inclui uma chave de roteamento, que contém strings de texto separadas por pontos. O formato de um nome de tópico é `string1.string2`: por exemplo, `customer.created` ou `customer.sent.email`.

  O broker permite usar curingas ao definir regras para o encaminhamento de mensagens. Você pode usar um asterisco (`*`) para substituir _uma_ cadeia de caracteres ou um sinal de libra (`#`) para substituir 0 ou mais cadeias de caracteres. Por exemplo, `customer.*` filtraria em `customer.create` e `customer.delete`, mas não `customer.sent.email`. No entanto, `customer.#` filtraria em `customer.create`, `customer.delete` e `customer.sent.email`.

- Uma fila é um buffer que armazena mensagens.

- Um consumidor recebe mensagens. Ele sabe qual fila consumir. Ele pode mapear processadores da mensagem para uma fila específica.

## Artemis do Apache AtiveMQ (STOMP)

Como alternativa ao RabbitMQ, o Adobe Commerce também oferece suporte ao [Apache AtiveMQ Artemis](https://activemq.apache.org/components/artemis/) como agente de mensagens usando o STOMP (Simple Text Oriented Messaging Protocol).

>[!NOTE]
>
>O AtiveMQ Artemis foi introduzido no Adobe Commerce 2.4.6 e versões posteriores.

O diagrama a seguir ilustra a estrutura STOMP com AtiveMQ Artemis:

![STOMP Framework](../../assets/configuration/stomp-framework.png)

### Componentes da estrutura STOMP

- **editor** é um componente que envia mensagens para um destino (fila ou tópico). Ele sabe para qual destino publicar e o formato das mensagens enviadas.

- Um **destino** no STOMP desempenha uma função semelhante às trocas no AMQP, recebendo mensagens de editores e as roteando. STOMP usa endereçamento de destino direto com um padrão hierárquico de nomeação usando pontos: por exemplo, `customer.created` ou `inventory.updated`.

  O Adobe Commerce usa o modo de endereçamento **ANYCAST** para destinos STOMP, que fornece entrega de mensagens ponto a ponto. No modo ANYCAST, as mensagens são entregues a apenas um consumidor a partir de um pool de consumidores disponíveis, permitindo o balanceamento de carga e a distribuição de trabalho em várias instâncias do consumidor.

- Uma **fila** é um buffer que armazena mensagens. Com o endereçamento ANYCAST, a fila garante que as mensagens sejam entregues a apenas um consumidor, mesmo quando vários consumidores estiverem conectados ao mesmo destino.

- Um **consumidor** recebe mensagens de destinos. Ele sabe a qual destino se inscrever e pode processar mensagens com diferentes modos de reconhecimento (automático, cliente ou cliente individual).

## Adaptador MySQL (fallback)

Um sistema básico de fila de mensagens também pode ser configurado sem usar agentes de mensagens externos. Neste sistema, um adaptador MySQL armazena mensagens no banco de dados. Três tabelas de banco de dados (`queue`, `queue_message` e `queue_message_status`) gerenciam a carga de trabalho da fila de mensagens. Os trabalhos da Cron garantem que os consumidores possam receber mensagens. Essa solução não é muito escalável. Agentes de mensagem externos como [!DNL RabbitMQ] ou Apache AtiveMQ Artemis devem ser usados sempre que possível para ambientes de produção.

## Informações relacionadas

Para obter instruções sobre instalação e configuração:

- [Instalar e configurar o RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [Instalar e configurar o AtiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [Gerenciar filas de mensagens](manage-message-queues.md)
- [Consumidores da fila de mensagens](consumers.md)
