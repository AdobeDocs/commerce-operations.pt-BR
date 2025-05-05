---
title: 'Alertas gerenciados para Adobe Commerce: alerta de aviso do CPU'
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta de aviso do CPU para o Adobe Commerce no [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 09b5331df0b7504b1a3a792d4203f0eaaab842cc
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Alertas gerenciados para Adobe Commerce: alerta de aviso do CPU

Este artigo fornece etapas de solução de problemas quando você recebe um alerta de aviso do CPU para o Adobe Commerce em [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta de aviso do CPU](../../assets/managed-alerts/cpu-warning-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Fazer!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele não responder totalmente. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) no Guia de Instalação do Commerce.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional no CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Use a [[!DNL New Relic] página Transação de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classificar transações por [!DNL Apdex] pontuações crescentes. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços Web. [Uma  [!DNL Apdex] pontuação](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce) baixa pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, [!DNL Redis], ou PHP. Para etapas, consulte [!DNL New Relic] [Exibir transações com maior [!DNL Apdex] insatisfação](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#apdex-dissat).
   * Classifique as transações por throughput mais alto, tempo médio de resposta mais lento, mais demorado e outros limites. Para obter as etapas, consulte [[!DNL New Relic] Localizar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se você ainda estiver com dificuldades para identificar a origem, use a [[!DNL New Relic] página Infraestrutura do APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar os serviços com muitos recursos. Para ver as etapas, consulte a [!DNL New Relic] [página Hosts de monitoramento de infraestrutura: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se você identificar a origem, o SSH no ambiente para investigar mais detalhadamente. Para ver as etapas, consulte [SSH para o seu ambiente](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) no Guia do Commerce na Nuvem.
1. Se você ainda estiver lutando para identificar a origem:
   * Revise tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
   * Considere verificar e desativar catálogos simples. Para ver as etapas, consulte [Cores de desempenho lento e execução lenta](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) na Base de Dados de Conhecimento de Suporte da Commerce.
   * Se você suspeitar que esteja enfrentando um ataque de DDoS, tente bloquear o tráfego de bot. Para ver as etapas, consulte [Como bloquear tráfego mal-intencionado para o Adobe Commerce no nível Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) na Base de Dados de Conhecimento de Suporte da Commerce.
1. Se o problema parecer temporário, execute etapas de mitigação, como um upsize ou coloque o site no modo de manutenção. Para obter as etapas, consulte [Como solicitar o redimensionamento temporário](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) na Base de Dados de Conhecimento de Suporte da Commerce e [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta da Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Para obter as etapas, consulte [Teste de carga e tensão](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) no Guia do Commerce na Nuvem.
