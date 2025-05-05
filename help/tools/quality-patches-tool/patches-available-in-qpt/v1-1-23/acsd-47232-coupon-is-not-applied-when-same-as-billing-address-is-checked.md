---
title: 'ACSD-47232: o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado'
description: Aplique o patch ACSD-47232 para corrigir o problema do Adobe Commerce em que o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado.
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232: o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado

O patch ACSD-47232 corrige o problema em que o cupom não é aplicado quando **[!UICONTROL Same as Billing Address]** é marcado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 está instalado. A ID do patch é ACSD-47232. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cupom não é aplicado quando **[!UICONTROL Same as Billing Address]** está marcado.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Crie um produto simples com peso = *8*.
1. Crie um novo cliente com faturamento e endereço de entrega padrão.
1. Crie uma regra de preço de carrinho com um cupom.
   * Em **[!UICONTROL Conditions]** seções, adicione *Peso Total igual ou maior que 5*
1. Tente criar um novo pedido no Administrador [!UICONTROL Commerce].
   * Use o cliente criado agora mesmo
   * Adicionar um produto
   * Tente aplicar o cupom

<u>Resultados esperados</u>:

Cupom aplicado.

<u>Resultados reais</u>:

Você recebe um erro semelhante ao seguinte: *O código do cupom 123 não é válido. Verifique o código e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
