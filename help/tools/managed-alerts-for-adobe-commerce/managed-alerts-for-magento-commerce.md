---
title: Alertas gerenciados para o Adobe Commerce
description: Se você for cliente da arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce, poderá usar alertas gerenciados para entender a integridade do site. Se você for um cliente de arquitetura de plano inicial do Adobe Commerce na infraestrutura em nuvem, receberá apenas alertas para as  [!DNL Apdex] condições e de taxa de erro.
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: efb58b920a9b72ac96bbd28aaae6210ede84e24f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Alertas gerenciados para o Adobe Commerce


Configuramos os principais painéis e alertas para ajudá-lo a entender quando seu site está atingindo níveis críticos de armazenamento e [!DNL Apdex] (satisfação dos usuários com o tempo de resposta dos aplicativos e serviços). Isso pode ajudá-lo a tomar medidas antes que você perceba tempos de resposta lentos ou uma interrupção. Você poderá solucionar problemas de alertas com os artigos listados abaixo. Antes de usar os alertas, primeiro configure os canais de notificação. Consulte [[!DNL New Relic] Configurar canais de notificação](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) no Guia do Commerce na nuvem.

>[!NOTE]
>
>Se os alertas gerenciados para a política de alertas da Adobe Commerce não estiverem disponíveis, talvez seja porque essa conta foi recém-criada ou [!DNL New Relic] foi configurada recentemente. Um processo é executado todas as terças-feiras para adicionar a política de alerta a essas contas. A política de alerta deve estar disponível para você no dia seguinte à execução do próximo processo. Se a política ainda estiver ausente, [envie uma solicitação de suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) e inclua a ID do projeto.

Consulte a tabela abaixo para obter os links para os artigos da Base de Dados de Conhecimento que fornecem as etapas de solução de problemas para esses alertas:

* Alertas gerenciados para Adobe Commerce: alerta de aviso do CPU
* Alertas gerenciados para Adobe Commerce: alerta crítico do CPU
* Alertas gerenciados para Adobe Commerce: alerta de aviso de memória
* Alertas gerenciados para Adobe Commerce: alerta crítico de memória
* Alertas gerenciados para Adobe Commerce: alerta de aviso [!DNL Apdex]
* Alertas gerenciados para Adobe Commerce: [!DNL Apdex] alerta crítico
* Alertas gerenciados para Adobe Commerce: alerta de aviso de disco
* Alertas gerenciados para Adobe Commerce: alerta crítico de disco
* Alertas gerenciados no Adobe Commerce: alertas do MariaDB
* Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta de aviso de memória
* Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta crítico de memória

>[!NOTE]
>
>Os limites definidos para Alertas de aviso e Alertas críticos baseiam-se em pesquisas que estamos fazendo usando dados históricos de desempenho em nossa base de clientes e representam os insights mais recentes das equipes de suporte e engenharia da Adobe Commerce. Observe que esses limites estão sujeitos a alterações com base na análise mais recente e contínua. O fluxo de alerta típico é receber alertas de gravidade menor a maior. Portanto, você provavelmente receberá um alerta de Aviso antes de receber um alerta Crítico. Consulte os links para os artigos para conhecer as etapas da solução de problemas.

| Severidade | CPU | Memória | Disco | [!DNL Apdex] | MariaDB | Memória [!DNL Redis] | Artigo de solução de problemas |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Aviso | ✅ |        |      |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta de aviso do CPU](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Crítico | ✅ |        |      |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta crítico do CPU](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Aviso |     | ✅ |      |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta de aviso de memória](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Crítico |     | ✅ |      |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta crítico de memória](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Aviso |     |        |      | ✅ |         |              | [Alertas gerenciados para Adobe Commerce: [!DNL Apdex] alerta de aviso](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Crítico |     |        |      | ✅ |         |              | [Alertas gerenciados para Adobe Commerce: [!DNL Apdex] alerta crítico](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Aviso |     |        | ✅ |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta de aviso de disco](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Crítico |     |        | ✅ |       |         |              | [Alertas gerenciados para Adobe Commerce: alerta crítico de disco](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Aviso e Crítico |     |        |      |       | ✅ |              | [Alertas gerenciados no Adobe Commerce: alertas do MariaDB](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Aviso |     |        |      |       |         | ✅ | [Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta de aviso de memória](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Crítico |     |        |      |       |         | ✅ | [Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta crítico de memória](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
