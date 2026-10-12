---
title: 'ACSD-65938: emails de cartão-presente enviados mesmo quando a criação da fatura falha'
description: Aplique o patch ACSD-65938 para corrigir o problema do Adobe Commerce em que emails de cartão-presente eram enviados antes que a fatura fosse salva e confirmada com êxito, garantindo que os emails fossem acionados depois que a fatura fosse salva corretamente.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: a6e85c9a-cbf6-4b4a-927b-43ec2ce827fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '402'
ht-degree: 0%
---
# ACSD-65938: emails de cartão-presente enviados mesmo quando a criação da fatura falha

O patch ACSD-65938 resolve um problema em que emails de cartão-presente eram enviados antes que a fatura fosse salva e confirmada com êxito. Com essa correção, os emails agora são acionados somente depois que a fatura é salva com êxito. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-65938. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Emails de cartão-presente foram enviados antes de confirmar que a fatura foi criada e salva com êxito, resultando no envio de emails mesmo quando a criação da fatura falhou.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel **[!UICONTROL Admin]**.
2. Navegue até **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]** e defina **[!UICONTROL Generate Gift Card Account when Order Item is]** como *Faturado*.
3. Crie um novo produto de cartão-presente.
4. Adicionar produto do carrinho de presente ao carrinho e prosseguir para **[!UICONTROL checkout]**. Você pode usar **[!UICONTROL Check/Money Order]** como método de pagamento.
5. Coloque o pedido.
6. Modifique o `OrderRepository` para simular uma exceção durante o posicionamento do pedido.
7. Envie uma solicitação POST para `rest/default/V1/order/<ORDER_ID>/invoice` com a seguinte carga:

   ```json
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Resultados esperados</u>:

Nenhum email de cartão-presente deverá ser enviado se a criação da fatura falhar.

<u>Resultados reais</u>:

O email do cartão-presente é enviado mesmo após a falha na criação da fatura.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
