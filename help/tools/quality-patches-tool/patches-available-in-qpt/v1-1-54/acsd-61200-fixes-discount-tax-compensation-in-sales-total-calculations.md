---
title: "ACSD-61200: Corrige a compensação de imposto de desconto nos cálculos do total de vendas"
description: Aplique o patch ACSD-61200 para corrigir o problema do Adobe Commerce em que *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* estão ausentes nos cálculos do total de vendas, causando discrepâncias entre os dados da ordem de venda e os dados do relatório de cupom.
feature: Reporting, Taxes
role: Admin, Developer
source-git-commit: 61259d8e059cd813a84907e4baef873b2cc8cad0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Corrige a compensação de imposto de desconto em cálculos de total de vendas

O patch ACSD-61200 corrige o problema em que *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* estão ausentes dos cálculos de *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]*, resultando em discrepâncias entre os dados da ordem de venda e os dados do relatório de cupom. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61200. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

- Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

- Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Imprecisões nos dados do relatório de cupom e ordem de venda devido à falta de *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* nos cálculos do total de vendas.

<u>Etapas a serem reproduzidas</u>:

1. Crie um [!UICONTROL Tax Zone] e um [!UICONTROL Tax Rule].
1. Defina as seguintes configurações de imposto:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Atualize as seguintes configurações de exibição para Ordens, NFFs e Avisos de Crédito:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Crie um [!UICONTROL Cart Price Rule] com um cupom para um desconto de 10%.
1. Conclua uma ordem usando o cupom e gere uma NFF e uma entrega.
1. Vá para **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** e gere um relatório.
1. Compare os dados no resumo da ordem com os do relatório.

<u>Resultados esperados</u>:

Os cálculos de *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* incluem *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]*, correspondendo o resumo do pedido com os dados do relatório.

<u>Resultados reais</u>:

Os dados da ordem de venda e do relatório de cupom não correspondem porque *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* estão ausentes nos cálculos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

- Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
- Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) no guia Ferramentas.
