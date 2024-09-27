---
title: "ACSD-51497: não é possível classificar a página de catálogo pelo atributo personalizado do tipo Suspenso"
description: Aplique o patch ACSD-51497 para corrigir o problema do Adobe Commerce em que um cliente não pode classificar uma página de catálogo pelo atributo personalizado do tipo Suspenso.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497: Não é possível classificar a página de catálogo pelo atributo personalizado do tipo *Suspenso*

O patch ACSD-51497 corrige o problema em que um cliente não consegue classificar uma página de catálogo por um atributo personalizado do tipo *Suspensão*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-51497. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

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

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
