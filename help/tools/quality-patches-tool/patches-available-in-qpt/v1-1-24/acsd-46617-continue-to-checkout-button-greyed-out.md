---
title: 'ACSD-46617: botão **[!UICONTROL Continue to Checkout]** esmaecido quando o subtotal é maior que o valor mínimo de pedido configurado'
description: Aplique o patch ACSD-46617 para resolver o problema do Adobe Commerce em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que a quantidade mínima de pedido configurada.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: botão &quot;[!UICONTROL Continue to Checkout]&quot; esmaecido quando um subtotal maior que &quot;[!UICONTROL Minimum Order Amount]&quot;

Este patch ACSD-46617 resolve o problema em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o valor mínimo de pedido configurado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-46617. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O botão **[!UICONTROL Continue to Checkout]** ficará esmaecido mesmo se o subtotal for maior que o valor mínimo de pedido configurado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e defina o seguinte:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;
     [!UICONTROL Minimum Amount]: *2*

1. Criar um [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Crie um produto com o preço de US$ 25.
1. Adicione o produto ao carrinho.
1. Vá para o carrinho de compras, selecione o método $5 **[!UICONTROL Flat Rate shipping]** e aplique o código do cupom.
1. Acesse o check-out, conclua o envio e navegue até a seção **[!UICONTROL Paytment]**.
1. Volte para o carrinho de compras.

<u>Resultados esperados</u>:

Não há erro relacionado ao valor mínimo do pedido, pois o total geral de US$ 2,4 é maior que o valor necessário de US$ 2.

<u>Resultados reais</u>:

* Há um erro relacionado ao valor mínimo do pedido mesmo quando o total geral de US$ 2,4 é maior que o valor mínimo do pedido de US$ 2.
* O botão **[!UICONTROL Continue to Checkout]** está esmaecido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
