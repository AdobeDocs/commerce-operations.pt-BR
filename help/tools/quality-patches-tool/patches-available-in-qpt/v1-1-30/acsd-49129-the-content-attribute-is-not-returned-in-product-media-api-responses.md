---
title: 'ACSD-49129: o atributo "Conteúdo" não é retornado nas respostas da API de mídia do produto'
description: Aplique o patch ACSD-49129 para corrigir o problema do Adobe Commerce em que o atributo *content* (*código de imagem base64*) não é retornado nas respostas da API de mídia do produto "rest/V1/products/sku/media".
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
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
1. Envie a solicitação da *API REST do GET* para `rest/V1/products/<sku>/media` e `rest/V1/products/<sku>/media/<entryId>`.
1. Verifique as respostas da API.

<u>Resultados esperados</u>

O atributo *content* com os dados está disponível via API REST.

<u>Resultados reais</u>

O atributo *content* não está presente nas respostas da API.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
