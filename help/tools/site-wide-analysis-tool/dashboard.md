---
title: '[!DNL Dashboard]'
description: Saiba mais sobre o [!DNL Dashboard] na guia [!DNL Site-Wide Analysis Tool], elementos, quando usar, benefícios e práticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

A variável [!UICONTROL Dashboard] A página mostra uma visão geral [!DNL widgets] que fornecem um &quot;painel único de visão&quot; da integridade e status atual do seu site da Adobe Commerce. Each [!DNL widget] contém um link de acesso para a página de cada recurso, para cada ferramenta ou para relatórios (dependendo da [!DNL widget]).
Há também uma lista de [!UICONTROL External Resources] links para o Adobe Commerce, incluindo o [Base de conhecimento de suporte do Centro de ajuda da Adobe Commerce (Centro de ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação do desenvolvedor do Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de segurança](https://helpx.adobe.com/security.html), e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: exibe as recomendações de práticas recomendadas para o site. O Recommendations (problemas encontrados e recomendações para corrigir) é classificado por prioridade — P0 (Crítico) a P4 (Notificação).
A Recommendations inclui Descrição, Recomendação, Impacto no site, Causa raiz, Cenários/pré-condições e Ferramentas usadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce. Ele também identifica possíveis problemas que devem ser corrigidos em seu código antes de tentar atualizar para uma versão mais recente do Adobe Commerce.
A variável [!UICONTROL Upgrade Compatibility Tool] permite identificar quando as alterações no código principal foram feitas nos recursos personalizados.

* **[!UICONTROL Security Center Widget]**: exibe insights de segurança do site.
As informações de segurança mostradas incluem [Tecnologia [!DNL Stack] Conformidade de versão com [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Recommendations de segurança de práticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
A variável [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) O monitora os sites da Adobe Commerce em busca de riscos de segurança. Ele pode detectar de forma proativa e eficiente o malware em lojas de comerciantes e notificá-los se houver riscos de segurança, malware ou ameaças, além de identificar patches e atualizações ausentes do Adobe Commerce.

* **[!UICONTROL Extensions]**: exibe as extensões instaladas no momento na instância do Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) as informações são fornecidas, quando disponíveis, para as extensões listadas lá.

* **[!UICONTROL Alerts]**: exibe a versão mais recente [!DNL New Relic Managed Alerts] para a instância do Adobe Commerce. Saiba mais sobre [Alertas gerenciados para o Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) e como [Acessar serviços da New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) na Base de conhecimento de suporte da Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: exibe o software não recomendado que sua instância do Adobe Commerce está usando no momento, com base na versão do Adobe Commerce. O software não recomendado está listado por [!UICONTROL Name], [!UICONTROL Installed Version], e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: exibe uma pequena lista de patches recomendados com base em patches que talvez você já tenha instalado e na sua versão do Adobe Commerce. A lista completa de patches recomendados encontra-se no **[!UICONTROL Patches]** guia recurso, que também está na guia [!DNL Site-Wide Analysis Tool]. Os patches são fornecidos pelo [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos os patches listados são compatíveis com a instância atual do Adobe Commerce.
Se não houver patches recomendados para exibir para sua instância do Adobe Commerce, este [!DNL widget] exibirá, **[!UICONTROL No Recommended Patches]**.

## Quando usar

A variável **[!UICONTROL Dashboard]** é a sua central de comandos rápida no [!DNL Site-Wide Analysis Tool] para ter uma visão geral da saúde do seu site como um todo, além de visualizar e acessar ferramentas, recomendações e relatórios específicos para o seu site da Adobe Commerce em cada [!DNL widget].

## Benefícios

* A variável [!DNL widgets] para [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], e [!UICONTROL Security Scan] todos usam gráficos interativos circulares codificados por cores de fácil leitura com legendas de gráfico ao lado e totais de contagem no centro para indicar quantos [!UICONTROL Recommendations], [!UICONTROL Extensions], e [!UICONTROL Security Scan Tool] itens que cada recurso tem. [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] os gráficos são separados por severidade. [!UICONTROL Extensions] são separadas em quatro classificações: versão atual, versão antiga, desativado e desconhecido.

* [!DNL New Relic Alerts] são listados com o alerta mais recente no topo, incluindo uma breve descrição e há quanto tempo o alerta ocorreu.

* A variável [!UICONTROL Recommendations] e [!UICONTROL Extensions] [!DNL widgets] tenha acesso à página completa de dados de cada recurso clicando em **[!UICONTROL View All]**.

* A variável [!UICONTROL Security Scan Tool] tem um **[!UICONTROL View Report]** no [!DNL widget] janela que leva você ao [!UICONTROL Recommendations] página.

* A variável [!DNL Upgrade Compatibility Tool] tem um **[!UICONTROL Run Upgrade Scan]** botão na caixa [!DNL widget] janela.

## Práticas recomendadas para usar o [!UICONTROL Dashboard]

* Clique em cada [!DNL widget] para acessar os dados detalhados que ele fornece para obter informações e compreensão da segurança, integridade, recomendações e práticas recomendadas do site para melhorá-lo.

* Vá para a [!UICONTROL Security Scan Tool] [!DNL widget] e clique em [!UICONTROL View Report] para exibir um [!UICONTROL Recommendations] relatório do site.

* Use o [!DNL External Resources] links para obter mais informações, manter-se atualizado sobre patches de segurança, atualizações e práticas recomendadas ou aproveitar o insight do [Base de conhecimento de suporte do Centro de ajuda da Adobe Commerce (Centro de ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação do desenvolvedor do Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de segurança](https://helpx.adobe.com/security.html), e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
