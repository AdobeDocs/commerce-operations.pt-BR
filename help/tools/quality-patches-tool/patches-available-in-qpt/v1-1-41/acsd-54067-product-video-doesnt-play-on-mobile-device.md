---
title: 'ACSD-54067: o vídeo do produto não é reproduzido no dispositivo móvel'
description: Aplique o patch ACSD-54067 para corrigir o problema do Adobe Commerce em que um vídeo de produto não é reproduzido em um dispositivo móvel.
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067: o vídeo do produto não é reproduzido em um dispositivo móvel

O patch ACSD-54067 corrige o problema em que um vídeo de produto não é reproduzido em um dispositivo móvel. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 está instalado. A ID do patch é ACSD-54067. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um vídeo de produto não é reproduzido em um dispositivo móvel.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Execute o comando:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Vá para a página **[!UICONTROL Admin product list]** e filtre por *[!UICONTROL SKU product_dynamic_120]*.
1. Abra a página do produto e acesse **[!UICONTROL Images and Videos]** > adicionar um vídeo > preencher o URL: https://vimeo.com/347119375 e salve.
1. Vá para a loja e abra a página do produto para *[!UICONTROL product_dynamic_120]*.
1. Defina o navegador como *dispositivo móvel* com largura de *320px* e atualize.
1. No controle deslizante da galeria, selecione o vídeo e clique para reproduzi-lo.

<u>Resultados esperados</u>:

O vídeo do produto é reproduzido.

<u>Resultados reais</u>:

O vídeo do produto não é reproduzido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
