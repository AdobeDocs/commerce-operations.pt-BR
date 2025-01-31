---
title: 'ACSD-63299: Preço especial de um produto configurável não é exibido na vitrine'
description: Aplique o patch ACSD-63299 para corrigir o problema do Adobe Commerce em que o atributo de preço especial não afeta mais a exibição de preços especiais para produtos configuráveis.
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: Preço especial de um produto configurável não é exibido na vitrine

O patch ACSD-63299 corrige o problema em que o atributo de preço especial não afeta mais a exibição de preços especiais para produtos configuráveis. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63299. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Em [!DNL Adobe Commerce], alterar o valor de *Usado na Lista de Produtos* para o atributo de preço especial não afeta mais como os preços especiais são exibidos para os produtos configuráveis.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Localize o atributo ***[!UICONTROL special_price]*** e navegue até **[!UICONTROL Storefront Properties]**.
1. Alterar ***[!UICONTROL Used in Product Listing]*** para ***[!UICONTROL No]***.
1. Crie um produto configurável com um secundário:
   * Nome e SKU: Teste
   * Preço: US$ 159,00
   * Gerar opção com base na cor. Adicione uma nova cor: Azul
   * Salvar
1. Abra o produto filho e siga estas etapas:
   * Defina um preço especial para US$ 99,90 em **[!UICONTROL Advanced Pricing]**
   * Alterar [!UICONTROL Visibility] para **[!UICONTROL Catalog, Search]**.
1. Abra a página do produto simples e confirme se o preço especial está visível.
1. Abra a página do produto configurável.
1. Selecione o produto azul.

<u>Resultados esperados</u>:

Preço especial é visível da mesma forma que é para o produto simples.

<u>Resultados reais</u>:

1. O preço total é exibido quando um produto configurável é selecionado.
1. Há uma incompatibilidade entre as seções *As low as...* ($99,90) e o preço real ($99,90 + $59,10 = $159,00).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
