---
title: Cron jobs
description: Saiba mais sobre grupos cron e como criar um trabalho cron personalizado.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Cron jobs

Estes tópicos discutem como configurar um trabalho cron personalizado e, opcionalmente, um grupo cron personalizado. Se sua extensão do Commerce exigir tarefas agendadas para execução periódica, você poderá usar esses tópicos para configurar um cron _tarefa_ (a tarefa agendada) e, opcionalmente, um cron _grupo_, que executa tarefas personalizadas ao mesmo tempo.

Se você usar um grupo cron fornecido pelo Commerce, não será necessário definir um grupo cron personalizado. No entanto, se você quiser que seus trabalhos cron sejam executados em um cronograma diferente ou que todos eles sejam executados juntos, defina um grupo cron

O aplicativo Commerce fornece os seguintes grupos cron:

- `default`, que contém a maioria dos trabalhos cron
- `index`, que atualiza [indexadores](../cli/manage-indexers.md)
- `consumers`, que executa a fila de mensagens [consumidores](../cli/start-message-queues.md)
- Estes tópicos estão disponíveis somente no Adobe Commerce
   - `staging`, que executa [Relacionado ao preparo](https://docs.magento.com/user-guide/cms/content-staging.html) tarefas
   - `catalog_event`, que executa tarefas para regras de carrinho de compras e direcionamento
