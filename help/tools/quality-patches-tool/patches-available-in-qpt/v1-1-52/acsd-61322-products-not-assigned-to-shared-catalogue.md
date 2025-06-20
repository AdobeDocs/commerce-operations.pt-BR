---
title: 'ACSD-61322: Os produtos não atribuídos a [!UICONTROL Shared Catalogue] estão incluídos no Mapa de Site XML'
description: Aplique o patch ACSD-61322 para corrigir o problema do Adobe Commerce em que produtos/categorias não atribuídos ao [!UICONTROL Shared Catalog] para o grupo Padrão (Geral) ainda estão incluídos no Mapa do Site XML.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: Os produtos não atribuídos a [!UICONTROL Shared Catalogue] estão incluídos no Mapa de Site XML

O patch ACSD-61322 corrige o problema em que produtos/categorias não atribuídos ao [!UICONTROL Shared Catalog] para o grupo Padrão (Geral) ainda estão incluídos no Mapa do Site XML. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-61322. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Produtos/categorias não atribuídos ao [!UICONTROL Shared Catalog] para o grupo Padrão (Geral) ainda estão incluídos no Mapa de Site XML.

<u>Etapas a serem reproduzidas</u>:

1. Crie algumas categorias e adicione produtos (por exemplo, Categoria 1 com Categoria 2).
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e habilite *[!UICONTROL Company and Shared Catalog]*.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e modifique o Catálogo Padrão.
1. Na lista suspensa **[!UICONTROL Select]**, selecione **[!UICONTROL Set Pricing and Structure]** e clique em **[!UICONTROL Configure]**.
1. Na categoria *Categoria 1 > Categoria 2*, desmarque alguns produtos que não devem estar na [!UICONTROL Shared Catalog].
1. Clique em **[!UICONTROL Next]** e gere o catálogo.
1. Na Loja, crie uma conta de cliente.
1. Vá para a categoria *Categoria 1 > Categoria 2*. Ele exibe somente os produtos que foram atribuídos a [!UICONTROL Shared Catalog].
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** e gere um novo mapa de site.
1. Abra o `sitemap.xml` na Loja.
1. Pesquise os produtos que você não incluiu no [!UICONTROL Shared Catalog].

<u>Resultados esperados</u>:

O mapa de site não contém links para produtos e categorias que não estão atribuídos ao [!UICONTROL Shared Catalog].

<u>Resultados reais</u>:

O mapa de site contém links para produtos e categorias que não estão atribuídos a [!UICONTROL Shared Catalog].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
