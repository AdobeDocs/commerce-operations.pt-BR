---
title: 'Alertas gerenciados para Adobe Commerce: [!DNL Apdex] alerta crítico'
description: Este artigo fornece etapas de solução de problemas quando você recebe um  [!DNL Apdex] alerta crítico do Adobe Commerce em [!DNL New Relic]. The [!DNL Apdex] a pontuação mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 028e9b3ba60c10c7c09672888a058ca34faeb365
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: [!DNL Apdex] alerta crítico

Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico do [!DNL Apdex] para o Adobe Commerce em [!DNL New Relic]. A pontuação [!DNL Apdex] mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico de apdex](../../assets/managed-alerts/apdex-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

* Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce
* Arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem

## Problema

Você receberá um alerta gerenciado em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Fazer!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) no Guia de Instalação do Commerce.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional no CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, o Administrador do Commerce, importações/exportações de dados).
* Limpe o cache.

Fazer o que foi descrito acima quando você recebeu um alerta crítico, antes de solucionar a causa do alerta, pode fazer com que o site não responda, caso você ainda não esteja passando por uma interrupção do site.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como este é um alerta crítico, é altamente recomendável concluir a **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) na Base de Dados de Conhecimento de Suporte da Commerce. O suporte pode ter recebido um alerta de limite [!DNL New Relic], criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do Contato: selecione **[!UICONTROL New Relic CRITICAL alert received]**.
   * Descrição do alerta.
   * [[!DNL New Relic] Link de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Para identificar a origem do problema, use a [[!DNL New Relic] página Transação do APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classificar transações por [!DNL Apdex] pontuações crescentes. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços Web. Uma pontuação baixa de [!DNL Apdex] pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, [!DNL Redis], ou PHP. Para etapas, consulte [[!DNL New Relic] Exibir transações com maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter as etapas, consulte [[!DNL New Relic] Localizar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se você ainda estiver com dificuldades para identificar o problema, use a [[!DNL New Relic] página Infraestrutura do APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Use a [[!DNL New Relic] página Infraestrutura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar processos que consomem muitos recursos. Para ver as etapas, consulte a [[!DNL New Relic] página Hosts de monitoramento de infraestrutura: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se serviços como [!DNL Redis] ou MySQL forem a principal fonte de consumo de memória, tente o seguinte:
   * Verifique se você está na versão mais recente. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=pt-BR) no Guia do Commerce na Nuvem.
   * Verifique problemas do MySQL, como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter as etapas, consulte [Problemas mais comuns do banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=pt-BR) no Manual de implementação do Commerce.
   * Verifique os problemas do PHP. Revise os processos em execução executando `ps aufx` na CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Para obter as etapas de solução de problemas, consulte [Cores de desempenho lento e execução demorada](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) e [Trabalho do Cron preso no status &quot;em execução&quot;](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) na Base de Dados de Conhecimento de Suporte da Commerce.

1. Depois que a fonte é identificada, SSH entra no ambiente para investigar mais detalhadamente. Para ver as etapas, consulte [SSH para o seu ambiente](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) no Guia do Commerce na Nuvem.
1. Se você ainda estiver lutando para identificar a fonte, revise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Se você não conseguir encontrar uma solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção se ainda não tiver feito isso. Para obter as etapas, consulte [Como solicitar o redimensionamento temporário](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) na Base de Dados de Conhecimento de Suporte da Commerce e [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce.
1. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta da Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Consulte [Teste de carga e estresse](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) no Guia do Commerce na Nuvem.
