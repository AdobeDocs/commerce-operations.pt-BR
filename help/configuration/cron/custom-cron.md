---
title: Cron jobs
description: Saiba mais sobre grupos cron e como criar trabalhos cron personalizados no Adobe Commerce. Descubra a configuração da tarefa agendada e a configuração do grupo cron.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '179'
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
  - `staging`, que executa tarefas [relacionadas a preparo](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging)
  - `catalog_event`, que executa tarefas para regras de carrinho de compras e destino
