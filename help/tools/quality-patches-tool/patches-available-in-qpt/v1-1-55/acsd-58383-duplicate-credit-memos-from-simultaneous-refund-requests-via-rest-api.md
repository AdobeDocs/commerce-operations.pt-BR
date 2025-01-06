---
title: 'ACSD-58383: Avisos de crédito duplicados de solicitações de reembolso simultâneas via  [!DNL REST API]'
description: Aplique o patch ACSD-58383 para corrigir o problema do Adobe Commerce em que a emissão de um reembolso via  [!DNL REST API]  com duas solicitações idênticas executadas simultaneamente cria avisos de crédito duplicados.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: d3d98c04afe32d80cdf985b1d93c8a2cb57236ed
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383: Duplicar avisos de crédito de solicitações de reembolso simultâneas via [!DNL REST API]

O patch ACSD-58383 corrige o problema em que emitir um reembolso por meio do [!DNL REST API] com duas solicitações idênticas executadas simultaneamente resulta em avisos de crédito duplicados.

Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58383. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Avisos de crédito duplicados resultam de dois reembolsos criados ao mesmo tempo.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL Paypal Express] no Commerce [!UICONTROL Admin].
1. Definir ação de pagamento como *Venda*.
1. Configure o IPN [!DNL PayPal] (Notificação de Pagamento Instantânea) no site da Sandbox [!DNL PayPal].
1. Emitir reembolso no site de sandbox [!DNL PayPal].
1. Emular uma mensagem IPN de [!DNL PayPal] usando ferramentas de desenvolvedor. O IPN deverá criar um aviso de crédito.
1. Crie um segundo memorando de crédito usando uma chamada [!DNL API].

<u>Resultados esperados</u>:

Somente um aviso de crédito é criado para o mesmo item.


<u>Resultados reais</u>:

Dois avisos de crédito são criados para o mesmo item.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
