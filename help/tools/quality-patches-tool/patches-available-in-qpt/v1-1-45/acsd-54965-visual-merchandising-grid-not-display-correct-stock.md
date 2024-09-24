---
title: "ACSD-54965: a grade [!UICONTROL Visual Merchandising] não exibe o estoque correto"
description: Aplique o patch ACSD-54965 para corrigir o problema do Adobe Commerce em que a grade [!UICONTROL Visual Merchandising] não exibe o estoque correto quando um produto é atribuído ao estoque personalizado.
feature: Merchandising, Categories
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: a grade [!UICONTROL Visual Merchandising] não exibe o estoque correto

O patch ACSD-54965 corrige o problema em que a grade [!UICONTROL Visual Merchandising] não exibe o estoque correto quando um produto é atribuído ao estoque personalizado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 está instalado. A ID do patch é ACSD-54965. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A grade [!UICONTROL Visual Merchandising] não exibe o estoque correto quando um produto é atribuído ao estoque personalizado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova fonte.
1. Criar um novo estoque.
1. Crie dois produtos:
   * Um produto somente com o estoque personalizado.
   * Um produto somente com o estoque padrão.
1. Adicionar esses produtos a uma categoria.
1. Vá para a grade [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Resultados Reais</u>:

Nos escopos *[!UICONTROL All Store Views]*, o produto com estoque personalizado não mostra nenhuma quantidade. É somente quando o escopo *[!UICONTROL Default Store View]* é selecionado que o estoque personalizado mostra a quantidade do produto.

<u>Resultados Esperados</u>:

A grade mostra todas as informações de estoque se o escopo for *[!UICONTROL All Store Views]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
