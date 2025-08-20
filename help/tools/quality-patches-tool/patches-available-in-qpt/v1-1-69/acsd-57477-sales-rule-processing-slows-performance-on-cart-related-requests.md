---
title: 'ACSD-57477: o processamento da regra de vendas reduz o desempenho nas solicitações relacionadas ao carrinho'
description: Aplique o patch ACSD-57477 para corrigir o problema do Adobe Commerce em que, em um projeto com muitos atributos de produto disponíveis (por exemplo, 1000 atributos), quando a operação GraphQL AddProductsToCart é executada com variáveis, o Commerce tenta carregar todos esses atributos de produto e causa problemas de desempenho lentos na operação GraphQL AddProductsToCart.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: o processamento da regra de vendas reduz o desempenho nas solicitações relacionadas ao carrinho

O patch ACSD-57477 corrige o problema em que o processamento da regra de vendas causa desempenho lento em solicitações relacionadas ao carrinho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-57477. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O processamento da regra de vendas causa desempenho lento em solicitações relacionadas ao carrinho se você enviar os parâmetros como variáveis do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Adicione 1000 atributos de produto.
1. Crie um carrinho usando a consulta abaixo do GraphQL.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Adicione um produto ao carrinho usando a consulta abaixo do GraphQL.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Defina essas Variáveis.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Esse problema ocorre somente quando você envia os parâmetros como variáveis do GraphQL. Se você incluir os parâmetros na própria consulta do GraphQL, esse problema não ocorrerá.
1. Envie a mesma solicitação **Adicionar ao carrinho** depois de adicionar parâmetros à própria consulta do GraphQL.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Resultados esperados</u>:

O desempenho da operação do GraphQL `AddProductsToCart` não deve ser degradado.

<u>Resultados reais</u>:

O desempenho da operação do GraphQL `AddProductsToCart` é degradado, pois carrega todos os atributos de produto quando os parâmetros são enviados como variáveis.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
