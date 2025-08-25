---
title: 'ACSD-66963: A mutação "estimateTotals" retorna nulo para descontos em produtos virtuais'
description: Aplique o patch ACSD-66963 para corrigir o problema do Adobe Commerce em que "estimateTotals" retorna *null* para descontos quando um código de desconto é aplicado a um carrinho apenas com produtos virtuais.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963: A mutação `estimateTotals` retorna nulo para descontos em produtos virtuais

O patch ACSD-66963 corrige o problema em que `estimateTotals` retorna *null* para descontos quando um código de desconto é aplicado a um carrinho apenas com produtos virtuais. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66963. Observe que esse problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação `estimateTotals` retorna *null* para descontos quando um código de desconto é aplicado a um carrinho que contém apenas produtos virtuais.

<u>Etapas a serem reproduzidas</u>:

1. Crie um carrinho contendo apenas produtos virtuais.
1. Aplicar um código de desconto:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

As informações de desconto são incluídas para carrinhos que contêm apenas produtos virtuais.

    &quot;
    &lbrace;
    &quot;dados&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;carrinho&quot;: &lbrace;
    &quot;preços&quot;: &lbrace;
    &quot;descontos&quot;: &lbrack;
    &lbrace;
    &quot;valor&quot;: &lbrace;
    &quot;valor&quot;: 100,5,
    &quot;moeda&quot;: &quot;USD&quot;
    &rbrace;,
    &quot;rótulo&quot;: &quot;Um segundo código de desconto para teste&quot;,
    &quot;cupom&quot;: &lbrace;
    &quot;código&quot;: &quot;z3r0c00l&quot;
    ,
    &quot;apply_to&quot;: &quot;ITEM&quot;,
    &quot;tipo&quot;: nulo
    &rbrace;
    &rbrack;
    &rbrace;
    &rbrace;
    &rbrace;
    ,
    &quot;extensões&quot;: {}
    &rbrace;
    &quot;

<u>Resultados reais</u>:

As informações de desconto são retornadas como *nulo* para carrinhos com apenas produtos virtuais.

    &quot;
    &lbrace;
    &quot;dados&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;carrinho&quot;: &lbrace;
    &quot;preços&quot;: &lbrace;
    &quot;descontos&quot;: nulo
    &rbrace;
    &rbrace;
    &rbrace;
    ,
    &quot;extensões&quot;: {}
    &rbrace;
    &quot;

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
