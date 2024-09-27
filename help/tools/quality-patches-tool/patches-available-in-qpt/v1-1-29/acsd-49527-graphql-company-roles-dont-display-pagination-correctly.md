---
title: "ACSD-49527: as funções da empresa GraphQL não exibem a paginação corretamente"
description: Aplique o patch ACSD-49527 para corrigir o problema do Adobe Commerce em que as funções da empresa GraphQL não exibem a paginação corretamente.
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-49527: as funções da empresa GraphQL não exibem a paginação corretamente

O patch ACSD-49527 corrige o problema em que as funções da empresa GraphQL não exibem a paginação corretamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49527. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As funções da empresa GraphQL não exibem a paginação corretamente.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar empresa B2B.
1. Na loja, crie uma nova empresa.
1. Crie pelo menos duas novas funções para esta empresa; portanto, há um total de três funções, uma função é o padrão.
1. Enviar solicitação GraphQL para obter funções especificando [!UICONTROL pageSize]: 2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Verifique a resposta do GraphQL.

<u>Resultados esperados</u>:

`total_count: 3` e `total_pages: 2` são retornados na resposta do GraphQL.

<u>Resultados reais</u>:

`total_count: 2` e `total_pages: 1` são retornados na resposta do GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
