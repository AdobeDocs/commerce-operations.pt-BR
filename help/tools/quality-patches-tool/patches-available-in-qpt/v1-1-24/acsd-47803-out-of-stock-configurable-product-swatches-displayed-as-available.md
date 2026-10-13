---
title: 'ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis'
description: Aplique o patch ACSD-47803 para corrigir o problema do Adobe Commerce em que as amostras de produto configuráveis e indisponíveis são exibidas como disponíveis.
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%
---
# ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis

O patch ACSD-47803 corrige o problema em que amostras de produtos configuráveis e indisponíveis são exibidas como disponíveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. A ID do patch é ACSD-47803. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
