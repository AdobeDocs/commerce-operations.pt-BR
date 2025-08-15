---
title: 'ACSD-45143: a mutação setShippingAddressesOnCart não define o código de região numérica como "região"'
description: O patch ACSD-45143 corrige o problema em que a mutação setShippingAddressesOnCart não permite definir o código de região numérica como "região". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45143. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: c7d9d1f2-4731-406f-93bd-036f0fe75b1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-45143: a mutação setShippingAddressesOnCart não define o código de região numérica como &quot;região&quot;

O patch ACSD-45143 corrige o problema em que a mutação setShippingAddressesOnCart não permite definir o código de região numérica como &quot;região&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45143. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação setShippingAddressesOnCart não permite definir o código de região numérico como &quot;região&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Crie um carrinho usando a consulta abaixo.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      createEmptyCart
    &rbrace;
    </code>
    </pre>

1. Envie uma solicitação para definir o endereço de entrega do carrinho.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) &lbrace;
      setShippingAddressesOnCart(
        input: &lbrace;
          cart_id: $cartId
          shipping_addresses: &lbrace;
            address: &lbrace;
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            &rbrace;
          &rbrace;
        &rbrace;
        ) &lbrace;
          cart &lbrace;
            shipping_addresses &lbrace;
              firstname
              lastname
              company
              street
              city
              region &lbrace;
                code
                label
              &rbrace;
              postcode
              telephone
              country &lbrace;
                code
                label
              &rbrace;
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Observação: neste exemplo, o código do país é definido como &quot;FR&quot; e o código da região como &quot;58&quot;. De acordo com a tabela Db `directory_country_region`, o código de região 58 é &quot;Nièvre&quot;.

1. Verifique a resposta retornada.

<u>Resultados esperados</u>:

O Adobe Commerce permite definir o código de região numérica na solicitação do GraphQL.

<u>Resultados reais</u>:

O código de região é alterado para 47.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "setShippingAddressesOnCart": &lbrace;
      "cart": &lbrace;
        "shipping_addresses": &lbrack;
        &lbrace;
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": &lbrack;
          "234 Rue de Rivoli"
          &rbrack;,
          "city": "Lille",
          "region": &lbrace;
            "code": "47",
            "label": "Lot-et-Garonne"
            &rbrace;,
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": &lbrace;
              "code": "FR",
              "label": "FR"
            &rbrace;
          &rbrace;
        &rbrack;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
