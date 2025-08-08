---
title: 'ACSD-66082: não é possível atualizar a imagem de amostra de um produto por meio da importação do produto'
description: Aplique o patch ACSD-66082 para corrigir o problema do Adobe Commerce em que o upload de um arquivo CSV com o campo swatch_image definido como EMPTY_VALUE para desdefinir imagens de amostra faz com que o processo de importação falhe com um erro.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Carregar um arquivo CSV com o campo `swatch_image` definido como `EMPTY_VALUE` para desmarcar imagens de amostra faz com que o processo de importação falhe com um erro.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Clique na seta para baixo ao lado do botão **[!UICONTROL Add Product]** e escolha **[!UICONTROL Simple Product]**. Defina seu **[!UICONTROL SKU]** como *ABC*.
1. Carregue uma imagem PNG chamada *testing.png* para `var/import/images/`.
1. Crie um arquivo CSV com o seguinte conteúdo:

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Vá para **[!UICONTROL System]** > **[!UICONTROL Import]** para importar o arquivo ajustando as seguintes configurações:
   * **[!UICONTROL Entity type]**: *Produtos*
   * **[!UICONTROL Import Behavior]**: *Adicionar/Atualizar*
   * Clique em **[!UICONTROL Choose File]** para selecionar o arquivo CSV criado na etapa anterior para importar. A importação foi bem-sucedida e a amostra foi adicionada.
1. Atualize o CSV com o seguinte conteúdo:

   ```
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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
