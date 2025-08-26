---
title: 'ACP2E-4050: [!UICONTROL Free Shipping] não aplicado com check-out de vários envios'
description: Aplique o patch ACP2E-4050 para corrigir o problema do Adobe Commerce em que [!UICONTROL Free Shipping] não é aplicado durante o check-out de vários endereços quando [!UICONTROL Cart Price Rules] inclui condições de subseleção e produtos com preços específicos.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]** não aplicado com check-out de vários envios

O patch ACP2E-4050 corrige o problema em que **[!UICONTROL Free Shipping]** não é aplicado durante o check-out de vários envios quando **[!UICONTROL Cart Price Rules]** inclui condições de subseleção e produtos com preços específicos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACP2E-4050. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p10

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

**[!UICONTROL Free Shipping]** não é aplicado durante o check-out de remessas múltiplas quando **[!UICONTROL Cart Price Rules]** inclui condições de subseleção e produtos com preços específicos.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente com dois endereços.
1. Habilitar **[!UICONTROL Free Shipping]** e definir **[!UICONTROL Minimum Order Amount]** como *999999*.
1. Navegue até [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] e crie uma regra de preço de carrinho com as seguintes condições:

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Instalar dados de amostra.
1. Adicione os seguintes produtos ao carrinho na ordem especificada:
   * Mala de mensageiro Wayfarer
   * Olivia 1/4 Zip Light Jacket
   * Sprite Yoga Companion Kit.
1. Abra o carrinho de compras e verifique se a opção **[!UICONTROL Free Shipping]** está disponível.
1. Clique em **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selecione um endereço de entrega diferente para o produto simples.
1. Clique em **[!UICONTROL Go to Shipping Information]**.

<u>Resultados esperados</u>:

**[!UICONTROL Free Shipping]** aplica-se a remessas de produtos configuráveis e agrupados.

<u>Resultados reais</u>:

**[!UICONTROL Free Shipping]** não está disponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
