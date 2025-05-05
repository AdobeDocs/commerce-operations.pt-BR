---
title: 'ACSD-58566: erro interno do servidor do GraphQL para comentários de ordem de compra'
description: Aplique o patch ACSD-58566 para corrigir o problema do Adobe Commerce em que o GraphQL retorna um erro interno do servidor ao consultar o campo "created_at" na mutação "addPurchaseOrderComment".
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: erro interno do servidor do GraphQL para comentários de ordem de compra

O patch ACSD-58566 corrige o problema em que consultar o campo `created_at` na mutação `addPurchaseOrderComment` retorna um valor nulo em vez do datetime esperado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58566. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GraphQL retorna um erro interno do servidor ao consultar o campo `created_at` na mutação `addPurchaseOrderComment`.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados e as Empresas e Ordens de compra são ativadas.

<u>Etapas a serem reproduzidas</u>:

1. Gere um token de cliente para um usuário da empresa.
1. Execute a seguinte sequência de solicitações do GraphQL:
   1. Crie um *carrinho* usando `customerCart`.
   1. Adicione um produto ao *carrinho* usando `addProductsToCart`.
   1. Fazer o pedido usando `placePurchaseOrder`.
   1. Adicionar um comentário à ordem de compra usando `addPurchaseOrderComment`.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Resultados esperados</u>:

O campo `created_at` retorna a data e hora do comentário da ordem de compra.

<u>Resultados reais</u>:

Exibe nulo em vez da data `created_at`.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
