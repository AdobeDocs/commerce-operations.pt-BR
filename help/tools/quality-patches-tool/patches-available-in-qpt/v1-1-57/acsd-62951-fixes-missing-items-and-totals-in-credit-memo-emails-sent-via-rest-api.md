---
title: 'ACSD-62951: corrige itens e totais ausentes em [!UICONTROL Credit Memo] emails enviados por meio da API REST'
description: Aplique o patch ACSD-62951 para corrigir o problema do Adobe Commerce para o qual o email [!UICONTROL Credit Memo] é enviado sem incluir os itens do pedido e os totais.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O email *[!UICONTROL Credit Memo]* enviado quando um memorando de crédito é criado por meio da API REST `POST V1/order/:orderId/refund` não inclui os itens de pedido e os totais.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com qualquer produto.
1. Enviar e faturar a ordem. Verifique se o email da fatura foi enviado e se inclui os detalhes do produto.
1. Gere um token de administrador usando o cliente da API.
1. Use o token para criar um memorando de crédito por meio da API REST.
   1. Ponto de extremidade: `POST V1/order/:orderId/refund`
   1. Carga da solicitação:

      ```json
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
