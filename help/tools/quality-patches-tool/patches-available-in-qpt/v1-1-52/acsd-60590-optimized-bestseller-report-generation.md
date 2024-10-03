---
title: "ACSD-60590: Melhorando o desempenho da geração de relatórios diários agregados dos melhores vendedores"
description: Aplique o patch ACSD-60590 para corrigir o problema do Adobe Commerce em que o Relatório diário agregado de best-sellers leva um tempo significativo para ser gerado para um grande volume de pedidos feitos.
feature: Reporting
role: Admin, Developer
source-git-commit: 4fe3f205754c040b60b6b7f01c7109cb31f70af8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590: Melhorando o desempenho da geração de relatórios diários agregados dos melhores vendedores

O patch ACSD-60590 corrige o problema em que o Relatório diário agregado de best-sellers leva uma quantidade significativa de tempo para ser gerado para um grande volume de pedidos feitos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.52 está instalado. A ID do patch é ACSD-60590. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Relatório diário agregado de best-sellers leva um tempo significativo para gerar um grande volume de pedidos feitos.

<u>Pré-requisitos</u>

Um grande número de pedidos (Por exemplo: *500k*).

<u>Etapas a serem reproduzidas</u>:

1. Execute o seguinte comando:

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. Execute o trabalho `aggregate_sales_report_bestsellers_data`.

<u>Resultados esperados</u>:

O trabalho é concluído em menos de 30 segundos.

<u>Resultados reais</u>:

A consulta leva cerca de 10 minutos para cada loja por `created_at` datas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
