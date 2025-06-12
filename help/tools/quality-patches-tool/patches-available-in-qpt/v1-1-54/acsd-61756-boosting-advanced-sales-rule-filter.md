---
title: 'ACSD-61756: degradação de desempenho de filtros "AdvancedSalesRule" devido à falta de índices de banco de dados'
description: Aplique o patch ACSD-61756 para corrigir o problema do Adobe Commerce em que a consulta "magento_salesrule_filter" executa uma verificação de tabela completa sem usar índices, resultando em degradação de desempenho ao manipular grandes volumes de registros. Este patch melhora o desempenho adicionando os índices de banco de dados ausentes para filtros "AdvancedSalesRule".
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: degradação de desempenho de `AdvancedSalesRule` filtros devido à ausência de índices de banco de dados

Aplique o patch ACSD-61756 para melhorar o desempenho dos filtros `AdvancedSalesRule` adicionando índices de banco de dados ausentes. Isso corrige o problema em que a consulta `magento_salesrule_filter` executa uma verificação completa da tabela sem utilizar os índices, levando à degradação do desempenho quando há muitos registros na tabela. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 está instalado. A ID do patch é ACSD-61756. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p9

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta `magento_salesrule_filter` executa uma verificação de tabela completa sem utilizar índices, levando à degradação de desempenho dos filtros `AdvancedSalesRule` quando há muitos registros na tabela.

<u>Etapas a serem reproduzidas</u>:

1. Check-out com várias regras de vendas ativas.

<u>Resultados esperados</u>:

Desempenho aprimorado das regras de vendas.

<u>Resultados reais</u>:

A consulta executa uma verificação completa da tabela e falha ao utilizar índices, levando à degradação do desempenho quando há muitos registros na tabela.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
