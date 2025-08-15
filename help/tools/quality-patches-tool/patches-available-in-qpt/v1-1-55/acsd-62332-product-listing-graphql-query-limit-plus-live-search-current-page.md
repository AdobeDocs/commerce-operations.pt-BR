---
title: 'ACSD-62332: consulta GraphQL da lista de produtos limitada a 10.000 produtos e  [!DNL Live Search] define a página atual como 1'
description: Aplique o patch ACSD-62332 para corrigir os problemas do Adobe Commerce em que a consulta do GraphQL da lista de produtos é limitada a uma contagem total de 10.000 produtos e em que [!DNL Live Search] define a página atual como *1* em vez da página *2* nos critérios de pesquisa quando consultado por meio do GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: A consulta GraphQL da lista de produtos está limitada a 10.000 produtos, e o [!DNL Live Search] define a página atual como 1

>[!NOTE]
>
>Este patch é uma versão atualizada do [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) e substitui o [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) nas versões 2.4.6 - 2.4.6-p8. Consulte os artigos correspondentes para obter mais detalhes.

O patch ACSD-62332 corrige os problemas em que a consulta GraphQL da lista de produtos é limitada a um `total_count` de 10.000 produtos e em que [!DNL Live Search] define a página atual como *1* em vez da página *2* nos critérios de pesquisa quando consultado via GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-62332. Observe que os problemas foram corrigidos no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta GraphQL de listagem de produtos está limitada a uma contagem total de 10.000 produtos e onde [!DNL Live Search] define a página atual como *1* em vez da página *2* nos critérios de pesquisa quando consultado via GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
