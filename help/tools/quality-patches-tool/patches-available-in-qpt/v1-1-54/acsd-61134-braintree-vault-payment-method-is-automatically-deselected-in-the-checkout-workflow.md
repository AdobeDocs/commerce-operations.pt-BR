---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] método de pagamento automaticamente desmarcado no fluxo de trabalho de check-out'
description: Aplique o patch ACSD-61134 para resolver o problema do Adobe Commerce em que o método de pagamento *[!UICONTROL Braintree Vault]* é automaticamente desmarcado no fluxo de trabalho de check-out quando um comprador atualiza o endereço de cobrança ao desmarcar a caixa de seleção *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* método de pagamento automaticamente desmarcado no fluxo de trabalho de check-out

O patch ACSD-61134 corrige o problema em que o método de pagamento *[!UICONTROL Braintree Vault]* é automaticamente desmarcado no fluxo de trabalho de check-out quando um comprador atualiza seu endereço de cobrança ao desmarcar a caixa de seleção *[!UICONTROL My billing and shipping address are the same]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 está instalado. A ID do patch é ACSD-61134. Observe que este problema está programado para ser corrigido no Adobe Commerce 2.4.7-beta1.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O método de pagamento *[!UICONTROL Braintree Vault]* é automaticamente desmarcado no fluxo de trabalho de check-out.

<u>Etapas a serem reproduzidas</u>:

1. Configure o método de pagamento *[!DNL Braintree]* com *[!UICONTROL Vault]* habilitado.
1. Faça check-out e salve um cartão no *[!UICONTROL Vault]*.
1. Confira outro produto.
1. Na página *[!UICONTROL Shipping]*, adicione um novo endereço de entrega para que você tenha dois endereços para selecionar.
1. Na página *[!UICONTROL Payment]*, selecione seu método de pagamento e clique em **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Resultados esperados</u>:

O método de pagamento selecionado permanece selecionado.

<u>Resultados reais</u>:

O método de pagamento selecionado está desmarcado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
