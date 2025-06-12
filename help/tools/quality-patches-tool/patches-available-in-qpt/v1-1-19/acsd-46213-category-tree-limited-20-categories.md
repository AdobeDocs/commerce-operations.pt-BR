---
title: 'ACSD-46213: solicitação de árvore de categoria limitada a 20 categorias'
description: 'O patch ACSD-46213 corrige o problema em que a solicitação da árvore de categorias é limitada a 20 categorias. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 está instalada. A ID do patch é ACSD-46213. '
feature: Categories
role: Admin
exl-id: 2cd4b102-db52-424f-9a7f-d775cb2b2c49
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-46213: solicitação de árvore de categoria limitada a 20 categorias

O patch ACSD-46213 corrige o problema em que a solicitação da árvore de categorias é limitada a 20 categorias. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 está instalada. A ID do patch é ACSD-46213.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.


## Problema

A solicitação da árvore de categorias é limitada a 20 categorias.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma categoria na categoria raiz.
1. Crie 24 subcategorias na categoria raiz criada na etapa um.
1. Execute a seguinte solicitação do GraphQL:

   <pre>
    <code class="language-graphql">
    &lbrace;
      categoryList(filters: { parent_id: { in: ["3"] } }) &lbrace;
        name
        level
        path
        url_path
        children &lbrace;
          id
          level
          name
          path
          url_path
          url_key
          children &lbrace;
            uid
            level
            name
            path
            url_path
            url_key
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Verifique os resultados.

<u>Resultados esperados</u>:

Ele mostra 24 categorias.

<u>Resultados reais</u>:

Ele mostra apenas 20 categorias.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
