---
title: "ACSD-53148: duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável"
description: Aplique o patch ACSD-53148 para corrigir o problema do Adobe Commerce, em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultaram em dois itens separados no carrinho com o mesmo SKU de produto.
feature: GraphQL, Shopping Cart
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53148: duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável

O patch ACSD-53148 corrige o problema em que duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultaram em dois itens separados no carrinho com o mesmo SKU de produto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.37 está instalado. A ID do patch é ACSD-53148. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Duas solicitações paralelas no GraphQL para adicionar o mesmo produto configurável ao carrinho resultaram em dois itens separados no carrinho com o mesmo SKU de produto.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com SKU *Test* e um produto simples com SKU *Test-A*.
1. Crie um novo carrinho vazio via GraphQL (altere o local com seu próprio [!DNL URL]):

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"mutation{\n createEmptyCart\n}","variables"{}}'
   ```

1. Execute duas solicitações simultâneas para adicionar o mesmo produto ao carrinho (altere *cartID* e o local para ambas as solicitações):

   ```GraphQL
       curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}' & curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}'
   ```

1. Faça com que o carrinho veja os itens (altere *cartId* e o local):

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"{\n cart(cart_id: \"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf\") {\n items {\n id\n product {\n name\n sku\n }\n quantity\n }\n\n }\n}\n","variables":{}}'
   ```

<u>Resultados esperados</u>:

Item listado uma vez com [!UICONTROL qty] = 2.

```GraphQL
    {"data":{"cart":{"items":[{"id":"5","product":{"name":"config1","sku":"config1"},"quantity":2}]}}}%
```

<u>Resultados reais</u>:

Item listado duas vezes com [!UICONTROL qty] = 1.

```GraphQL
    {"data":{"cart":{"items":[{"id":"1","product":
    {"name":"config1","sku":"config1"},"quantity":1},
    {"id":"3","product":{"name":"config1","sku":"config1"},"quantity":1}]}}}%
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
