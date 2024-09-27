---
title: "ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis"
description: Aplique o patch ACSD-47803 para corrigir o problema do Adobe Commerce em que as amostras de produto configuráveis e indisponíveis são exibidas como disponíveis.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis

O patch ACSD-47803 corrige o problema em que amostras de produtos configuráveis e indisponíveis são exibidas como disponíveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-47803. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As amostras de produtos configuráveis indisponíveis são exibidas como disponíveis.

<u>Etapas a serem reproduzidas</u>:

>[!NOTE]
>
>As etapas abaixo se referem a dados de amostra como exemplo.

1. No Administrador [!UICONTROL Commerce], vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e defina o **[!UICONTROL Display Out of Stock Products]** como *Sim*.
1. Novamente, no Admin, navegue até **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e edite um produto configurável na página de edição do produto (por exemplo, SKU &quot;WB04&quot;, se estiver usando dados de exemplo):
   * Para uma das variantes de configuração, defina a quantidade como *0* (por exemplo, para &quot;WB04-M-Roxo&quot;).
1. Agora abra o produto configurável na loja.
1. Selecione o tamanho do produto da variante configurável com zero estoque (ou seja, &quot;M&quot;).

<u>Resultados esperados</u>:

As opções indisponíveis estão desabilitadas e marcadas como [!UICONTROL Out of Stock].

<u>Resultados reais</u>:

Todas as amostras de cores estão habilitadas, mesmo a que é [!UICONTROL Out of Stock].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
