---
title: 'ACP2E-3789: Arquivos de mídia duplicados na atualização do produto via WebAPI'
description: Aplique o patch ACP2E-3789 para corrigir o problema do Adobe Commerce em que as atualizações de produto por meio de arquivos de mídia duplicados da WebAPI quando uma ID de mídia é fornecida.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789: Arquivos de mídia duplicados na atualização do produto via WebAPI

O patch ACP2E-3789 corrige o problema em que o produto atualiza por meio de arquivos de mídia duplicados da WebAPI quando uma ID de mídia é fornecida. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACP2E-3789. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Atualizar um produto via WebAPI com uma ID de mídia faz com que o sistema duplique os arquivos de mídia em vez de substituí-los, criando novos arquivos a cada chamada de API e resultando em um acúmulo de imagens que sobrecarrega o diretório `/pub/media/catalog/products/cache/`.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto e adicione uma imagem.
1. Obter detalhes do produto usando a API REST em `base_url/rest/V1/products/<sku>`.
1. Execute uma solicitação PUT para atualizar o produto, mantendo os `media_gallery_entrie`s inalterados (mesmo nome de imagem e arquivo).
1. Verifique o diretório `pub/media/catalog/product/xx/yy` antes e depois da atualização.

<u>Resultados esperados</u>:

O arquivo de imagem é substituído quando a ID de mídia é incluída na solicitação.

<u>Resultados reais</u>:

A imagem é duplicada com um novo nome (por exemplo, wb04-blue-1.jpg), causando a criação desnecessária do arquivo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
