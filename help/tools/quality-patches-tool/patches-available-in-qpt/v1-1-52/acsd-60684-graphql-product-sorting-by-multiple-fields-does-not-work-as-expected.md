---
title: 'ACSD-60684: a classificação de produto [!DNL GraphQL] por vários campos não funciona conforme esperado'
description: Aplique o patch ACSD-60684 para corrigir o problema do Adobe Commerce em que a classificação de produto [!DNL GraphQL] por vários campos não funciona quando a classificação é passada em variáveis.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 1c29299b-c85f-4166-886b-357a1486e67e
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
source-wordcount: '322'
ht-degree: 0%
---
# ACSD-60684: a classificação de produto [!DNL GraphQL] por vários campos não funciona conforme esperado

O patch ACSD-60684 corrige o problema em que a classificação de produto [!DNL GraphQL] por vários campos não funciona quando a classificação é passada em variáveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 está instalado. A ID do patch é ACSD-60684. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classificação de produtos [!DNL GraphQL] por vários campos não funciona conforme esperado.

<u>Etapas a serem reproduzidas</u>:

1. Crie três produtos com os nomes A, B e C.
1. Buscar os produtos usando o seguinte [!DNL GraphQL]:

   ```graphql
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   Variáveis:

   ```json
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. Repetir a consulta com `sort` : `DESC`

<u>Resultados esperados</u>:

Os resultados são classificados adequadamente.

<u>Resultados reais</u>:

A classificação selecionada não foi aplicada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
