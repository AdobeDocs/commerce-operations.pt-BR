---
title: "ACSD-61133: 'sales_clean_quotes' cron exclui cotações de ordens de compra não aprovadas"
description: Aplique o patch ACSD-61133 para corrigir o problema do Adobe Commerce em que "sales_clean_quotes" cron exclui cotações de ordens de compra não aprovadas.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 67b1dd3d4814b487d47a25697ed21d60f1e4e378
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` cron exclui cotações de ordens de compra não aprovadas

O patch ACSD-61133 corrige o problema em que o cron `sales_clean_quotes` exclui cotações de ordens de compra não aprovadas. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.53 está instalado. A ID do patch é ACSD-61133. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 e 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`sales_clean_quotes` o cron exclui cotações de ordens de compra não aprovadas. A *[Ordem de Compra B2B]* não pode ser convertida na ordem da cotação associada à ordem comprada, pois o cron a exclui.

<u>Pré-requisitos</u>:

Os módulos do Adobe Commerce [!UICONTROL B2B] estão instalados e habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar a funcionalidade *[!UICONTROL B2B Purchase Order]*.
1. Crie uma empresa.
1. Criar um *[!UICONTROL Purchase Order]*.
1. Aguarde até que a cotação expire e seja excluída pelo cron. O período de expiração da cotação pode ser definido com **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Converter *[!UICONTROL Purchase Order]* no pedido via *[!UICONTROL My Purchase Order in Customer Dashboard]* ou com [!DNL GraphQL] `placeOrderForPurchaseOrder` mutação.

<u>Resultados esperados</u>:

A cotação associada ao *[!UICONTROL Purchase Order]* ativo não é excluída como expirada pelo cron. O pedido foi feito com êxito na loja ou via [!DNL GraphQL].

<u>Resultados reais</u>:

O pedido não é feito e um erro é exibido na loja ou retornado na resposta [!DNL GraphQL].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
