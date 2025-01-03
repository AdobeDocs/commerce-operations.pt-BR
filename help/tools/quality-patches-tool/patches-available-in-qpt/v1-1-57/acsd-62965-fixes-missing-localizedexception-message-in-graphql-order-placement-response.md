---
title: 'ACSD-62965: corrige a mensagem LocalizedException ausente na resposta de posicionamento do pedido do GraphQL'
description: Aplique o patch ACSD-62965 para corrigir os problemas do Adobe Commerce em que a mensagem "LocalizedException" não foi incluída na resposta do GraphQL durante o posicionamento do pedido.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: Correções sem a mensagem `LocalizedException` na resposta de posicionamento do pedido do GraphQL

O patch ACSD-62965 corrige o problema em que a mensagem `LocalizedException` não era incluída na resposta do GraphQL durante a inserção do pedido. Este patch está disponível com o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. A ID do patch é ACSD-62965. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A resposta do GraphQL para o posicionamento do pedido não inclui uma mensagem `LocalizedException`, resultando em detalhes de erro insuficientes para depuração.

<u>Etapas a serem reproduzidas</u>:

1. Instalar uma instância **[!DNL Adobe Commerce]** limpa.
1. Adicione um produto ao carrinho e prossiga para a etapa de colocação do pedido.
1. Adicione um `LocalizedException` a `Magento\Framework\Exception\LocalizedException` em `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Insira a exceção após a seguinte linha:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Adicione a exceção:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Execute a solicitação de GraphQL de ordem de colocação:

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Observe a resposta:
   1. A resposta não inclui a mensagem `LocalizedException`.
   1. Exemplo da resposta incorreta:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Resultados esperados</u>:

Se ocorrer um `LocalizedException`, a mensagem de exceção deverá ser incluída na resposta do GraphQL para o posicionamento do pedido para melhorar a manipulação de erros.

<u>Resultados reais</u>:

Se ocorrer um `LocalizedException`, a mensagem de exceção não será incluída na resposta do GraphQL para o posicionamento do pedido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
