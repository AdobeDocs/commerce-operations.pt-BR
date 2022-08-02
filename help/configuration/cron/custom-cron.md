---
title: Trabalhos Cron
description: Saiba mais sobre grupos cron e como criar um trabalho cron personalizado.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Trabalhos Cron

Esses tópicos discutem como configurar um trabalho cron personalizado e, opcionalmente, um grupo cron personalizado. Se sua extensão do Commerce exigir a execução periódica de tarefas agendadas, você pode usar esses tópicos para configurar um cron _trabalho_ (a tarefa agendada) e, opcionalmente, um cron _grupo_, que executa tarefas personalizadas ao mesmo tempo.

Se você usar um grupo cron fornecido pelo Commerce, não será necessário definir um grupo cron personalizado; no entanto, se você quiser que seus trabalhos do cron sejam executados em uma programação diferente ou se quiser que todos sejam executados juntos, defina um grupo do cron

O aplicativo Commerce fornece os seguintes grupos cron:

- `default`, que contém a maioria dos trabalhos do cron
- `index`, que é atualizado [indexadores](../cli/manage-indexers.md)
- `consumers`, que executa a fila de mensagens [consumidores](../cli/start-message-queues.md)
- Esses tópicos estão disponíveis somente no Adobe Commerce
   - `staging`, que é executado [Relacionado ao armazenamento temporário](https://docs.magento.com/user-guide/cms/content-staging.html) tarefas
   - `catalog_event`, que executa tarefas para regras de carrinho de compras e de direcionamento
