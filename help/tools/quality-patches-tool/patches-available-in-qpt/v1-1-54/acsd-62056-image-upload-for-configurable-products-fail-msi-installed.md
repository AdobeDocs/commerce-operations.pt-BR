---
title: 'ACSD-62056: o upload de imagem para o produto configurável falha se o MSI estiver instalado'
description: Aplique o patch ACSD-62056 para corrigir o problema do Adobe Commerce em que imagens de produtos configuráveis não são adicionadas se o MSI estiver instalado.
feature: Products, Media
role: Admin, Developer
source-git-commit: 9c186e936492ebcab3903949f40d73745d2a28d3
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: o upload de imagem para o produto configurável falha se o MSI estiver instalado

O patch ACSD-62056 corrige o problema em que imagens de produtos configuráveis não são adicionadas se o MSI estiver instalado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-62056. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao editar um produto configurável com o [!UICONTROL Inventory Management/MSI] habilitado, as opções para adicionar imagens não funcionam. Isso afeta as opções [!UICONTROL Apply a single set of images to all SKUs] e [!UICONTROL Apply unique images by attribute to each SKU].

<u>Pré-requisitos</u>:

[!UICONTROL Inventory Management/MSI] módulos estão instalados e habilitados.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova fonte.
1. Crie um novo estoque e atribua a nova fonte.
1. Edite um produto configurável.
1. Clique em **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Selecione uma das opções a seguir e adicione uma imagem.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Resultados esperados</u>:

As imagens são adicionadas.

<u>Resultados reais</u>:

As imagens não estão sendo adicionadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
