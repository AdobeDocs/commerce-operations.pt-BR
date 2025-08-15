---
title: 'ACSD-60326: a consulta GraphQL no status do cliente [!UICONTROL Returns] fornece um erro'
description: Aplique o patch ACSD-60326 para corrigir o problema do Adobe Commerce em que ocorre um erro na consulta do GraphQL para o status do cliente [!UICONTROL Returns].
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: a consulta GraphQL no status do cliente [!UICONTROL Returns] fornece um erro

O patch ACSD-60326 corrige o problema em que ocorre um erro na consulta do GraphQL para o status do cliente [!UICONTROL Returns]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 está instalado. A ID do patch é ACSD-60326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta GraphQL no status do cliente [!UICONTROL Returns] fornece um erro.

<u>Etapas a serem reproduzidas</u>:

1. Inicialize uma nova instância com dados de amostra.
1. Na barra lateral *[!UICONTROL Admin]*, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** e defina **[!UICONTROL Enable RMA on Storefront]** como *Sim*.
1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** e preencha o endereço.
1. Altere a senha do cliente `roni_cost@example.com`.
1. Faça logon no painel de administração e faça um pedido para o cliente `roni_cost@example.com` com os seguintes produtos:
   * *WSH12-32-Vermelho*
   * *WSH12-32-Roxo*
   * *WSH12-32-Verde*
1. Crie um *[!UICONTROL Invoice]* e *[!UICONTROL Shipment]* para este pedido.
1. Selecione **[!UICONTROL Create Returns]**.
1. Vá para **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** e:
   * Selecione *WSH12-32-Vermelho* e *WSH12-32-Roxo*
   * Clique em **[!UICONTROL Add Selected Products to returns]**:
      * Conjunto **[!UICONTROL Requested]** = *1*
      * Definir **[!UICONTROL Return Reason]** como *Fora de Serviço*
      * Definir **[!UICONTROL Item Condition]** como *Aberto*
      * Ajustar **[!UICONTROL Resolution]** para *Reembolso*
   * Clique em **[!UICONTROL Submit Returns]**.
1. Abra **[!UICONTROL Returns]** e selecione **[!UICONTROL Return Items]** à esquerda.
   * Definir **[!UICONTROL Authorized]** = *1* para os dois produtos
   * Definir **[!UICONTROL Status]** como *Autorizado* para *WSH12-32-Roxo*
   * Definir **[!UICONTROL Status]** como *Negado* para *WSH12-32-Vermelho*
   * Clique em **[!UICONTROL Save]**
1. Crie um novo pedido com os mesmos produtos.
1. Crie um(a) *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* e *[!UICONTROL Returns]* para os mesmos produtos. Autorizar e prosseguir até o final do processo [!UICONTROL Returns].
1. Gere um token de cliente usando a seguinte query do GraphQL:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autorize com o token recebido e execute a seguinte consulta:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Resultados esperados</u>:

A consulta não mostra nenhum erro. O status do segundo retorno não é *nulo*.

<u>Resultados reais</u>:

A consulta retorna um erro interno do servidor:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
