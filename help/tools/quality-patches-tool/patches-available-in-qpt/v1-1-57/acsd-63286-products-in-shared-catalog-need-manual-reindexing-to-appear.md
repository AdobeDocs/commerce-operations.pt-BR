---
title: 'ACSD-63286: os produtos atribuídos ao catálogo compartilhado precisam de reindexação manual para serem exibidos'
description: Aplique o patch ACSD-63286 para corrigir o problema do Adobe Commerce em que os produtos atribuídos a um catálogo compartilhado por meio da API não aparecem na loja até que uma reindexação manual seja executada.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '424'
ht-degree: 0%
---
# ACSD-63286: os produtos atribuídos ao catálogo compartilhado precisam de reindexação manual para serem exibidos

O patch ACSD-63286 corrige o problema em que os produtos atribuídos a um catálogo compartilhado por meio da API não aparecem na loja até que uma reindexação manual seja executada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-63286. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando os produtos são atribuídos a um catálogo compartilhado por meio da API, eles não aparecem no front-end após a execução do indexador parcial e dos trabalhos cron do consumidor. No entanto, elas aparecem após uma reindexação completa manual.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL RabbitMQ] como o serviço de fila.
1. Crie um catálogo compartilhado e atribua-o a uma empresa.
1. Crie um produto simples e atribua-o a uma categoria.
1. Executar reindexação parcial.

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Use a solicitação de API a seguir para atribuir o produto criado ao catálogo compartilhado `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`:

   ```json
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Execute o cron a seguir para limpar as filas e executar o reindexação parcial.

   ```shell
   bin/magento cron:run --group=consumers
   ```

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Faça logon no front-end como um usuário da empresa.
1. Verifique a página de categoria de front-end. Os produtos recentemente atribuídos não estão visíveis.
1. Executar uma reindexação manual:

   ```shell
   bin/magento index:reindex
   ```

<u>Resultados esperados</u>:

O produto aparece no front-end sem uma reindexação manual.

<u>Resultados reais</u>:

O produto aparece no front-end somente após reindexação manual.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
