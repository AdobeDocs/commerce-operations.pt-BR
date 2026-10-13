---
title: 'ACSD-55100: [!DNL GraphQL] não retorna produtos acima de 10k nos resultados da pesquisa'
description: Aplique o patch ACSD-55100 para corrigir o problema do Adobe Commerce em que a GraphQL não retorna produtos além de *10k* nos resultados da pesquisa.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%
---
# ACSD-55100: [!DNL GraphQL] não retorna produtos acima de 10k nos resultados da pesquisa

>[!NOTE]
>
>Um patch atualizado ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) foi lançado para resolver o mesmo problema para as versões 2.4.6 - 2.4.6-p8. Para obter mais detalhes, consulte [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

O patch ACSD-55100 corrige o problema em que [!DNL GraphQL] não retorna produtos além de *10k* nos resultados da pesquisa. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. A ID do patch é ACSD-55100. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL GraphQL] não retorna produtos além de *10k* nos resultados da pesquisa.

<u>Pré-requisitos</u>:

No caso de **[!DNL OpenSearch]**, verifique se você está usando a versão mais recente disponível.

Para resolver o problema relatado, a funcionalidade Ponto no Tempo foi introduzida, disponível após **[!DNL OpenSearch]** 2.5.0 e requer a versão 2.2 do pacote `opensearch-project/opensearch-php`.

No entanto, há um conflito com `magento/magento-cloud-metapackage`, que especifica uma dependência no pacote `opensearch-project/opensearch-php` que deve ser menor que a versão 2.0.1.


Esta dependência impede a atualização do pacote [opensearch-project/opensearch-php] para a versão 2.2 mais recente.

Como resultado, o sistema encontra o seguinte erro e retorna resultados nulos para produtos que excedem *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

A dependência existente torna desafiador adicionar diretamente uma versão ao arquivo `composer.json` e atualizar o pacote `opensearch-project/opensearch-php` para a versão 2.2.

Para resolver o problema, inclua a seguinte linha no arquivo `composer.json` principal no bloco obrigatório. Depois, reimplante para atualizar o pacote problemático para a versão mais recente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Etapas a serem reproduzidas</u>:

1. Gerar o catálogo com *15k* produtos.
1. Enviar o [!DNL GraphQL]:

```graphql
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

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

Total_count = *15k*
Você poderá mostrar todos os produtos.

<u>Resultados reais</u>:

Total_count = *10k*
Não é possível exibir mais nenhum produto após o lote *10k*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
