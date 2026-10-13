---
title: 'ACSD-48044: a aplicação de vários cartões-presente impede que os pedidos sejam feitos'
description: Aplique o patch ACSD-48044 para corrigir o problema do Adobe Commerce, onde a aplicação de vários cartões-presente a um único pedido com vários envios impede que os pedidos sejam feitos.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%
---
# ACSD-48044: a aplicação de vários cartões-presente impede que os pedidos sejam feitos

O patch ACSD-48044 corrige o problema em que a aplicação de vários cartões-presente a um único pedido com vários envios impede que os pedidos sejam feitos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. A ID do patch é ACSD-48044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Aplicar vários cartões-presente a um único pedido com remessa múltipla impede que os pedidos sejam feitos.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma versão limpa do Adobe Commerce.
1. Crie um produto simples com um preço de $100 e outro produto simples com um preço de $10.
1. Faça logon no [!UICONTROL Admin panel] e crie dois cartões-presente.

   * 02KB8M0H0GRD = US$ 50
   * 00GXM6SUGBLW = US$ 25

1. Crie um cliente com dois endereços.
1. Adicione dois produtos ao carrinho.

   * Adicione o produto de US$ 10 primeiro e, em seguida, adicione o produto de US$ 100. O problema não pode ser reproduzido se o produto de US$ 100 for adicionado primeiro.

1. Vá para o carrinho de compras e adicione os dois cartões-presente que você criou.
1. Clique em **[!UICONTROL Ship to Multiple Addresses]** na página do carrinho.
1. Atribua cada produto a um endereço diferente.
1. Vá para a página **[!UICONTROL Shipping information]**.
1. Vá para a página **[!UICONTROL Billing information]**.
1. Vá para a página **[!UICONTROL Review Your Order]**, onde você pode ver o problema.
1. Tente fazer o pedido.

<u>Resultados esperados</u>:

* Os cartões-presente são aplicados corretamente ao valor total.
* Os pedidos são feitos.

<u>Resultados reais</u>:

Os valores do cartão-presente estão misturados com um erro *&quot;Corrija o código do cartão-presente.&quot;* ao fazer o pedido.

* Primeiro produto:

  * Remover Cartão Presente (00GXM6SUGBLW) - $15,00
  * Remover Cartão Presente (02KB8M0H0GRD) - $0,00

* Segundo produto:

  * Remover Cartão Presente (00GXM6SUGBLW) - $25,00
  * Remover Cartão Presente (02KB8M0H0GRD) - $35,00

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
