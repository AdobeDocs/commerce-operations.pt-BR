---
title: 'Alertas gerenciados no Adobe Commerce: alerta crítico do CPU'
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico do CPU para Adobe Commerce no [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 8629ab18-5eef-4d76-9cf8-88fe2d3439df
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alerta crítico do CPU

Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico do CPU para Adobe Commerce em [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico de disco](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta gerenciado em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe Commerce para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u>**Fazer!**</u>:

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) no Guia de Instalação do Commerce.

<u>**Não!**</u>:

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou colunas adicionais, o que pode causar tensão adicional no CPU ou disco.
* Execute qualquer tarefa administrativa importante (ou seja, o Administrador do Commerce, importações/exportações de dados).
* Limpe o cache.

Seu site pode não responder (se você ainda não estiver passando por uma interrupção do site) se você executar qualquer uma das ações &quot;Não&quot; antes de investigar e resolver a causa do alerta.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como este é um alerta crítico, é altamente recomendável concluir a **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

Verifique se o tíquete de suporte do Adobe Commerce existe. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) na Base de Dados de Conhecimento de Suporte da Commerce. O suporte pode ter recebido um alerta de limite [!DNL New Relic], criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:

1. Motivo do Contato: selecione **[!UICONTROL New Relic CRITICAL alert received]**.
1. Descrição do alerta.
1. [[!DNL New Relic] Link de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Use a [[!DNL New Relic] página Transação de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços Web. Um [low [!DNL Apdex] score](managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente, está relacionado ao banco de dados, [!DNL Redis], ou PHP. New Relic Para obter as etapas, consulte [Exibir transações com a  [!DNL Apdex] insatisfação](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) mais alta.
   * Classifique as transações por throughput mais alto, tempo médio de resposta mais lento, mais demorado e outros limites. Para etapas, consulte [!DNL New Relic] [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se você ainda estiver com dificuldades para identificar a origem, use a [[!DNL New Relic] página Infraestrutura do APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) para identificar serviços com muitos recursos. Para ver as etapas, consulte [!DNL New Relic] [Página de Hosts do monitoramento de infraestrutura: guia Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se você identificar a origem, o SSH no ambiente para investigar mais detalhadamente. Para ver as etapas, consulte [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR) no Guia do Commerce na Nuvem.
1. Se você ainda estiver lutando para identificar a origem:
   * Revise tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
   * Considere verificar e desativar catálogos simples. Para ver as etapas, consulte [Cores de desempenho lento e execução lenta](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) na Base de Dados de Conhecimento de Suporte da Commerce.
   * Se você suspeitar que esteja enfrentando um ataque de DDoS, tente bloquear o tráfego de bot. Para ver as etapas, consulte [Como bloquear tráfego mal-intencionado do Adobe Commerce na infraestrutura em nuvem no nível Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) na Base de Dados de Conhecimento de Suporte da Commerce.
1. Se o problema parecer temporário, execute etapas de mitigação, como um upsize ou coloque o site no modo de manutenção. Para obter as etapas, consulte [Como solicitar o redimensionamento temporário](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) na Base de Dados de Conhecimento de Suporte da Commerce e [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta da Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduz a pressão sobre os serviços. Para obter as etapas, consulte [Teste de carga e tensão](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) no Guia do Commerce na Nuvem.
