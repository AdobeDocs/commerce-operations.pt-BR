---
title: 'ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] não preenchidos quando [!UICONTROL asynchronous indexing] está habilitado'
description: Aplique o patch ACSD-46865 para corrigir o problema do Adobe Commerce em que as grades [!UICONTROL shipment] e [!UICONTROL credit memo] não são populadas quando [!UICONTROL asynchronous indexing] está habilitado.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] não preenchidos quando [!UICONTROL asynchronous indexing] está habilitado

O patch ACSD-46865 corrige o problema em que as grades [!UICONTROL shipment] e [!UICONTROL credit memo] não são preenchidas quando [!UICONTROL asynchronous indexing] está habilitado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-46865. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As grades de [!UICONTROL Shipment] e [!UICONTROL credit memo] não são populadas quando [!UICONTROL asynchronous indexing] está habilitado.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador [!DNL Commerce], vá para **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SIM*.
2. Novamente vá para **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Limpar cache de configuração.
4. Faça um novo pedido de um produto simples.
5. Execute o cron.
6. Abra o pedido no Administrador [!UICONTROL Commerce] acessando **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e gerando uma fatura e um memorando de crédito.
7. Mover a ordem para [!UICONTROL Archive].
8. Criar outro pedido para um produto simples.
9. Execute o cron.
10. Vá para a nova ordem e gere uma nova entrega, uma NFF e um aviso de crédito.
11. Execute o cron.
12. Verifique as grades de [!UICONTROL shipments], [!UICONTROL invoices] e [!UICONTROL credit memo] no administrador.

<u>Resultados esperados</u>:

Novos [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo] são exibidos.

<u>Resultados reais</u>:

Os novos [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo] não são exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
