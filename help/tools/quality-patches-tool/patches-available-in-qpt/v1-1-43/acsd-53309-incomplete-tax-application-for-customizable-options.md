---
title: 'ACSD-53309: Aplicativo de imposto incompleto para opções personalizáveis e rótulo [!UICONTROL Regular Price]'
description: Aplique o patch ACSD-53309 para corrigir o problema do Adobe Commerce em que o imposto não é totalmente aplicado no rótulo '[!UICONTROL Regular Price]' quando uma opção personalizável é selecionada.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: 7f4a8923-11dd-48b2-9d97-77de5c2b24ce
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53309: aplicativo de imposto incompleto para opções personalizáveis e rótulo &#39;[!UICONTROL Regular Price]&#39;

O patch ACSD-53309 corrige o problema em que o imposto não é totalmente aplicado no rótulo &#39;[!UICONTROL Regular Price]&#39; quando uma opção personalizável é selecionada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-53309. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O imposto não é totalmente refletido no rótulo &#39;[!UICONTROL Regular Price]&#39; quando uma opção personalizável é escolhida.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Painel de administração.
1. Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** para definir as configurações de imposto.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Conjunto **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Reino Unido*.

1. Criar os seguintes *[!UICONTROL Tax Rate]* e *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Estados Unidos
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. Crie um produto simples e defina o seguinte:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Na lista suspensa, defina tipo como opção personalizada com preço definido como 15%
1. Vá para a página do produto do item simples feito na loja.
1. Escolha a opção personalizada criada, *15%*.

<u>Resultados esperados</u>:

* O imposto de 20% é aplicado à opção personalizada selecionada.
* &#39;[!UICONTROL Regular Price]&#39; = 151,80.

<u>Resultados reais</u>:

* O imposto de 20% não é aplicado à opção personalizada selecionada.
* &#39;[!UICONTROL Regular Price]&#39; = 148,50.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
