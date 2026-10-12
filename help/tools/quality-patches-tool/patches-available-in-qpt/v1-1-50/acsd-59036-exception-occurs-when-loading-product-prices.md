---
title: 'ACSD-59036: uma exceção ocorre ao carregar preços de produtos com limites inferiores e superiores definidos como US$ 0'
description: Aplique o patch ACSD-59036 para corrigir o problema do Adobe Commerce em que ocorre uma exceção ao carregar preços do produto com limites inferiores e superiores definidos como *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%
---
# ACSD-59036: Ocorre uma exceção ao carregar preços de produtos com limites inferiores e superiores definidos como *$0*

O patch ACSD-59036 corrige o problema em que uma exceção ocorre ao carregar preços de produtos com limites inferiores e superiores definidos como *$0*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-59036. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
