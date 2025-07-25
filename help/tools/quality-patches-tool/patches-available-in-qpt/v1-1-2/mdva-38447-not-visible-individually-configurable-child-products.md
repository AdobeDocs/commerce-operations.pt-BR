---
title: 'MDVA-38447: os produtos secundários configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta do MySQL é lenta'
description: O patch do Adobe Commerce MDVA-38447 corrige o problema em que os produtos secundários configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta MySQL lenta para consulta de produtos GraphQL com filtro de categoria. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-38447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447: os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e a consulta do MySQL é lenta

O patch do Adobe Commerce MDVA-38447 corrige o problema em que os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e a consulta MySQL lenta para consulta de produtos GraphQL com filtro de categoria. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-38447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e na consulta lenta do MySQL para produtos da GraphQL com filtro de categoria.

<u>Pré-requisitos</u>:

Os módulos B2B devem ser instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com produtos simples definidos como **Não visíveis individualmente**.
1. Executar uma **reindexação completa**.
1. Executar uma **consulta do GraphQL** como:

<pre>consulta getFilteredProducts(
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) &lbrace;
  products(
    filtro: $filter
    sort: $sort
    pesquisa: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_páginas
      current_page
      page_size
    &rbrace;
    itens &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variáveis:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Resultados esperados</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; não serão retornados em resposta.

<u>Resultados reais</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; são retornados em resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR).
