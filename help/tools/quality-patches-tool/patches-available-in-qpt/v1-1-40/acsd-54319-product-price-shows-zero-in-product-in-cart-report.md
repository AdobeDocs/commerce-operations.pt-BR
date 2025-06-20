---
title: 'ACSD-54319: o preço do produto mostra zero no relatório *[!UICONTROL Products in Carts]*'
description: Aplicar o patch ACSD-54319 para corrigir o problema do Adobe Commerce em que o preço do produto mostra zero no relatório *[!UICONTROL Products in Carts]*
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319: o preço do produto mostra zero no relatório *[!UICONTROL Products in Carts]*

O patch ACSD-54319 corrige o problema em que o preço do produto mostra zero no relatório *[!UICONTROL Products in Carts]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 está instalado. A ID do patch é ACSD-54319. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço do produto mostra zero no relatório *[!UICONTROL Products in Carts]*.

<u>Etapas a serem reproduzidas</u>:

1. Defina **[!UICONTROL Catalog Price Scope]** como **[!UICONTROL Website]** de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Crie um segundo site de **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Crie um produto a partir de **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Atribua este produto somente ao segundo site.
1. Adicione um produto ao carrinho a partir do segundo site.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > grade **[!UICONTROL Products In Carts]**.
1. Verifique a coluna *[!UICONTROL Price]* na grade *[!UICONTROL Products In Carts]*.

<u>Resultados esperados</u>:

O preço do produto não é zero na grade de relatório *[!UICONTROL Products in Carts]*.

<u>Resultados reais</u>:

O preço do produto é zero na grade de relatório *[!UICONTROL Products in Carts]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
