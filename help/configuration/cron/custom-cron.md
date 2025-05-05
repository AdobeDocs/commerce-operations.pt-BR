---
title: Cron jobs
description: Saiba mais sobre grupos cron e como criar um trabalho cron personalizado.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron jobs

Estes tópicos discutem como configurar um trabalho cron personalizado e, opcionalmente, um grupo cron personalizado. Se sua extensão do Commerce requer tarefas agendadas para execução periódica, você pode usar esses tópicos para configurar um _trabalho_ do cron (a tarefa agendada) e, opcionalmente, um _grupo_ do cron, que executa tarefas personalizadas ao mesmo tempo.

Se você usar um grupo cron fornecido pela Commerce, não será necessário definir um grupo cron personalizado. No entanto, se você quiser que seus trabalhos cron sejam executados em um cronograma diferente ou se quiser que todos eles sejam executados juntos, defina um grupo cron

O aplicativo Commerce fornece os seguintes grupos cron:

- `default`, que contém a maioria dos trabalhos cron
- `index`, que atualiza [indexadores](../cli/manage-indexers.md)
- `consumers`, que executa os [consumidores](../cli/start-message-queues.md) da fila de mensagens
- Estes tópicos estão disponíveis somente no Adobe Commerce
   - `staging`, que executa tarefas [relacionadas a preparo](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/content-design/staging/content-staging)
   - `catalog_event`, que executa tarefas para regras de carrinho de compras e destino
