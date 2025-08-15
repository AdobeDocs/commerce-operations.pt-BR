---
title: 'ACSD-49179: O relatório de pedidos mostra valores incorretos para armazenamentos diferentes.'
description: Aplique o patch ACSD-49179 para corrigir o problema do Adobe Commerce em que o relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179: O relatório de pedidos mostra valores incorretos para armazenamentos diferentes

O patch ACSD-49179 corrige o problema em que o relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-49179. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** e defina [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Crie um site adicional, loja e visualização de loja.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** e defina:
   * Configuração padrão:
      * Moeda de base: USD
      * Moeda de Exibição Padrão: USD
      * Moedas permitidas: EUR, USD e THB (Baht tailandês)
   * Site principal:
      * Moeda de base: EUR
      * Moeda de Exibição Padrão: EUR
      * Moedas permitidas: EUR
   * Novo site adicional:
      * Moeda de base: THB (Baht tailandês)
      * Moeda de exibição padrão: THB (Baht tailandês)
      * Moedas permitidas: THB (Baht tailandês)
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** e defina as taxas de conversão vazias para o THB (defina as taxas como 1.0000).
1. Crie um produto, atribua-o aos dois sites e faça um pedido com esse produto no site adicional criado anteriormente.
1. Verifique se o pedido está no status *Processando* (fatura).
1. No back-end, vá para **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Clique no aviso **[!UICONTROL Yellow]** para atualizar as estatísticas.
1. Defina o escopo do relatório no site adicional criado anteriormente e defina o filtro da seguinte maneira:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: O mesmo dia quando a ordem de teste foi feita
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Resultados esperados</u>:

Total de vendas mostra o valor correto convertido na moeda do site.

<u>Resultados reais</u>:

O total é zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
