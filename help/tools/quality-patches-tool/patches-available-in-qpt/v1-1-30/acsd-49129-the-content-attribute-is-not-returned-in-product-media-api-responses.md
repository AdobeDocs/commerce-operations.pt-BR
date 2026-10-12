---
title: 'ACSD-49129: o atributo "Conteúdo" não é retornado nas respostas da API de mídia do produto'
description: Aplique o patch ACSD-49129 para corrigir o problema do Adobe Commerce em que o atributo *content* (*código de imagem base64*) não é retornado nas respostas da API de mídia do produto "rest/V1/products/sku/media".
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%
---
# ACSD-49129: o atributo &quot;Conteúdo&quot; não é retornado nas respostas da API de mídia do produto

O patch ACSD-49129 corrige o problema em que o atributo (*[!UICONTROL base64 image code]*) *content* não é retornado nas respostas da API de mídia do produto `rest/V1/products/sku/media`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.30 está instalado. A ID do patch é ACSD-49129. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O atributo *content* (*[!UICONTROL base64 image code]*) não é retornado nas respostas da API de mídia do produto `rest/V1/products/sku/media`.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com uma imagem.
1. Enviar solicitação *GET REST API* para `rest/V1/products/<sku>/media` e `rest/V1/products/<sku>/media/<entryId>`.
1. Verifique as respostas da API.

<u>Resultados esperados</u>

O atributo *content* com os dados está disponível via API REST.

<u>Resultados reais</u>

O atributo *content* não está presente nas respostas da API.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
