---
title: "ACSD-51792: a página não tem evento de impressão"
description: Aplique o patch ACSD-51792 para corrigir o problema de desempenho do Adobe Commerce em que uma página não tem o evento de impressão quando o Google Tag Manager 4 está ativado.
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-51792: a página não tem evento de impressão

O patch ACSD-51792 corrige o problema de desempenho em que uma página não tem o evento de impressão quando o [!DNL Google Tag Manager] 4 está habilitado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51792. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página não tem o evento de impressão quando [!DNL Google Tag Manager] 4 está habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Configure a integração do **[!DNL GoogleTag Manager]**.
1. Vá para o [Assistente de Marca da Google](https://tagassistant.google.com/) e conclua as etapas necessárias para se conectar ao seu site.
1. Abra uma página de categoria que tenha uma lista de produtos na loja.
1. Verifique o evento de impressões no observador do Assistente de tags.

<u>Resultados esperados</u>:

O evento de impressão deve começar com todos os produtos na página.

<u>Resultados reais</u>:

A página não tem o evento de impressão no observador do Assistente de tags.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
