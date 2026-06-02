---
title: 'B2B-2598: Adiciona o recurso de armazenamento em cache a storeConfig, moeda, país, países, availableStores GraphQl queries'
description: Aplique o patch B2B-2598 para adicionar recurso de cache às consultas GraphQl "storeConfig", "currency", "country", "countries" e "availableStores".
feature: B2B, GraphQL, Cache
role: Admin
type: Troubleshooting
autotag-review: '2026-05-22T20:21:20.687Z'
TQID: 'https://experienceleague.adobe.com/DQWkSrUHcUhOTn3fWdnRPVQUK6jRkPGCAnIKPRHkebQ'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
industry_v2:
  - id: aad1e361-483a-40cf-9a88-144325515074
source-git-commit: 17c3f587a16209876a9713881eff0034d872581e
workflow-type: tm+mt
source-wordcount: 457
ht-degree: 0%

---

# B2B-2598: Adiciona recurso de cache às consultas GraphQl `storeConfig`, `currency`, `country`, `countries` e `availableStores`

O patch B2B-2598 adiciona o recurso de cache às consultas GraphQl `storeConfig`, `currency`, `country`, `countries` e `availableStores`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é B2B-2598. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7-beta1.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As consultas GraphQL `availableStores`, `countries`, `country`, `currency`, `storeConfig` e `customAttributeMetadata` não podem ser armazenadas em cache.

<u>Pré-requisitos</u>:

* O servidor está apontando para o proxy [!DNL Varnish] para o back-end do Adobe Commerce.
* A configuração `system/full_page_cache/caching_application` está definida como *2* ([!DNL Varnish]), ou vá para Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > e defina-a como [!DNL Varnish].

Após a aplicação do patch, execute as seguintes etapas para garantir que o recurso de cache esteja disponível:

1. Envie a solicitação `GET` para qualquer uma das consultas GraphQL listadas acima, usando quaisquer campos arbitrários.
1. Reenviar a solicitação sem qualquer alteração. Você notará que é muito mais rápido. Observe que a solicitação não é enviada para o back-end, mas é completamente tratada por [!DNL Varnish] como uma ocorrência de cache.
1. Se for necessária mais prova, comente o unset do cabeçalho `X-Magento-Debug` presente em nosso [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), reinicie o [!DNL Varnish] e execute as etapas acima novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool]
