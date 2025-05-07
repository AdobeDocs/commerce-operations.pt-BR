---
title: 'ACSD-63520: imagens carregadas por meio da Configuração de carregamento de imagem excedem os limites de tamanho configurados'
description: Aplique o patch ACSD-63520 para corrigir o problema do Adobe Commerce em que as Imagens carregadas por meio da Configuração de carregamento de imagens no painel de Administração não aderem aos limites de tamanho máximo de upload configurados.
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520: Imagens carregadas por meio de [!UICONTROL Image Upload Configuration] excedem os limites de tamanho configurados

O patch ACSD-63520 resolve um problema em que imagens carregadas por meio do [!UICONTROL Images Upload Configuration] não aderem aos limites de tamanho máximo de upload configurados. Para resolver isso, defina as configurações de [!UICONTROL Images Upload Configuration] no painel [!UICONTROL Admin]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 está instalado. A ID do patch é ACSD-63520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com sua versão [!DNL Adobe Commerce], atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens carregadas por meio do [!UICONTROL Images Upload Configuration] no painel [!UICONTROL Admin] não aderem ao limite de tamanho máximo de carregamento.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel **[!UICONTROL Admin]**.
1. Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** e defina:
   * Qualidade: 100
   * Ativar redimensionamento de front-end: Sim
   * Largura máxima: 800
   * Altura Máxima: 600
1. Expandir **[!UICONTROL Media Gallery Image Optimization]** e definir:
   * Ativar otimização de imagem: Sim
   * Largura máxima: 1000
   * Altura Máxima: 1000
1. Navegue até **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. Adicionar **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** e **[!UICONTROL Price]**.
   1. Clique em **[!UICONTROL Create Configurations]**, selecione **[!UICONTROL Attributes]** e clique em **[!UICONTROL Next]**.
   1. Escolha os tamanhos (S, M, L, XL) e clique em **[!UICONTROL Next]**.
   1. Em **[!UICONTROL Images]**, selecione **[!UICONTROL Apply single set of images to all SKUs]**.
   1. Carregue uma imagem (mínimo 1024x1024), clique em **[!UICONTROL Next]**.
   1. Clique em **[!UICONTROL Generate Product]**.
1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

As imagens devem seguir os limites configurados de tamanho e redimensionamento do upload.

<u>Resultados reais</u>:

As imagens não são redimensionadas e excedem os limites de tamanho de upload configurados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
