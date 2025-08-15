---
title: 'Alertas gerenciados para Adobe Commerce: alerta de aviso de memória'
description: Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso de memória do Adobe Commerce no [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0910a431-bf2c-469e-81e2-92c8d9be3249
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta de aviso de memória

Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso de memória do Adobe Commerce em [!DNL New Relic]. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![aviso de memória](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe Commerce para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u>**Fazer!**</u>:

* É recomendável suspender qualquer implantação agendada até que esse alerta seja apagado.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) no Guia de Instalação do Commerce.

<u>**Não!**</u>:

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais, o que pode causar stress adicional no CPU ou no disco.
* Realize qualquer tarefa administrativa importante (ou seja, o Administrador, importações/exportações de dados).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Use a [[!DNL New Relic] página Infraestrutura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar os principais processos com uso intenso de memória. Para obter etapas, consulte [[!DNL New Relic] [página de Hosts de monitoramento de infraestrutura: [!UICONTROL Processes] guia]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Se serviços como [!DNL Redis] ou MySQL forem a principal fonte de consumo de memória, tente o seguinte:

   * Verifique se você está na versão mais recente. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Change Services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) no Guia do Commerce na Nuvem.
   * Se ainda não conseguir identificar a origem do aumento do consumo de memória, verifique se há problemas do MySQL, como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter as etapas, consulte [Problemas mais comuns do banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) no Manual de implementação do Commerce.
   * Se não houver problemas do MySQL, verifique se há problemas do PHP. Revise os processos em execução executando `ps aufx` na CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Consulte [Crons de desempenho lento e execução demorada](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) e [Trabalho do Cron preso no status &quot;em execução&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) na Base de Dados de Conhecimento de Suporte da Commerce para ver as etapas de solução de problemas.

1. Se você ainda estiver lutando para identificar a origem do problema, use a [[!DNL New Relic] página Transação de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:

   * Classificar transações por [!DNL Apdex] pontuações crescentes. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços Web. Um [low [!DNL Apdex] score](managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente, é o banco de dados, [!DNL Redis], ou PHP. New Relic Para obter as etapas, consulte [Exibir transações com a  [!DNL Apdex] insatisfação](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) mais alta.
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter as etapas, consulte [[!DNL New Relic] Localizar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se você ainda estiver com dificuldades para identificar o problema, use a [[!DNL New Relic] página Infraestrutura do APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).

1. Se não conseguir identificar a causa do aumento do consumo de memória, analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.

1. Se os métodos acima não ajudarem você a encontrar a causa e/ou a solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção, caso ainda não o tenha feito. Para obter as etapas, consulte [Como solicitar o redimensionamento temporário](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) na Base de Dados de Conhecimento de Suporte da Commerce e [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce.

1. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta da Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Consulte [Teste de carga e estresse](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) no Guia do Commerce na Nuvem.
