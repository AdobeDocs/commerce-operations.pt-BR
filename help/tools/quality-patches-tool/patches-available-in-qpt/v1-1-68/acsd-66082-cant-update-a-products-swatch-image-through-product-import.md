---
title: 'ACSD-66082: não é possível atualizar a imagem de amostra de um produto por meio da importação do produto'
description: Aplique o patch ACSD-66082 para corrigir o problema do Adobe Commerce em que o upload de um arquivo CSV com o campo swatch_image definido como EMPTY_VALUE para desdefinir imagens de amostra faz com que o processo de importação falhe com um erro.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%
---
# ACSD-66082: não é possível atualizar a imagem de amostra de um produto por meio da importação do produto

O patch ACSD-66082 corrige o problema em que não era possível atualizar a imagem de amostra de um produto por meio da importação de produtos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-66082. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Carregar um arquivo CSV com o campo `swatch_image` definido como `EMPTY_VALUE` para desmarcar imagens de amostra faz com que o processo de importação falhe com um erro.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Clique na seta para baixo ao lado do botão **[!UICONTROL Add Product]** e escolha **[!UICONTROL Simple Product]**. Defina seu **[!UICONTROL SKU]** como *ABC*.
1. Carregue uma imagem PNG chamada *testing.png* para `var/import/images/`.
1. Crie um arquivo CSV com o seguinte conteúdo:

   ```text
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Vá para **[!UICONTROL System]** > **[!UICONTROL Import]** para importar o arquivo ajustando as seguintes configurações:
   * **[!UICONTROL Entity type]**: *Produtos*
   * **[!UICONTROL Import Behavior]**: *Adicionar/Atualizar*
   * Clique em **[!UICONTROL Choose File]** para selecionar o arquivo CSV criado na etapa anterior para importar. A importação foi bem-sucedida e a amostra foi adicionada.
1. Atualize o CSV com o seguinte conteúdo:

   ```text
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Repita o processo de importação.

<u>Resultados esperados</u>:

A imagem da amostra não está definida.

<u>Resultados reais</u>:

O processo de importação gera um erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
