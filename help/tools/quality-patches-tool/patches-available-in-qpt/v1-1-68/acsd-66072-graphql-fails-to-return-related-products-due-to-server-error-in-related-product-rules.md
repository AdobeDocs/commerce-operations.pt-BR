---
title: 'ACSD-66072: a GraphQL não retorna produtos relacionados na Página de detalhes do produto'
description: Aplique o patch ACSD-66072 para corrigir o problema do Adobe Commerce em que os produtos relacionados não são retornados por meio do GraphQL na Página de detalhes do produto devido a um erro interno do servidor quando as Regras de produto relacionadas são configuradas.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
exl-id: a706a710-aed3-41a4-bc87-3150e9ba95f7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '409'
ht-degree: 7%
---
# ACSD-66072: a GraphQL não retorna produtos relacionados na Página de detalhes do produto

O patch ACSD-66072 corrige o problema em que os produtos relacionados não são retornados via GraphQL na Página de Detalhes do Produto devido a um erro interno do servidor quando o **[!UICONTROL Related Products Rule]** é configurado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66072. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos relacionados não são retornados via GraphQL na Página de Detalhes do Produto devido a um erro interno do servidor quando o **[!UICONTROL Related Products Rule]** é configurado.

<u>Etapas a serem reproduzidas</u>:

1. Crie produtos configuráveis:
   * **Produto 1**: `config1` com `option1`
   * **Produto 2**: `config2` com `option2`

1. Criar e atribuir produtos a uma categoria
   * Criar uma **nova categoria**.
   * Atribuir ambos os produtos (`config1` e `config2`) a esta categoria.

1. Navegue até **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]** e crie uma nova regra com as seguintes configurações:

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. Execute os seguintes comandos da CLI da Magento:

   ```shell
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. Envie uma solicitação POST para `../graphql` com a seguinte carga:

   ```graphql
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>Resultados esperados</u>:

A consulta retorna o produto relacionado (`config1`).

<u>Resultados reais</u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

O arquivo `var/log/exception.log` contém:

```text
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
