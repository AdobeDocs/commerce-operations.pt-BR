---
title: 'ACSD-49737: o cupom está marcado incorretamente como usado após um pagamento de cartão com falha'
description: Aplique o patch ACSD-49737 para corrigir o problema do Adobe Commerce em que o cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737: O cupom está marcado incorretamente como *usado* após uma falha no pagamento do cartão

O patch ACSD-49737 corrige o problema em que o cupom é marcado incorretamente como *usado* após uma falha no pagamento do cartão. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é ACSD-49737. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cupom está marcado incorretamente como *usado* após falha no pagamento por cartão.

<u>Pré-requisitos</u>:

1. Configure o método **[!UICONTROL Braintree sandbox payment]**.
1. Verifique se o consumidor [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=pt-BR) está configurado e em execução.

<u>Etapas a serem reproduzidas</u>:

1. Crie um **[!UICONTROL Cart Price Rule]** com códigos de cupom gerados automaticamente.
1. Faça logon como cliente.
1. Adicionar produtos ao carrinho.
1. Aplicar um código de cupom gerado automaticamente.
1. Tente fazer um pedido com um pagamento com falha.
1. Verifique o uso do cupom no **[!UICONTROL Cart Price Rule]** na guia **[!UICONTROL Manage Coupon Codes]**.

<u>Resultados esperados</u>:

O cupom não deve ser sinalizado como *usado* se o pagamento falhar.

<u>Resultados reais</u>:

* O código do cupom diz - Usado: *Sim*, Vezes Usado: *1*
* O código do cupom é válido apenas para uso único.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Etapas adicionais necessárias após a instalação do patch

(Esta seção é opcional; pode haver algumas etapas necessárias após a aplicação do patch para corrigir o problema.) 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
