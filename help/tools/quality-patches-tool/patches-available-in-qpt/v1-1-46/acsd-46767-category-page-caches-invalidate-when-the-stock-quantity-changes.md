---
title: "ACSD-46767: os caches de página [!UICONTROL Category] são invalidados quando a quantidade em estoque é alterada"
description: Aplique o patch ACSD-46767 para corrigir o problema do Adobe Commerce em que os caches de página do [!UICONTROL Category] são invalidados quando a quantidade em estoque é alterada, mesmo que o produto ainda esteja em estoque.
feature: Cache, Products, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] os caches de página são invalidados quando a quantidade em estoque é alterada

O patch ACSD-46767 corrige o problema em que os caches de página [!UICONTROL Category] são invalidados quando a quantidade em estoque é alterada, mesmo que o produto ainda esteja em estoque. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 está instalado. A ID do patch é ACSD-46767. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os caches de página [!UICONTROL Category] são invalidados quando a quantidade de estoque é alterada.

<u>Etapas a serem reproduzidas</u>:

1. Crie alguns produtos e adicione-os à mesma categoria.
1. Abra a página *[!UICONTROL Category]* na loja para garantir que a página seja armazenada em cache.
1. Fazer o pedido com um dos produtos da categoria *(a quantidade do produto é alterada, mas o produto ainda está no estoque)*.
1. Abra a página [!UICONTROL Category] na loja novamente.

<u>Resultados Reais</u>:

A página não é carregada do cache. Ela é gerada novamente.

<u>Resultados Esperados</u>:

A página é carregada do cache.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
