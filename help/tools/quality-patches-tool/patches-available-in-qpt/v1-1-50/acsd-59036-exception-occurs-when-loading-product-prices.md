---
title: 'ACSD-59036: uma exceção ocorre ao carregar preços de produtos com limites inferiores e superiores definidos como US$ 0'
description: Aplique o patch ACSD-59036 para corrigir o problema do Adobe Commerce em que ocorre uma exceção ao carregar preços do produto com limites inferiores e superiores definidos como *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-59036: Ocorre uma exceção ao carregar preços de produtos com limites inferiores e superiores definidos como *$0*

O patch ACSD-59036 corrige o problema em que uma exceção ocorre ao carregar preços de produtos com limites inferiores e superiores definidos como *$0*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-59036. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Exceção ao carregar preços de produtos com limites inferiores e superiores definidos como *$0*.

O problema está ocorrendo porque o algoritmo não leva em conta valores NULL ao carregar a consulta com intervalos de preços. Para corrigir isso, podemos verificar se os intervalos inferior e superior são NULOS e, se forem, atribuir um valor de *0* para ambos os limites. Isso deve impedir que erros sejam gerados.

<u>Etapas a serem reproduzidas</u>:

1. Criar *13* produtos simples.
1. Atribuir todos os produtos *13* a uma categoria.
1. Defina o preço de um produto para *$1322.94*.
1. Defina o preço de todos os outros produtos para *$0*.
1. Configure [!DNL OpenSearch] como um mecanismo de pesquisa.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** e defina a contagem de **[!UICONTROL PLP]** como *16*.
1. Defina **[!UICONTROL Price Navigation Step Calculation]** como *Automático (equalizar contagens de produtos)*.
1. Executar reindexação completa.
1. Abra a página *[!UICONTROL Category]*.

<u>Resultados esperados</u>:

A página *[!UICONTROL Category]* exibe todos os produtos.

<u>Resultados reais</u>:

Ocorre um erro:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
