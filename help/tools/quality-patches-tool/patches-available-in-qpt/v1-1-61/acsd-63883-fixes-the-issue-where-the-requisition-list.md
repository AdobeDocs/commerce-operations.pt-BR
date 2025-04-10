---
title: 'ACSD-63883: corrigindo "items_count" incorreto em  [!DNL GraphQL] resposta para [!UICONTROL Requisition List]'
description: Aplique o patch ACSD-63883 para corrigir o problema em que [!UICONTROL Requisition List] retorna um "items_count" incorreto na resposta  [!DNL GraphQL] .
feature: B2B, GraphQL
role: Admin, Developer
source-git-commit: 5d8b78588b11534828a9b925cbab0cc945860367
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: Corrigindo `items_count` incorreto na resposta [!DNL GraphQL] para [!UICONTROL Requisition List]

O patch ACSD-63883 corrige o problema em que **[!UICONTROL Requisition List]** retorna um `items_count` incorreto na resposta [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-63883. Observe que o problema está programado para ser corrigido no Adobe Commerce B2B 1.5.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O **[!UICONTROL Requisition List]** retorna um `items_count` incorreto na resposta [!DNL GraphQL].


<u>Etapas a serem reproduzidas</u>:

1. Habilite o recurso B2B **[!UICONTROL Requisition List]**.
1. Crie alguns produtos.
1. Crie uma conta de cliente.
1. Clique em **[!UICONTROL Create new Requisition List]**.
1. Envie a solicitação de mutação `addProductsToRequisitionList` [!DNL GraphQL] com um produto para adicioná-la ao [!UICONTROL Requisition List].

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Envie a solicitação de mutação `addProductsToRequisitionList` [!DNL GraphQL] com três outros produtos para adicioná-los ao [!UICONTROL Requisition List].
1. Verifique o `items_count` na resposta.

**Resultados esperados**:

* `items_count`: 4 deve ser retornado na resposta.

**Resultados reais**:

* `items_count`: 2 é retornado na resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
