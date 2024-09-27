---
title: "ACSD-57854: a resposta *GraphQL* contém categorias desabilitadas que não devem ser listadas nas agregações de categoria"
description: Aplique o patch ACSD-57854 para corrigir o problema do Adobe Commerce em que a resposta *GraphQL* contém categorias desativadas que não devem ser listadas nas agregações de categorias.
feature: GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57854: A resposta *GraphQL* contém categorias desabilitadas que não devem ser listadas nas agregações de categorias

O patch ACSD-57854 corrige o problema em que a resposta do *GraphQL* contém categorias desabilitadas que não devem ser listadas nas agregações de categorias. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. A ID do patch é ACSD-57854. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A resposta do *GraphQL* contém categorias desabilitadas que não devem ser listadas nas agregações de categorias.

<u>Etapas a serem reproduzidas</u>:

1. Crie duas categorias.
1. Crie um produto (Produto de Adobe de teste) e atribua o produto a ambas as categorias.
1. Desative uma das categorias criadas.
1. Use os produtos *GraphQL* para pesquisar o produto.
1. Verifique a lista de categorias de produtos na resposta do *GraphQL*.

<u>Resultados esperados</u>:

As categorias desabilitadas não estão listadas na resposta *GraphQL*.

<u>Resultados reais</u>:

As categorias desabilitadas estão listadas na resposta da agregação de categorias *GraphQL*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
