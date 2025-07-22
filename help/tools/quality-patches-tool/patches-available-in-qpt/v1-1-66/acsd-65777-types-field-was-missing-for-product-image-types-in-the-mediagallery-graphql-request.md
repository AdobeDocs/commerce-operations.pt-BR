---
title: 'ACSD-65777: campo "tipos" ausente para tipos de imagem de produto na solicitação do GraphQL "MediaGallery"'
description: Aplique o patch ACSD-65777 para corrigir o problema do Adobe Commerce em que o campo "tipos" estava ausente para tipos de imagem de produto na solicitação do GraphQL "MediaGallery".
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777: campo **[!UICONTROL types]** ausente para tipos de imagem de produto na solicitação do GraphQL `MediaGallery`

O patch ACSD-65777 corrige o problema em que o campo **[!UICONTROL types]** estava ausente para tipos de imagem de produto na solicitação do GraphQL `MediaGallery`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-65777. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O campo **[!UICONTROL types]** está ausente para tipos de imagem de produto ao buscar dados de mídia por meio da solicitação do GraphQL `MediaGallery`.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto.
1. Faça upload de uma imagem no produto.
1. Busque os dados de mídia usando o seguinte GraphQL.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

A interface do GraphQL `media_gallery` deve incluir o campo **[!UICONTROL types]**.

<u>Resultados reais</u>:

O `media_gallery` não contém o campo de mídia **[!UICONTROL types]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
