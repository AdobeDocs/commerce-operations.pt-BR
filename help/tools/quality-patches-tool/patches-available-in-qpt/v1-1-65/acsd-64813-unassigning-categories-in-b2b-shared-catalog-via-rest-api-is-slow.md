---
title: 'ACSD-64813: o cancelamento de atribuição de categorias no catálogo compartilhado [!DNL B2B] por meio da API REST é lento'
description: Aplique o patch ACSD-64813 para corrigir o problema do Adobe Commerce em que o cancelamento de atribuição de categorias em um catálogo compartilhado [!DNL B2B] por meio da API REST é lento.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '398'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cancelamento da atribuição de categorias em um catálogo compartilhado [!DNL B2B] por meio da API REST é lento.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL B2B]**, **[!UICONTROL Company]** e **[!UICONTROL Shared Catalog]**.
1. Gerar 30.000 produtos ativos, em estoque.
1. Crie um [catálogo compartilhado personalizado](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) e atribua todos os produtos a ele.
1. Crie uma nova categoria na categoria raiz padrão e atribua a ela alguns produtos.
1. Use o token de administrador para chamar o ponto de extremidade da API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` com a nova ID de categoria.

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Confirme se a resposta é *true*.
1. Execute `bin/magento cron:run` duas vezes ou execute uma reindexação.
1. Use o token de administrador para chamar o ponto de extremidade da API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` com a nova ID de categoria.

   ```json
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
