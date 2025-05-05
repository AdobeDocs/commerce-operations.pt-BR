---
title: 'ACSD-63469: descontos de carrinho de valor fixo não aplicados corretamente com várias regras'
description: Aplique o patch ACSD-63469 para corrigir o problema do Adobe Commerce, em que os descontos de quantia fixa para todo o carrinho não são aplicados corretamente quando mais de uma regra é aplicada.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469: descontos de carrinho de valor fixo não aplicados corretamente com várias regras

O patch ACSD-63469 corrige o problema em que os descontos de valor fixo para todo o carrinho não se aplicam corretamente quando mais de uma regra é aplicada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-63469. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando várias regras **[!UICONTROL Fixed amount discount for whole cart]** são aplicadas simultaneamente e os produtos têm preços especiais ou com desconto, o valor do desconto é calculado incorretamente.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos com preços de US$ 850 e US$ 85 e defina seus preços especiais como US$ 765 e US$ 68, respectivamente.
1. Crie dois **[!UICONTROL Cart Price Rules]** da seguinte maneira:
   * Regra 1
      * **[!UICONTROL Conditions]**: Para o produto de $850, defina *Qtd* como *igual ou maior que 2*
      * **[!UICONTROL Actions]**: Aplicar **[!UICONTROL Fixed amount discount for whole cart]** de *$153*
   * Regra 2
      * **[!UICONTROL Conditions]**: Para o produto de $85, defina *Qtd* como *igual ou maior que 2*
      * **[!UICONTROL Actions]**: Aplicar **[!UICONTROL Fixed amount discount for whole cart]** de *$14*
1. Adicione ambos os produtos ao carrinho, cada um com uma quantidade de 2.

<u>Resultados esperados</u>:

O desconto aplicado no carrinho é de US$ 167.

<u>Resultados reais</u>:

O desconto aplicado no carrinho é de US$ 41.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Etapas adicionais necessárias após a instalação do patch

(Esta seção é opcional; pode haver algumas etapas necessárias após a aplicação do patch para corrigir o problema.) 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

