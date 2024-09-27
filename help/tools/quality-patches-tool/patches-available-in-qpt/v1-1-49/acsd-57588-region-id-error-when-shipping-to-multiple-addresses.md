---
title: "ACSD-57588: erro no processamento da ID da região ao enviar para vários endereços"
description: Aplique o patch ACSD-57588 para corrigir o problema do Adobe Commerce em que o envio de um pedido para vários endereços aciona um erro durante o processamento da ID da região.
feature: Orders, Shipping/Delivery
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57588: erro no processamento da ID da região ao enviar para vários endereços

O patch ACSD-57588 corrige o problema em que o envio de um pedido para vários endereços aciona um erro durante o processamento da ID da região. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 está instalado. A ID do patch é ACSD-57588. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro disparado durante o processamento da ID da região ao enviar para vários endereços.

<u>Etapas a serem reproduzidas</u>:

1. Configure o método de pagamento [!DNL Braintree].
1. Faça logon como cliente na loja.
1. Adicione um produto ao carrinho e prossiga para visualizar e editar o carrinho.
1. Adicione vários endereços *(Por exemplo, UK, US, CA)* durante o processo de check-out e revise o pedido.
1. Na página de finalização, selecione a opção de pagamento com cartão de crédito, insira as credenciais necessárias e faça o pedido.

<u>Resultados esperados</u>:

O pedido pode ser feito com sucesso.

<u>Resultados reais</u>:

O pedido não é feito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
