---
title: 'ACSD-50260: os resultados da pesquisa de produtos do GraphQL são limitados'
description: Aplique o patch ACSD-50260 para corrigir o problema do Adobe Commerce, em que os resultados da pesquisa de produto do GraphQL são limitados a apenas 10.000 resultados.
feature: Admin Workspace, Categories, GraphQL, Products, Search
role: Admin
exl-id: a9099fab-226d-439b-b2d0-f354d6b5638f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-50260: os resultados da pesquisa de produtos do GraphQL são limitados

O patch ACSD-50260 corrige o problema em que os resultados da pesquisa de produtos do GraphQL são limitados a apenas 10.000 resultados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-50260. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os resultados da pesquisa de produtos do GraphQL são limitados a apenas 10.000 resultados.

<u>Etapas a serem reproduzidas</u>:

1. Gerar *[!UICONTROL 15,000 products]* em uma categoria.
1. Consulte essa categoria com a solicitação do GraphQL anexada abaixo:

```GraphQL
{
  products(
    filter: { category_id: { eq: "{CATEGORY_ID}" } }
    pageSize: 5
    currentPage: 1
  ) {
    total_count
    page_info {
      current_page
      page_size
      total_pages
    }

    aggregations {
      attribute_code
      count
      label
      options {
        label
        value
      }
    }

    items {
      uid
      sku
      is_for_clearance
      categories {
        name
        breadcrumbs {
          category_name
          category_uid
        }
        display_mode
        description
      }
    }
  }
}
```

<u>Resultados esperados</u>:

`total_count = 15k`

Possibilidade de obter todos os produtos nos resultados da pesquisa.

<u>Resultados reais</u>:

`total_count = 10k`

Não é possível obter produtos após esse lote de 10 mil nos resultados da pesquisa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
