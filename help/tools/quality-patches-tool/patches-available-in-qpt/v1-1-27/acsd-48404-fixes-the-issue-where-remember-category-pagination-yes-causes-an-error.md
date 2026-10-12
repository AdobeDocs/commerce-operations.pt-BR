---
title: 'ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa erro ao pressionar o botão Voltar do navegador'
description: Aplique o patch ACSD-48404 para corrigir o problema do Adobe Commerce em que *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador.
feature: Categories
role: Admin
exl-id: 8c08f0e2-d4f9-4ac8-b8e8-85b4a7de98fb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%
---
# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa erro ao pressionar o botão Voltar do navegador

O patch ACSD-48404 corrige o problema em que *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-48404. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador.


<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** e defina *[!UICONTROL Remember Category Pagination]* como *Sim*.
1. Abra uma categoria na loja.
1. Selecione um valor que não seja o valor padrão na lista suspensa *[!UICONTROL Show Per Page]*. Após selecionar uma opção, a página é recarregada.
1. Depois que a página for recarregada, clique em qualquer produto na página do catálogo.
1. Na página de detalhes do produto aberta, clique no botão **[!UICONTROL Back]** do navegador.

<u>Resultados esperados</u>:

A página do catálogo é aberta novamente.

<u>Resultados reais</u>:

A página de categoria retorna um erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
