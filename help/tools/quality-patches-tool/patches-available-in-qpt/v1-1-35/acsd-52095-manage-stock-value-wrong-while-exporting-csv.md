---
title: 'ACSD-52095: o gerenciamento do valor de estoque está incorreto ao exportar CSV'
description: Aplique o patch ACSD-52095 para corrigir o problema do Adobe Commerce em que o valor do estoque de gerenciamento de produtos está incorreto ao exportar CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095: valor [!UICONTROL Manage Stock] incorreto ao exportar CSV

O patch ACSD-52095 corrige o problema em que o valor do produto `manage_stock` está errado ao exportar CSV. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52095. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor `manage_stock` está incorretamente definido como 0 no arquivo CSV após a exportação do produto.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e defina **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Crie um novo produto e salve.
1. Vá para **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Selecione *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* e exporte os produtos.
1. Verifique o arquivo CSV gerado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Novamente vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e defina **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Ir para **Sistema** > **Exportar**.
Selecione *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Verifique o arquivo CSV gerado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Abra o produto no Administrador, vá para **[!UICONTROL Advanced Inventory]** e verifique o valor de **[!UICONTROL Manage Stock]**.

<u>Resultados esperados</u>

O valor **[!UICONTROL Manage Stock]** é *1* quando está habilitado para os produtos.

<u>Resultados reais</u>

O valor **[!UICONTROL Manage Stock]** é *0* quando está habilitado para os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
