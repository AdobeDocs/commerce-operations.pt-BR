---
title: 'ACSD-51497: não é possível classificar a página de catálogo pelo atributo personalizado do tipo Suspenso'
description: Aplique o patch ACSD-51497 para corrigir o problema do Adobe Commerce em que um cliente não pode classificar uma página de catálogo pelo atributo personalizado do tipo Suspenso.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%
---
# ACSD-51497: Não é possível classificar a página de catálogo pelo atributo personalizado do tipo *Suspenso*

O patch ACSD-51497 corrige o problema em que um cliente não consegue classificar uma página de catálogo por um atributo personalizado do tipo *Suspensão*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. A ID do patch é ACSD-51497. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um cliente não pode classificar uma página de catálogo por um atributo personalizado do tipo *Lista suspensa*.

<u>Etapas a serem reproduzidas</u>

1. Crie cerca de seis produtos simples e atribua-os a uma única categoria.
1. Crie um atributo de produto para adicioná-lo como uma opção de classificação nas páginas de listagem.

   * Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Na guia **[!UICONTROL Properties]**, defina o seguinte:

     * *[!UICONTROL Default Label]* = *teste*
     * *[!UICONTROL Catalog Input Type]* para Proprietário da Loja = *Lista Suspensa*
     * *[!UICONTROL Options]*:

       * *primeiro*
       * *segundo*
       * *terço*
       * *quarto*

   * Na guia **[!UICONTROL Storefront Properties]**, defina o seguinte:

     * *[!UICONTROL Used for sorting in product listing]* = *Sim*
     * Deixe todas as outras opções como *Padrão*.

1. Atribua o atributo *test* ao atributo *Padrão* definido em **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Configure os produtos para terem valores de atributo de *teste*.

   * SKU: s00001, teste: quarto
   * SKU: s00002, teste: terceiro
   * SKU: s00003, teste: segundo
   * SKU: s00004, teste: primeiro
   * SKU: s00005, teste: quarto
   * SKU: s00006, teste: terceiro

1. Reindexe e limpe o cache.
1. Vá para a categoria na loja.
1. Classificar pelo atributo *test*.

<u>Resultados esperados</u>:

Os produtos estão classificados pelo atributo *test*.

<u>Resultados reais</u>:

Os produtos não estão classificados pelo atributo *test*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
