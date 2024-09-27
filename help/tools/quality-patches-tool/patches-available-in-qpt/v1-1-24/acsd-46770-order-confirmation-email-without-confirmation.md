---
title: "ACSD-46770: o email de confirmação do pedido é enviado mesmo quando [!UICONTROL Email Order Confirmation] está desmarcado"
description: Aplique o patch ACSD-46770 para corrigir o problema do Adobe Commerce em que os emails de confirmação de pedido são enviados mesmo quando [!UICONTROL Email Order Confirmation] não está selecionado.
feature: Communications, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-46770: o email de confirmação de pedido é enviado mesmo quando **[!UICONTROL Email Order Confirmation]** está desmarcado

O patch ACSD-46770 corrige o problema em que os pedidos podem ser feitos por meio da API REST como um usuário convidado mesmo quando **[!UICONTROL Email Order Confirmation]** está desmarcado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-46770. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um email de confirmação de pedido é enviado mesmo quando **[!UICONTROL Email Order Confirmation]** não está selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente.
1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Order]** e clique em **[!UICONTROL Create New Order]**.
1. Selecione o cliente, adicione os produtos ao pedido, preencha o endereço e selecione os métodos de Envio e Pagamento.
1. Antes de enviar o pedido, desmarque a caixa de seleção **[!UICONTROL Email Order confirmation]**.
1. Clique em **[!UICONTROL Submit Order]** para criar o pedido.

<u>Resultados esperados</u>:

Um email de confirmação de pedido não deve ser enviado se a opção **[!UICONTROL Email Order Confirmation]** não estiver selecionada.

<u>Resultados reais</u>:

Um email de confirmação de pedido é enviado independentemente da caixa de seleção **[!UICONTROL Email Order Confirmation]** não selecionada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
