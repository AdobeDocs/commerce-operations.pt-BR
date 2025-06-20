---
title: 'ACSD-62951: corrige itens e totais ausentes em [!UICONTROL Credit Memo] emails enviados por meio da API REST'
description: Aplique o patch ACSD-62951 para corrigir o problema do Adobe Commerce para o qual o email [!UICONTROL Credit Memo] é enviado sem incluir os itens do pedido e os totais.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: corrige itens e totais ausentes em *[!UICONTROL Credit Memo]* emails enviados por meio da API REST

O patch ACSD-62951 corrige o problema em que o email [!UICONTROL Credit Memo] é enviado sem incluir os itens de pedido e os totais. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62951. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p10

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O email *[!UICONTROL Credit Memo]* enviado quando um memorando de crédito é criado por meio da API REST `POST V1/order/:orderId/refund` não inclui os itens de pedido e os totais.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com qualquer produto.
1. Enviar e faturar a ordem. Verifique se o email da fatura foi enviado e se inclui os detalhes do produto.
1. Gere um token de administrador usando o cliente da API.
1. Use o token para criar um memorando de crédito por meio da API REST.
   1. Ponto de extremidade: `POST V1/order/:orderId/refund`
   1. Carga da solicitação:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Resultados esperados</u>:

O email *[!UICONTROL Credit Memo]* deve incluir os itens e os totais reembolsados

<u>Resultados reais</u>:

O email *[!UICONTROL Credit Memo]* não contém itens ou totais, resultando em informações incompletas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
