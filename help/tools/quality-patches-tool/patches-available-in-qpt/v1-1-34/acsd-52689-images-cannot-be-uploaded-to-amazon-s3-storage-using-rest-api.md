---
title: 'ACSD-52689: as imagens não podem ser carregadas no armazenamento do Amazon S3 por meio da API REST'
description: Aplique o patch ACSD-52689 para corrigir o problema do Adobe Commerce em que as imagens não podem ser carregadas para o armazenamento do Amazon S3 por meio da API REST.
feature: REST, Storage, Iaas
role: Admin
exl-id: 4d7a8ea7-2856-4b40-a922-fdd356dcaea4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: df5e974b-6742-4873-a687-a6bedaafdaa2
    internal-label: IaaS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# ACSD-52689: as imagens não podem ser carregadas no armazenamento do Amazon S3 por meio da API REST

O patch ACSD-52689 corrige o problema em que as imagens não podem ser carregadas para o armazenamento do Amazon S3 usando a API REST. Esse patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. A ID do patch é ACSD-52689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens não podem ser carregadas no armazenamento do Amazon S3 usando a API REST

<u>Etapas a serem reproduzidas</u>:

1. Configure o REMOTE_STORAGE para o bucket do Amazon S3.
1. Adicione uma imagem ao produto usando a API em massa.

   `POST .../rest/all/async/bulk/V1/products/bySku/media`

   ```text
   [
       {
           "sku": "p1",
           "entry": {
               "media_type": "image",
               "position": 0,
               "disabled": false,
               "types": [
                   "image",
                   "thumbnail",
                   "small_image",
                   "swatch_image"
               ],
               "content": {
                "type": "image\/jpeg",
                   "name": "adobe_commerce_test_3",
                   "base64_encoded_data": "/9j/4AAQSkZJRgABAQAAAQABA..."
               }
           }
       }
   ]
   ```

1. Aguarde o processamento da operação em massa.

<u>Resultados esperados</u>

A imagem deve ser carregada no bucket do Amazon S3.

<u>Resultados reais</u>

O upload da imagem não é feito automaticamente no bucket do Amazon S3.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
