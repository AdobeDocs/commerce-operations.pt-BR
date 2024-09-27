---
title: "ACSD-45071: origem padrão adicionada ao produto durante a importação"
description: O patch ACSD-45071 resolve o problema em que a origem padrão é adicionada ao produto durante a importação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 é instalado. A ID do patch é ACSD-45071. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Data Import/Export, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-45071: origem padrão adicionada ao produto durante a importação

O patch ACSD-45071 resolve o problema em que a origem padrão é adicionada ao produto durante a importação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 está instalado. A ID do patch é ACSD-45071. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Após uma importação de produto, a origem padrão é atribuída automaticamente ao produto, a quantidade é definida como zero e o status é definido como esgotado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova fonte.
1. Crie um novo estoque usando a nova fonte.
1. Na página de edição do produto no Adobe Commerce Admin, atribua somente o estoque personalizado, defina uma quantidade e o status do estoque como **[!UICONTROL In Stock]**.
1. Importar o produto via **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.

<u>Resultados esperados</u>:

A origem padrão não é atribuída automaticamente ao produto após a importação.

<u>Resultados reais</u>:

A origem padrão é atribuída ao produto após a importação com status de indisponível e quantidade zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
