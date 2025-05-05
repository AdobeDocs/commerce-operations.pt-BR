---
title: 'ACSD-46519: [!UICONTROL product_count] em [!UICONTROL categoryList] [!DNL GraphQL] a consulta retorna 0 para categorias de âncora'
description: Aplique o patch ACSD-46519 para corrigir o problema do Adobe Commerce em que, ao usar o método [!UICONTROL categoryList] [!DNL GraphQL]  para obter categorias secundárias, ele mostra [!UICONTROL product_count] como 0 para categorias principais.
feature: Categories, GraphQL, Products
role: Admin
exl-id: 7becaa4e-421a-4983-ac73-f5b58fc45d8f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46519: [!UICONTROL product_count] em [!UICONTROL categoryList] [!DNL GraphQL], a consulta retorna 0 para categorias de âncora

O patch ACSD-46519 resolve o problema em que [!UICONTROL product_count] em [!UICONTROL categoryList] [!DNL GraphQL] query retorna 0 para categorias de âncora. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 está instalado. A ID do patch é ACSD-46519. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o método [!UICONTROL categoryList] [!DNL GraphQL] é usado para obter categorias filho, ele mostra [!UICONTROL product_count] como 0 para categorias pai.

<u>Etapas a serem reproduzidas</u>:

1. Use a seguinte solicitação [!DNL GraphQL] para obter a hierarquia de categoria com [!UICONTROL product_count]:

<pre><code>
&lbrace;
  categoryList(filters: { ids: { eq: "2" } }) &lbrace;
    id
    name
    product_count
    level
    children &lbrace;
      name
      product_count
      level
      children &lbrace;
        name
        product_count
        level
        children &lbrace;
          name
          product_count
          level
          children &lbrace;
            name
            product_count
            level
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code></pre>

<u>Resultados esperados</u>:

Se a categoria principal for uma categoria ancorada, o [!UICONTROL product_count] deverá mostrar a soma das contagens de produtos da categoria secundária em cada nível.

<u>Resultados reais</u>:

Se a categoria principal for uma categoria ancorada, os produtos serão exibidos como 0 para a categoria de nível 2 e abaixo.

<pre><code>
&lbrace;
    "data": &lbrace;
        "categoryList": &lbrack;
            &lbrace;
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": &lbrack;
                    &lbrace;
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    &rbrace;,
                    &lbrace;
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": &lbrack;
                            &lbrace;
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;,
                            &lbrace;
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;
                        &rbrack;
                    &rbrace;,
                    ...
                &rbrack;
            &rbrace;
        &rbrack;
    &rbrace;
&rbrace;
</code></pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
