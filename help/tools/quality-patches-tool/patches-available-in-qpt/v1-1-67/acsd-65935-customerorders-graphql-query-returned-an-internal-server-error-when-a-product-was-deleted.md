---
title: 'ACSD-65935: A consulta do GraphQL "customerOrders" retornou um erro interno do servidor quando um produto é excluído'
description: Aplique o patch ACSD-65935 para corrigir o problema do Adobe Commerce em que a consulta do GraphQL "customerOrders" retornou um erro interno do servidor quando um produto é excluído.
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: fd0b7043770bbbd12fbb9aad8cddaa2434d2ea5b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# ACSD-65935: `customerOrders` A consulta do GraphQL retornou um erro interno do servidor quando um produto foi excluído

O patch ACSD-65935 corrige o problema em que a consulta do GraphQL `customerOrders` retornava um erro interno do servidor quando um produto era excluído. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-65935. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta do GraphQL `customerOrders` retorna um erro interno do servidor quando um produto é excluído.

<u>Etapas a serem reproduzidas</u>:

1. Criar dois produtos simples
1. Crie um cliente e faça um pedido com dois produtos do front-end.
1. Ir para o back-end e excluir um produto.
1. Criar um token de cliente:

```
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. Recupere a lista de pedidos usando o filtro `eligible_for_return` (usado no PWA para buscar pedidos de clientes):

```
https://localhost/pub/graphql
{
  customerOrders {
    items {
      order_number
      id
      created_at
      grand_total
      status
			items{
				eligible_for_return
			}
    }
  }
}
```

<u>Resultados esperados</u>:

A lista de pedidos é coletada sem erros.

<u>Resultados reais</u>:

Exceção: *Erro interno do servidor*

```
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
