---
title: 'ACSD-65938: emails de cartão-presente enviados mesmo quando a criação da fatura falha'
description: Aplique o patch ACSD-65938 para corrigir o problema do Adobe Commerce em que emails de cartão-presente eram enviados antes que a fatura fosse salva e confirmada com êxito, garantindo que os emails fossem acionados depois que a fatura fosse salva corretamente.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
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

   ```
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
