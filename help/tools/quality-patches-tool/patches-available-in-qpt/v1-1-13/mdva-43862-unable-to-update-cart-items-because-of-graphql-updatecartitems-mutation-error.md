---
title: 'MDVA-43862: o cliente não pode atualizar itens do carrinho devido a um erro de mutação UpdateCartItems do GraphQL'
description: O patch MDVA-43862 resolve o problema em que o cliente não pode atualizar itens do carrinho devido a um erro de mutação UpdateCartItems do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43862. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: GraphQL, Orders, Shopping Cart
role: Admin
exl-id: d8a2579f-58f5-4407-8006-d58794a84b1f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43862: o cliente não pode atualizar itens do carrinho devido a um erro de mutação UpdateCartItems do GraphQL

O patch MDVA-43862 resolve o problema em que o cliente não pode atualizar itens do carrinho devido a um erro de mutação UpdateCartItems do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43862. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1, 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cliente não pode atualizar itens do carrinho devido a um erro de mutação UpdateCartItems do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável (MH01) atribuindo um simples (MH01-XL-Gray).
1. Acesse o Administrador do Commerce > **Catálogo** > **Produtos** > **SKU** > **MH01** > **Opções Personalizáveis**.
1. Adicione uma opção personalizada ao produto.
   * Título da opção: Option1
   * Tipo de opção: campo
   * Obrigatório: Sim
   * Preço: 10,00
   * Tipo de Preço: Fixo
   * SKU: MHC1
   * Máximo de caracteres: 25
1. Execute a consulta do GraphQL abaixo para gerar a ID do carrinho.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Anote o código de ID do carrinho.
1. Execute a consulta abaixo para adicionar o produto configurável ao carrinho:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Você notará que o carrinho é preenchido com o item configurável.
1. Anote a uid retornada.
1. Novamente, execute a consulta abaixo para atualizar o item do carrinho.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Observe a resposta.

<u>Resultados esperados</u>:

O carrinho é atualizado sem nenhum problema.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
