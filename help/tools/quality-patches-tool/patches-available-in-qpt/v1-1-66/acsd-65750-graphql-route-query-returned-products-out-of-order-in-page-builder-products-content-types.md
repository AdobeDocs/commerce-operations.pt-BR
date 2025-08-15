---
title: 'ACSD-65750: a consulta  [!DNL GraphQL] "rota" retorna produtos fora de ordem no tipo de conteúdo  [!DNL Page Builder]  Produtos'
description: Aplique o patch ACSD-65750 para corrigir o problema do Adobe Commerce em que a consulta de "rota" do GraphQL retorna produtos fora de ordem no  [!DNL Page Builder] tipo de conteúdo Produtos.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 2d6debf4d426a0473eb77919c2307afdc77bf937
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-65750: a consulta &quot;rota&quot; [!DNL GraphQL] retorna produtos fora de ordem no tipo de conteúdo [!DNL Page Builder] Produtos

O patch ACSD-65750 corrige o problema em que a consulta &quot;rota&quot; [!DNL GraphQL] retorna produtos fora de ordem no tipo de conteúdo [!DNL Page Builder] Produtos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-65750. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A consulta &quot;rota&quot; do [!DNL GraphQL] não retorna produtos na ordem de classificação correta ao usar o tipo de conteúdo Produtos [!DNL Page Builder].

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova categoria e alguns produtos no Catálogo e vincule os produtos a esta categoria.
1. Navegue até **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, edite a categoria criada e abra a guia **[!UICONTROL Products in Category]**.
1. Defina o **[!UICONTROL Position]** personalizado para cada produto desta categoria.
1. Salve a categoria e execute a reindexação.
1. Navegue até **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** e clique em **[!UICONTROL Add New Page]**.
1. Expanda a guia **[!UICONTROL Content]** e clique em **[!UICONTROL Edit with Page Builder]**.
1. Arraste um elemento **[!UICONTROL Row]** para a área de conteúdo e, em seguida, arraste um elemento **[!UICONTROL Products]** para dentro da linha.
1. Configure o elemento Produtos da seguinte maneira:
   * **[!UICONTROL Select Products By]**: *Categoria*
   * **[!UICONTROL Category]**: *Selecione a categoria recém-criada*
   * **[!UICONTROL Sort By]**: *Posição*
1. Alterne para a guia **[!UICONTROL Search Engine Optimization]** e defina o **[!UICONTROL URL Key]** como *widget de teste*.
1. Salve a página.
1. Faça a seguinte solicitação [!DNL GraphQL]:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Resultados esperados</u>:

O sistema retorna produtos na ordem definida por sua posição de categoria.

<u>Resultados reais</u>:

O sistema retorna produtos em um pedido que não corresponde à posição da categoria na resposta do GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
