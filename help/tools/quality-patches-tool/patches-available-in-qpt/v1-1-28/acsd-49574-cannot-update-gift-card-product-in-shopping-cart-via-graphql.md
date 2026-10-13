---
title: 'ACSD-49574: não é possível atualizar o produto de cartão-presente no carrinho de compras via GraphQL'
description: Aplique o patch ACSD-49574 para corrigir o problema do Adobe Commerce em que um produto de cartão-presente não pode ser atualizado no carrinho de compras via GraphQL.
feature: Admin Workspace, Gift, GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 31dede84-3733-4481-b21d-526494eb8e9b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-49574: não é possível atualizar o produto de cartão-presente no carrinho de compras via GraphQL

O patch ACSD-49574 corrige o problema em que um produto de cartão-presente não pode ser atualizado no carrinho de compras via GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. A ID do patch é ACSD-49574. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um produto de cartão-presente não pode ser atualizado no carrinho de compras via GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto de cartão-presente.
1. Adicione o produto de cartão-presente ao carrinho via GraphQL.
1. Tente atualizar os campos de produto de cartão-presente no carrinho via GraphQL usando a mutação `updateCartItems`.

   Exemplo de uso do GraphQL:

   ```GraphQL
   mutation ($cartId: String!, $cartItems: [CartItemUpdateInput!]!){
       updateCartItems(
           input: {
               cart_id: $cartId,
               cart_items: $cartItems
           }
       )   {
           cart {
               id
               items {
                   uid
                   quantity
                   product {
                       sku
                   }
                   ... on GiftCardCartItem {
                       sender_name
                       sender_email
                       recipient_name
                       recipient_email
                       message
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   
   variables
   {
       "cartId": "sDrOu06VYlGejhDivQMcnmcNPSxTMUDd",
       "cartItems": [
           {
               "cart_item_id": 113,
               "quantity": 1,
               "customizable_options": [{
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX25hbWU=",
                       "value_string": "sender_name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX2VtYWls",
                       "value_string": "sender_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X25hbWU=",
                       "value_string": "recipient name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X2VtYWls",
                       "value_string": "recipient_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfbWVzc2FnZQ==",
                       "value_string": "message"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvY3VzdG9tX2dpZnRjYXJkX2Ftb3VudA==",
                       "value_string": "10"
                   }
               ]
           }]
   }
   ```

<u>Resultados esperados</u>:

Todos os campos de produto de cartão-presente (sender_name, sender_email, recipient_name, recipient_email, message, amount) são atualizados usando a mutação `updateCartItems`.

<u>Resultados reais</u>:

Somente o valor é atualizado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
