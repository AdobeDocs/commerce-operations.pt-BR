---
title: '[!DNL Dashboard]'
description: Saiba mais sobre a  [!DNL Dashboard] guia em  [!DNL Site-Wide Analysis Tool], elementos, quando usar, benefícios e práticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

A página [!UICONTROL Dashboard] mostra rapidamente [!DNL widgets] que fornecem um &quot;painel único de visão&quot; da integridade e do status atual do site do Adobe Commerce. Cada [!DNL widget] contém um link de acesso para a página de cada recurso, para cada ferramenta ou para relatórios (dependendo do [!DNL widget]).
Também há uma lista de links [!UICONTROL External Resources] para o Adobe Commerce, incluindo a [Base de Dados de Conhecimento de Suporte da Central de Ajuda da Adobe Commerce (Central de Ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação de Desenvolvedor do Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de Segurança](https://helpx.adobe.com/security.html) e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: exibe as práticas recomendadas para o seu site. As recomendações (problemas encontrados e recomendações para corrigir) são classificadas por prioridade: P0 (Crítico) a P4 (Notificação).
As recomendações incluem Descrição, Recomendação, Impacto no site, Causa raiz, Cenários/pré-condições e Ferramentas usadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce. Ele também identifica possíveis problemas que devem ser corrigidos em seu código antes de tentar atualizar para uma versão mais recente do Adobe Commerce.
O [!UICONTROL Upgrade Compatibility Tool] permite identificar quando as alterações no código principal foram feitas nos recursos personalizados.

* **[!UICONTROL Security Center Widget]**: Exibe insights de segurança para o site.
As informações de segurança mostradas incluem [Conformidade técnica [!DNL Stack] com a versão [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Recomendações de Segurança de Práticas Recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
O [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) monitora os sites do Adobe Commerce em busca de riscos de segurança. Ele pode detectar de forma proativa e eficiente o malware em lojas de comerciantes e notificá-los se houver riscos de segurança, malware ou ameaças, além de identificar patches e atualizações ausentes do Adobe Commerce.

* **[!UICONTROL Extensions]**: exibe as extensões atualmente instaladas em sua instância do Adobe Commerce. As informações do [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) são fornecidas, quando disponíveis, para as extensões listadas lá.

* **[!UICONTROL Alerts]**: exibe o [!DNL New Relic Managed Alerts] mais recente para a instância do Adobe Commerce. Saiba mais sobre [Alertas gerenciados para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) e como [Acessar serviços da New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) na Base de Dados de Conhecimento de Suporte da Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: exibe o software não recomendado que sua instância do Adobe Commerce está usando no momento, com base na sua versão do Adobe Commerce. O software não recomendado está listado por [!UICONTROL Name], [!UICONTROL Installed Version] e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Exibe uma pequena lista de todos os patches recomendados com base em patches que talvez você já tenha instalado e na sua versão do Adobe Commerce. A lista completa de patches recomendados encontra-se na guia de recursos **[!UICONTROL Patches]**, que também está dentro do [!DNL Site-Wide Analysis Tool]. Os patches são fornecidos por [[!DNL Quality Patches Tool]: procure por patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos os patches listados são compatíveis com a instância atual do Adobe Commerce.
Se não houver patches recomendados para exibir para a instância do Adobe Commerce, este [!DNL widget] será exibido, **[!UICONTROL No Recommended Patches]**.

## Quando usar

A página **[!UICONTROL Dashboard]** é a sua central de comandos rápida no [!DNL Site-Wide Analysis Tool] para não apenas visualizar facilmente o &quot;cenário geral&quot; da integridade do site como um todo, mas você também pode ver e acessar ferramentas, recomendações e relatórios específicos para o seu site do Adobe Commerce por meio de cada [!DNL widget].

## Benefícios

* Os [!DNL widgets] para [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] e [!UICONTROL Security Scan] todos usam gráficos circulares interativos codificados por cores de fácil leitura com legendas para os gráficos à lateral e totais de contagem no centro para denotar quantos itens [!UICONTROL Recommendations], [!UICONTROL Extensions] e [!UICONTROL Security Scan Tool] cada recurso tem. Os gráficos [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] são separados por severidade. [!UICONTROL Extensions] são separadas em quatro classificações: versão atual, versão antiga, desabilitada e desconhecida.

* [!DNL New Relic Alerts] estão listados com o alerta mais recente no topo, incluindo uma breve descrição e há quanto tempo o alerta ocorreu.

* O [!UICONTROL Recommendations] e o [!UICONTROL Extensions] [!DNL widgets] têm acesso à página inteira de dados de cada recurso clicando em **[!UICONTROL View All]**.

* O [!UICONTROL Security Scan Tool] tem um link **[!UICONTROL View Report]** na janela [!DNL widget] que direciona você à página [!UICONTROL Recommendations].

* O [!DNL Upgrade Compatibility Tool] tem um botão **[!UICONTROL Run Upgrade Scan]** na janela [!DNL widget].

## Práticas recomendadas para usar o [!UICONTROL Dashboard]

* Clique em cada [!DNL widget] para acessar os dados detalhados que ele fornece para obter informações do insight e sobre a segurança, a integridade, as recomendações e as práticas recomendadas do seu site para melhorá-lo.

* Vá para o [!UICONTROL Security Scan Tool] [!DNL widget] e clique em [!UICONTROL View Report] para exibir um relatório [!UICONTROL Recommendations] para seu site.

* Use os links [!DNL External Resources] para saber mais informações, manter-se atualizado sobre patches de segurança, atualizações e práticas recomendadas, ou aproveitar o insight da [Base de Dados de Conhecimento de Suporte da Central de Ajuda da Adobe Commerce (Central de Ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação para Desenvolvedores da Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de Segurança](https://helpx.adobe.com/security.html) e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
