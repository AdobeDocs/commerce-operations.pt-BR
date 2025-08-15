---
title: 'ACSD-62118: a tabela "sales_order_tax_item" não foi totalmente atualizada para ordens B2B feitas usando o método [!UICONTROL Purchase Order]'
description: Aplique o patch ACSD-62118 para corrigir o problema do Adobe Commerce em que a tabela "sales_order_tax_item" não é totalmente atualizada quando pedidos B2B são feitos usando o método [!UICONTROL Purchase Order].
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62118: A tabela `sales_order_tax_item` não foi totalmente atualizada para pedidos B2B feitos usando o método [!UICONTROL Purchase Order]

O patch ACSD-62118 corrige o problema em que a tabela `sales_order_tax_item` não é totalmente atualizada quando um pedido B2B é colocado usando o método *[!UICONTROL Purchase Order]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-62118. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando pedidos B2B são feitos usando o método *[!UICONTROL Purchase Order]*, a tabela `sales_order_tax_item` não é totalmente atualizada. Esse problema afeta os cálculos de imposto e o processamento de pedido. Especificamente, a matriz `applied_taxes` fica vazia ao consultar a ordem por meio da API, e `tax_item_amount` e `tax_item_percent` são NULL.

<u>Etapas a serem reproduzidas</u>:

1. Adicionar regras de imposto para **[!UICONTROL Product]** e **[!UICONTROL Shipping]**.
1. Habilite o método **[!UICONTROL Purchase Order]** nas Configurações da empresa.
1. Faça logon como um usuário administrador da empresa.
1. Coloque um **[!UICONTROL Purchase Order]** usando um método de pagamento offline.
1. Depois que o [!UICONTROL Purchase Order] for aprovado automaticamente e convertido em um pedido, verifique os dados de imposto na tabela `sales_order_tax_item` e por meio da API REST.

<u>Resultados esperados</u>:

* A tabela `sales_order_tax_item` deve conter dados `tax_item`.
* A matriz `applied_taxes` deve exibir as informações de imposto corretas na resposta da API para ordens de compra, semelhantes a outros métodos de pagamento (por exemplo, Cheque/Ordem de Pagamento).

<u>Resultados reais</u>:

* A tabela `sales_order_tax_item` não contém dados `tax_item`.
* As matrizes `applied_taxes` e `item_applied_taxes` estão vazias na resposta da API para *[!UICONTROL Purchase Order]*.
* Nenhum dado de imposto é exibido ao usar o método de pagamento *[!UICONTROL Purchase Order]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
