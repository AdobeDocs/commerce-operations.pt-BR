---
title: "ACSD-48262: produtos não visíveis na loja quando [!UICONTROL Allow All Products Per Page] está definido como [!UICONTROL Yes]"
description: Aplique o patch ACSD-48262 para corrigir o problema do Adobe Commerce em que os produtos não estão visíveis na loja quando a configuração [!UICONTROL Allow All Products Per Page] está definida como [!UICONTROL Yes].
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262: produtos não visíveis na loja quando [!UICONTROL Allow All Products Per Page] está definido como *[!UICONTROL Yes]*

O patch ACSD-48262 corrige o problema em que os produtos não estão visíveis na loja quando a configuração [!UICONTROL Allow All Products Per Page] está definida como *[!UICONTROL Yes]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-48262. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch ACSD-48262 corrige o problema em que os produtos não estão visíveis na loja quando a configuração [!UICONTROL Allow All Products Per Page] está definida como *[!UICONTROL Yes]*.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma categoria de teste.
1. Criar um produto de teste na categoria de teste.
1. Navegue pelo produto para testar a página de categorias na loja e verifique se o produto está visível.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** e defina a configuração [!UICONTROL Allow All Products Per Page] como *[!UICONTROL Yes]*.
1. Limpar cache.
1. Verifique a página de categoria na loja.

<u>Resultados esperados</u>:

O produto está visível.

<u>Resultados reais</u>:

O produto não está visível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
