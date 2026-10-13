---
title: 'ACSD-49480: descartar regras subsequentes que não estejam funcionando'
description: Aplique o patch ACSD-49480 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado.
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%
---
# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado

O patch ACSD-49480 corrige o problema em que o [!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-49480. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] não está funcionando como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um **[!UICONTROL Cart Price Rule]** com um código de cupom (nomeie-o como *TEST*) que concede um desconto de US$10 à *ID do Produto 1* na guia **[!UICONTROL Actions]** com [!UICONTROL Discard Subsequent Rules] definido como *[!UICONTROL Yes]* e [!UICONTROL Priority] definido como *1*.
1. Crie outro **[!UICONTROL Cart Price Rule]** sem um código de cupom que dê um desconto de $5 para *ID do Produto 2* na guia **[!UICONTROL Actions]** com [!UICONTROL Priority] definido como *2*. Aqui, supomos que esta é uma venda global para *ID do Produto 2*.
1. Vá para o site de front-end e adicione a *ID do Produto 1* e a *ID do Produto 2* ao carrinho.
1. Aplicar o código de cupom *TEST*.

<u>Resultados esperados</u>

* *O desconto 1* é aplicado à *ID do Produto 1*.
* *O desconto 2* é aplicado à *ID do Produto 2*.

<u>Resultados reais</u>

* Somente *O desconto 1* é aplicado à *ID do Produto 1*.
* *O desconto 2* não foi aplicado à *ID do Produto 2*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
