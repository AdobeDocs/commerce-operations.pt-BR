---
title: 'ACSD-63062: cálculos de desconto de carrinho incorretos com várias regras de sobreposição'
description: Aplique o patch ACSD-63062 para corrigir o problema do Adobe Commerce em que cálculos incorretos de desconto do carrinho ocorrem quando várias regras de sobreposição são aplicadas.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: cálculos de desconto de carrinho incorretos com várias regras de sobreposição

O patch ACSD-63062 corrige o problema em que cálculos incorretos de desconto do carrinho ocorrem quando várias regras de sobreposição são aplicadas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-63062. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Cálculos incorretos de desconto do carrinho ocorrem quando várias regras de sobreposição são aplicadas.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma nova instância com dados de amostra.
1. Crie três produtos simples:

   * simples1: US$ 1.080
   * simples2: US$ 260
   * simples3: US$ 280

1. Crie quatro *[!UICONTROL Cart Price Rules]* da seguinte maneira:

   * Regra 1:

      * *[!UICONTROL Priority]*: 100
      * Guia *[!UICONTROL Conditions]*: usar produto simple2 ($280) se a quantidade total for igual ou maior que 3
      * Guia *[!UICONTROL Actions]*: SKU é simples2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regra 2:

      * *[!UICONTROL Priority]*: 200
      * Guia *[!UICONTROL Actions]*: SKU é simples2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * Regra 3:

      * *[!UICONTROL Priority]*: 300
      * Guia *[!UICONTROL Conditions]*: Subtotal igual ou maior que $1000
      * *[!UICONTROL Fixed Amount Discount]* para todo o carrinho: $100

   * Regra 4:

      * *[!UICONTROL Priority]*: 400
      * Guia *[!UICONTROL Conditions]*: usar produto simple1 ($1080) se a quantidade total for igual ou maior que 2
      * Guia *[!UICONTROL Actions]*: SKU é simples1
      * *[!UICONTROL Fixed Amount Discount]* para todo o carrinho: $960

1. Vá para a loja e adicione os seguintes produtos com determinada quantidade no carrinho:

   * simples1 = 2
   * simples2 = 1
   * simples3 = 3

1. Verifique o carrinho de compras.

<u>Resultados esperados</u>:

O desconto aplicado é de US$ 1352.

<u>Resultados reais</u>:

O desconto aplicado é de US$ 1525,33.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
