---
title: '[!DNL Dashboard]'
description: Saiba mais sobre o [!DNL Dashboard] na guia no [!DNL Site-Wide Analysis Tool], elementos, quando usar, benefícios e práticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

O [!UICONTROL Dashboard] exibições de página [!DNL widgets] que fornecem uma &quot;visualização de um único painel de vidro&quot; da integridade e do status atual do seu site do Adobe Commerce. Cada [!DNL widget] contém um link de acesso para a página de cada recurso, para cada ferramenta em si ou para relatórios (dependendo do [!DNL widget]).
Há também uma lista de [!UICONTROL External Resources] links para o Adobe Commerce, incluindo o [Base de conhecimento de suporte da Central de Ajuda da Adobe Commerce (Central de Ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação do desenvolvedor do Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Pesquisar por patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de segurança](https://helpx.adobe.com/security.html)e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: Exibe recomendações de práticas recomendadas para o seu site. Recommendations (problemas encontrados e recomendações para corrigir) são classificados por prioridade — P0 (Crítico) a P4 (Notificação).
O Recommendations inclui Descrição, Recomendação, Impacto do site, Causa raiz, Cenários/Pré-condições e Ferramentas usadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: Verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos e o código principal instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce. Ela também identifica possíveis problemas que devem ser corrigidos no código antes de tentar atualizar para uma versão mais recente do Adobe Commerce.
O [!UICONTROL Upgrade Compatibility Tool] O permite identificar quando as alterações no código principal foram feitas nos recursos personalizados.

* **[!UICONTROL Security Center Widget]**: Exibe informações de segurança do site.
As informações de segurança mostradas incluem [Tech [!DNL Stack] Conformidade com a versão [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Recommendations de segurança de práticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
O [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) monitora os sites da Adobe Commerce quanto a riscos de segurança. Ele pode detectar de maneira proativa e eficiente o malware em lojas de produtos e notificar os comerciantes se houver riscos de segurança, malware ou ameaças, além de identificar patches e atualizações ausentes do Adobe Commerce.

* **[!UICONTROL Extensions]**: Exibe as extensões atualmente instaladas na instância do Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) Quando disponível, são fornecidas informações para as extensões aí listadas.

* **[!UICONTROL Alerts]**: Exibe o mais recente [!DNL New Relic Managed Alerts] para a instância do Adobe Commerce. Saiba mais sobre [Alertas gerenciados para o Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) e como [Acessar serviços da New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) na Base de conhecimento de suporte da Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: Exibe o software não recomendado que sua instância do Adobe Commerce está usando no momento, com base na sua versão do Adobe Commerce. O software não recomendado é listado por [!UICONTROL Name], [!UICONTROL Installed Version]e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Exibe uma lista curta de todos os patches recomendados com base em ambos os patches que você já instalou e na sua versão do Adobe Commerce. A lista completa de patches recomendados encontra-se no **[!UICONTROL Patches]** guia recurso , que também está no [!DNL Site-Wide Analysis Tool]. Os sistemas são fornecidos pela [[!DNL Quality Patches Tool]: Pesquisar por patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos os patches listados são compatíveis com sua instância atual do Adobe Commerce.
Se não houver patches recomendados para exibir para sua instância do Adobe Commerce, isso [!DNL widget] será exibido, **[!UICONTROL No Recommended Patches]**.

## Quando usar

O **[!UICONTROL Dashboard]** página é o seu centro de comando instantâneo na [!DNL Site-Wide Analysis Tool] para não apenas visualizar facilmente o &quot;panorama geral&quot; da integridade do seu site como um todo, mas também pode ver e acessar ferramentas, recomendações e relatórios específicos para o seu site Adobe Commerce em cada [!DNL widget].

## Benefícios

* O [!DNL widgets] para [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]e [!UICONTROL Security Scan] todos usam gráficos circulares interativos, codificados por cores e fáceis de ler, com legendas de gráfico ao lado e totais de contagem no centro para indicar quantos [!UICONTROL Recommendations], [!UICONTROL Extensions]e [!UICONTROL Security Scan Tool] itens que cada recurso tem. [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] os gráficos são separados por severidade. [!UICONTROL Extensions] são separadas em quatro classificações: versão atual, versão antiga, desativada e desconhecida.

* [!DNL New Relic Alerts] são listados com o alerta mais recente no topo, incluindo uma breve descrição e há quanto tempo o alerta ocorreu.

* O [!UICONTROL Recommendations] e [!UICONTROL Extensions] [!DNL widgets] tenha acesso à página completa de dados de cada recurso clicando em **[!UICONTROL View All]**.

* O [!UICONTROL Security Scan Tool] tem um **[!UICONTROL View Report]** no [!DNL widget] que leva você ao [!UICONTROL Recommendations] página.

* O [!DNL Upgrade Compatibility Tool] tem um **[!UICONTROL Run Upgrade Scan]** no botão [!DNL widget] janela.

## Práticas recomendadas para usar o [!UICONTROL Dashboard]

* Clique em cada [!DNL widget] para acessar os dados detalhados, fornece informações e compreensão sobre a segurança, integridade, recomendações e práticas recomendadas do seu site para melhorá-lo.

* Vá para o [!UICONTROL Security Scan Tool] [!DNL widget] e clique em [!UICONTROL View Report] para visualizar uma [!UICONTROL Recommendations] relatório para seu site.

* Use o [!DNL External Resources] links para obter mais informações, manter-se atualizado sobre patches de segurança, atualizações e práticas recomendadas, ou aproveitar os insights do [Base de conhecimento de suporte da Central de Ajuda da Adobe Commerce (Central de Ajuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentação do desenvolvedor do Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Pesquisar por patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Central de segurança](https://helpx.adobe.com/security.html)e [Observação para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
