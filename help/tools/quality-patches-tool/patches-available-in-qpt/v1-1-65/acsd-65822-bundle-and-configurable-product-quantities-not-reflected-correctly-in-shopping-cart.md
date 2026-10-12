---
title: 'ACSD-65822: Quantidades de pacote e produto configuráveis não refletidas corretamente no carrinho de compras'
description: Aplique o patch ACSD-65822 para corrigir o problema do Adobe Commerce em que a quantidade aparecia como 0 na seção carrinho de compras do cliente no painel de administração ao adicionar produtos do pacote.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-65822: Quantidades de pacote e produto configuráveis não refletidas corretamente no [!UICONTROL Shopping Cart]

O patch ACSD-65822 corrige o problema em que as quantidades de pacote e de produto configuráveis não são exibidas corretamente na seção **[!UICONTROL Shopping Cart]** em *[!UICONTROL Customer's Activities]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-65822. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As quantidades do pacote e do produto configurável não são exibidas corretamente na seção **[!UICONTROL Shopping Cart]** em *[!UICONTROL Customer's Activities]*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um usuário na loja.
2. Crie um **[!UICONTROL Bundle product]** no painel de administração.
3. Na loja, como usuário conectado, adicione o produto incluído ao carrinho com uma quantidade especificada.
4. No painel *Admin*, vá para **[!UICONTROL Customers]** e clique em **[!UICONTROL Edit]** para o cliente criado na Etapa 1.
5. Clique em **[!UICONTROL Create Order]**.
6. No lado esquerdo, em *[!UICONTROL Customer's Activities]*, verifique a seção **[!UICONTROL Shopping Cart]**. Você deve ver o produto do pacote junto com a quantidade selecionada.

<u>Resultados esperados</u>:

A quantidade do item do pacote deve corresponder à quantidade mostrada na loja.

<u>Resultados reais</u>:

A quantidade do item do pacote é exibida como 0.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
