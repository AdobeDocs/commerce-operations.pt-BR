---
title: 'Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta de aviso de memória'
description: Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso do  [!DNL Redis] Adobe Commerce no [!DNL New Relic]. É necessária uma ação imediata.
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: f71b5e83-fb6c-4183-87c7-f41cbdf4c684
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: [!DNL Redis] alerta de aviso de memória

Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso do [!DNL Redis] para o Adobe Commerce no [!DNL New Relic]. É necessária ação imediata para resolver o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado:

![new_relic_redis_memory_warning.png](../../assets/managed-alerts/new_relic_redis_memory_warning.png)

## Produtos e versões afetados

Todas as versões da arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce.

## Problema

Você receberá um alerta em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão de alertas usando insights do suporte e da engenharia.

**<u>Fazer!</u>**

* É recomendável suspender qualquer implantação agendada até que esse alerta seja limpo.
* Se o site estiver respondendo ou ficar totalmente sem resposta, coloque-o imediatamente no modo de manutenção. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce.
* Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) no Guia de Instalação do Commerce.

**<u>Não!</u>**

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional no CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, uma ação importante no Administrador do Commerce, como importações/exportações de dados, mídia de limpeza, categorias de salvamento com um grande número de produtos atribuídos e atualizações em massa).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Verifique se a Memória Usada do [!DNL Redis] está aumentando ou diminuindo na página [one.newrelic.com](https://login.newrelic.com/login) > **Infraestrutura** > **Serviços de terceiros**. Selecione o painel [!DNL Redis]. Se estiver estável ou aumentando, [envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) para fazer o upsizing do cluster ou aumente o limite de `maxmemory` para o próximo nível.
1. Se não for possível identificar a causa do aumento do consumo de memória do [!DNL Redis], analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Verifique se há extensões de terceiros que se comportam mal:
   * Tente encontrar uma correlação com extensões de terceiros instaladas recentemente e a hora em que o problema começou.
   * Revise as extensões que poderiam afetar o cache do Adobe Commerce e fazer com que o cache cresça rapidamente. Por exemplo, blocos de layout personalizados, substituição da funcionalidade de cache e armazenamento de grandes quantidades de dados em cache.
1. Se não houver evidência de extensões com comportamento incorreto, [Instale os patches mais recentes para corrigir [!DNL Redis] problemas do Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues). Se as etapas acima não ajudarem a identificar ou solucionar o problema, considere habilitar o cache L2 para reduzir o tráfego de rede entre o aplicativo e o [!DNL Redis]. Para obter informações gerais sobre o que é cache L2, consulte [cache L2 no aplicativo do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cache/level-two-cache) no Guia de Configuração do Commerce. Para habilitar o cache L2 para a infraestrutura em nuvem, tente o seguinte:
   * Atualize as Ferramentas ECE se estiverem abaixo da versão 2002.1.2.
   * Configure o Cache L2 usando a [variável REDIS\_BACKEND](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) e atualizando o arquivo `.magento.env.yaml`:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
