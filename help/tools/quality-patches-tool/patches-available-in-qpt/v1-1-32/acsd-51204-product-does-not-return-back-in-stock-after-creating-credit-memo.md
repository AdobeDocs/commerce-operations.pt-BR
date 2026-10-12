---
title: 'ACSD-51204: o produto não retorna ao estoque após criar o memorando de crédito'
description: Aplique o patch ACSD-51204 para corrigir o problema do Adobe Commerce em que o produto não retorna ao estoque após criar o memorando de crédito.
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-51204: o produto não retorna ao estoque após criar o memorando de crédito

O patch ACSD-51204 corrige o problema em que o produto não retorna ao estoque após criar o memorando de crédito. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. A ID do patch é ACSD-51204. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto esgotado não retorna em estoque após a criação do memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Instale o **[!UICONTROL Adobe Commerce]** e habilite o **[!UICONTROL Inventory Management Module]** somente com a *origem* e o *estoque* padrão.
1. Adicione um **[!UICONTROL new product]** com uma quantidade de *10*.
1. Atribua o produto a **[!UICONTROL default stock]**.
1. Na Loja, adicione o produto ao carrinho e faça o pedido de uma quantidade total disponível de 10.
1. No painel de administração, gere uma *fatura* e uma *remessa* para o pedido.
1. Crie um **[!UICONTROL Credit Memo]** com a caixa de seleção *retornar ao estoque* marcada para todos os itens.
1. Verifique o **[!UICONTROL Salable Quantity]** do produto no Administrador.

<u>Resultados esperados</u>:

A quantidade comercializável do produto deve retornar para *10*.

<u>Resultados reais</u>:

A quantidade vendável do produto é deixada como *0*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
