---
title: 'ACSD-47137: melhorar a velocidade de carregamento da galeria de imagens na pasta "pub/media" big'
description: Aplique o patch ACSD-47137 para melhorar a velocidade de carregamento da galeria de imagens quando a pasta "pub/media" for muito grande.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: melhorar a velocidade de carregamento da galeria de imagens quando a pasta `pub/media` for grande

O patch ACSD-47137 melhora a velocidade de carregamento da galeria de imagens quando a pasta `pub/media` é muito grande. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-47137. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A velocidade de carregamento da galeria de imagens fica lenta quando a pasta `pub/media` é muito grande.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Administrador do Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** to _Não_.
1. Limpe o cache de configuração.
1. Saia e faça logon como usuário administrador novamente.
1. Na barra lateral Admin, vá para **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e selecione a categoria raiz.
1. Expanda a seção **[!UICONTROL Content]** e clique em **[!UICONTROL Select from Gallery]**.

Ao carregar a página, o Adobe Commerce envia a solicitação `media_gallery/directories/gettree` para carregar a árvore de pastas de mídia.

<u>Resultados esperados</u>:

A solicitação `media_gallery/directories/gettree` deve carregar o conteúdo somente dos diretórios necessários, além de executar um loop em toda a lista de caminhos da pasta `pub/media/`.

<u>Resultados reais</u>:

A solicitação `media_gallery/directories/gettree` leva muito tempo para carregar quando a pasta `pub/media/` tem muito conteúdo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
