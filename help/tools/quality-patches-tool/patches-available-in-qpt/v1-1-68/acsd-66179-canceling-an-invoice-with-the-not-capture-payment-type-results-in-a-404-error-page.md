---
title: 'ACSD-66179: cancelar uma fatura com o tipo de pagamento [!UICONTROL Not Capture] resulta em uma página de erro 404'
description: Aplique o patch ACSD-66179 para corrigir o problema do Adobe Commerce em que o cancelamento de uma fatura com o tipo de pagamento [!UICONTROL Not Capture] resultava em uma página de erro 404.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179: cancelar uma fatura com o tipo de pagamento [!UICONTROL Not Capture] resulta em uma página de erro 404

O patch ACSD-66179 corrige o problema em que cancelar uma fatura criada com o tipo de pagamento *[!UICONTROL Not Capture]* resultava em uma página de erro 404. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66179. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Cancelar uma fatura criada com o tipo de pagamento *[!UICONTROL Not Capture]* resulta em uma página de erro 404.

<u>Etapas a serem reproduzidas</u>:

1. Crie um pedido usando um método de pagamento, como o Check-out expresso do PayPal.
1. Criar uma fatura. Defina **[!UICONTROL Amount]** como *[!UICONTROL Not Capture]* e envie a fatura.
1. Abra a fatura criada e selecione **[!UICONTROL Cancel]**.

<u>Resultados esperados</u>:

1. A fatura foi cancelada com êxito.
1. Uma mensagem de êxito é exibida: *Você cancelou a fatura.*

<u>Resultados reais</u>:

Uma página de erro 404 é exibida: *Página Não Encontrada.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
