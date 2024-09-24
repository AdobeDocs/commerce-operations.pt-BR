---
title: 'MDVA-42341: a consulta do GraphQL "categoryList" não filtra os resultados'
description: O patch MDVA-42341 resolve o problema em que a consulta do GraphQL "categoryList" não filtra os resultados se uma solicitação tiver o cabeçalho Loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-42341. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: GraphQL, Categories
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341: a consulta GraphQL &quot;categoryList&quot; não filtra os resultados

O patch MDVA-42341 resolve o problema em que a consulta do GraphQL &quot;categoryList&quot; não filtra os resultados se uma solicitação tiver o cabeçalho Loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 está instalada. A ID do patch é MDVA-42341. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta &quot;categoryList&quot; do GraphQL não filtra os resultados se uma solicitação tiver o cabeçalho Loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova Categoria Raiz e nomeie-a como **root2**.
1. Crie um segundo Site/Loja/Loja e atribua **root2** à nova Loja.
1. Crie uma nova categoria em Default root category = category1.
1. Usando uma solicitação GraphQL, obtenha uma lista de categorias para o segundo site (use Header store = new).

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>Resultados esperados</u>:

As categorias da categoria raiz padrão não são listadas na resposta, pois estamos usando um cabeçalho de armazenamento &quot;novo&quot;.

<u>Resultados reais</u>:

As categorias da categoria raiz padrão estão disponíveis nos resultados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
