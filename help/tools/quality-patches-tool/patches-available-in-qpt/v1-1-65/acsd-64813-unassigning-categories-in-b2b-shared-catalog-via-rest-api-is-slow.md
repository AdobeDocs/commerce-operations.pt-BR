---
title: 'ACSD-64813: o cancelamento de atribuição de categorias no catálogo compartilhado  [!DNL B2B] por meio da API REST é lento'
description: Aplique o patch ACSD-64813 para corrigir o problema do Adobe Commerce em que o cancelamento de atribuição de categorias em um catálogo compartilhado  [!DNL B2B]  por meio da API REST é lento.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
source-git-commit: 239a9efcc2ae231b337f654e4e36e6119e6eff7e
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-64813: o cancelamento de atribuição de categorias no catálogo compartilhado [!DNL B2B] por meio da API REST é lento

O patch ACSD-64813 corrige o problema em que o cancelamento de atribuição de categorias em um catálogo compartilhado [!DNL B2B] por meio da API REST é lento. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-64813. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cancelamento da atribuição de categorias em um catálogo compartilhado [!DNL B2B] por meio da API REST é lento.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL B2B]**, **[!UICONTROL Company]** e **[!UICONTROL Shared Catalog]**.
1. Gerar 30.000 produtos ativos, em estoque.
1. Crie um [catálogo compartilhado personalizado](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) e atribua todos os produtos a ele.
1. Crie uma nova categoria na categoria raiz padrão e atribua a ela alguns produtos.
1. Use o token de administrador para chamar o ponto de extremidade da API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` com a nova ID de categoria.

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Confirme se a resposta é *true*.
1. Execute `bin/magento cron:run` duas vezes ou execute uma reindexação.
1. Use o token de administrador para chamar o ponto de extremidade da API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` com a nova ID de categoria.

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>Resultados esperados</u>:

A operação deve ser concluída em um tempo razoável (em alguns minutos).

<u>Resultados reais</u>:

A execução leva aproximadamente 30 minutos ou resulta em um erro de tempo limite.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
