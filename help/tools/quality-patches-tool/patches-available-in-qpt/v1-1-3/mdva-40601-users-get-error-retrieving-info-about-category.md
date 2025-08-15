---
title: 'MDVA-40601: Não é possível recuperar dados sobre categoria alterada pela atualização agendada via GraphQL'
description: O patch de qualidade MDVA-40601 do Adobe Commerce corrige o problema em que os usuários recebem um erro ao obter informações sobre a categoria alterada por atualização agendada por meio do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 está instalada. A ID do patch é MDVA-40601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40601: Não é possível recuperar dados sobre categoria alterada pela atualização agendada via GraphQL

O patch de qualidade MDVA-40601 do Adobe Commerce corrige o problema em que os usuários recebem um erro ao obter informações sobre a categoria alterada por atualização agendada por meio do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 está instalada. A ID do patch é MDVA-40601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.3 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários recebem um erro ao tentar recuperar informações sobre a categoria alterada pela atualização agendada por meio do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Configure uma estrutura de categoria com uma subcategoria conforme indicado abaixo:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Execute a consulta do GraphQL com a ID 49 de &quot;Alguma categoria&quot;.

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   Resultado:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Crie uma atualização de agendamento para &quot;Alguma categoria&quot; com um nome de categoria diferente.
1. Aguarde a atualização do cronograma ser ativada.
1. Execute a mesma query fornecida acima.

<u>Resultados esperados</u>:

Você recebe o mesmo resultado, mas com o nome de categoria atualizado.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

&#x200B;* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
&#x200B;* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

&#x200B;* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
&#x200B;* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR).
