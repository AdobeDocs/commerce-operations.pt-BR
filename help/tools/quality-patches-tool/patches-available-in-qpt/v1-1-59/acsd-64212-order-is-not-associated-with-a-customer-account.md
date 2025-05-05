---
title: 'ACSD-64212: Pedido não vinculado a uma conta de cliente criada via [!DNL GraphQL] após a realização do pedido'
description: Aplique o patch ACSD-64212 para corrigir o problema do Adobe Commerce em que um pedido não é vinculado a uma conta de cliente criada via [!DNL GraphQL] após a realização do pedido.
feature: GraphQL, Checkout, Customers
role: Admin, Developer
source-git-commit: d1d5214293f3bb38b787f80172aabf9cd0bf808b
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212: Pedido não vinculado a uma conta de cliente criada via [!DNL GraphQL] após a realização do pedido

O patch ACSD-64212 corrige o problema em que um pedido não é vinculado a uma conta de cliente criada via [!DNL GraphQL] após a realização do pedido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-64212. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O pedido não está vinculado a uma conta de cliente quando a conta é criada via [!DNL GraphQL] após o pedido.

<u>Etapas a serem reproduzidas</u>:

1. Coloque um pedido de convidado no front-end.
1. Envie a seguinte solicitação para criar a conta:

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>Resultados esperados</u>:

A ordem do convidado é associada ao cliente após a criação da conta do cliente.

<u>Resultados reais</u>:

A conta do cliente foi criada, mas a ordem do convidado não está associada ao cliente.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
