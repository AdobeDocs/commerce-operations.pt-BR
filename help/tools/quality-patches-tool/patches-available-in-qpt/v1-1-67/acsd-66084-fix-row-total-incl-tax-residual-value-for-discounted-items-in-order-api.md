---
title: 'ACSD-66084: "row_total_incl_tax" retorna perto de zero em vez de 0,00 para itens totalmente descontados na API da ordem'
description: Aplique o patch ACSD-66084 para corrigir o problema do Adobe Commerce em que "row_total_incl_tax" retornou como um valor residual próximo de zero em vez de 0,00 para itens totalmente descontados na resposta da API do pedido.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%
---
# ACSD-66084: `row_total_incl_tax` retorna quase zero em vez de 0,00 para itens totalmente descontados na API de ordem

O patch ACSD-66084 corrige o problema em que `row_total_incl_tax` é retornado como um valor residual quase zero na resposta da API do pedido em vez de 0,00 para itens totalmente descontados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66084. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O `row_total_incl_tax` é retornado como um valor residual quase zero na resposta da API do pedido em vez de 0,00 para itens totalmente descontados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com um preço e um preço especial. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Clique em **[!UICONTROL Add Product]** > defina **[!UICONTROL Price]** como $25 e **[!UICONTROL Special Price]** como $16.99 em **[!UICONTROL Advanced Pricing]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** e adicione uma taxa de 20%. Em seguida, vá para **[!UICONTROL Tax Rules]**, crie uma regra e atribua
   **[!UICONTROL Taxable Goods]** como a classe de imposto do produto.
1. Crie uma regra de vendas com um desconto de 100% e um cupom. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**, adicione uma regra com um desconto de 100% e use **[!UICONTROL Specific Coupon]** e insira seu código.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > e defina as configurações de imposto.
1. Ativar frete gratuito. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. Defina **[!UICONTROL Enabled]** como **[!UICONTROL Yes]** e ajuste as configurações.
1. Vá para a página do produto e selecione **[!UICONTROL Add to Cart]**. Vá para o carrinho de compras e aplique o código do cupom.
1. Coloque o pedido na zona de imposto aplicável.
1. Gerar um token de administrador (API) por meio da API REST.
1. Recupere detalhes do pedido por meio da API REST.
1. Verifique `row_total_incl_tax` na resposta.

<u>Resultados esperados</u>:

`row_total_incl_tax` deve retornar um valor apropriado para a moeda como `0.00` quando o item for totalmente descontado.

<u>Resultados reais</u>:

`row_total_incl_tax` retorna um valor de ponto flutuante próximo a zero, como `3.5527136788005e-15`, que não é apropriado para exibição de moeda.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
