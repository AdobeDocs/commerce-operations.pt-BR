---
title: "ACSD-52160: resultado da validação do produto em relação à regra de preço do carrinho"
description: Aplique o patch ACSD-52160 para corrigir o problema do Adobe Commerce em que o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição da regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160: o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente

O patch ACSD-52160 corrige o problema em que o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição de regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 está instalado. A ID do patch é ACSD-52160. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição de regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos atribuídos a duas categorias diferentes.
1. Criar um **[!UICONTROL Cart Price Rule]** com condições como:

   * **SKU 1** no parâmetro *[!UICONTROL FOUND]*
   * **SKU 2** no parâmetro *[!UICONTROL NOT FOUND]*

1. Adicione ambos os produtos ao carrinho.
1. Aplique o código do cupom.

<u>Resultados esperados</u>

O código do cupom não é aplicado, pois o carrinho contém produtos da categoria restrita.

<u>Resultados reais</u>

O código do cupom é aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](</help/tools/quality-patches-tool/usage.md>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
