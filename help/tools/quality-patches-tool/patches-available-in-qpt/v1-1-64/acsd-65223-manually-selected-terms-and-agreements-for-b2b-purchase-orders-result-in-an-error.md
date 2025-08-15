---
title: 'ACSD-65223: os termos e contratos selecionados manualmente para ordens de compra B2B resultam em um erro'
description: Aplique o patch ACSD-65223 para corrigir o problema do Adobe Commerce em que os pedidos criados usando o [!UICONTROL Purchase Orders] não podem ser concluídos com métodos de pagamento online, como cartões de crédito, quando os termos e condições são necessários para o check-out.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-65223: os termos e contratos selecionados manualmente para ordens de compra B2B resultam em um erro

O patch ACSD-65223 corrige o problema em que os pedidos criados usando o **[!UICONTROL Purchase Orders]** não podem ser concluídos com métodos de pagamento online, como cartões de crédito, quando os termos e condições são necessários para o check-out. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65223.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) B2B 1.5.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) B2B 1.5.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Se os termos e condições forem necessários para fazer um pedido e você estiver tentando finalizá-lo usando o [!UICONTROL Purchase Orders], o pedido não poderá ser feito com métodos de pagamento online como cartões de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** e escolha **[!UICONTROL B2B Features]**.
1. Defina **[!UICONTROL Enable Company]** e **[!UICONTROL Enable Purchase Orders]** como *Sim*.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** e crie uma nova condição. Defina **[!UICONTROL Applied]** como *[!UICONTROL Manually]*.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** e defina **[!UICONTROL Enable Terms and Conditions]** como *Sim*.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** e configure [!DNL Braintree].
1. Na loja, crie uma empresa.
1. No admin, vá para **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.
1. Aprove a empresa e permita **[!UICONTROL Purchase Orders]**.
1. No front-end, faça logon na conta do.
1. Adicione um item ao carrinho.
1. Fazer um pedido usando **[!UICONTROL Purchase Order]**.
1. No painel do cliente, clique na guia **[!UICONTROL Purchase Orders]**.
1. Criar um pedido a partir da nova ordem de compra. Em seguida, selecione cartão de crédito como o método de pagamento.
1. Concordo com os termos e condições.
1. Coloque o pedido.

<u>Resultados esperados</u>:

Você pode colocar uma ordem usando um método de pagamento on-line em ordens de compra aprovadas quando os termos e condições são necessários para a finalização da compra.

<u>Resultados reais</u>:

Você não pode colocar um pedido usando um método de pagamento online em ordens de compra aprovadas quando os termos e condições são necessários para a finalização da compra.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
