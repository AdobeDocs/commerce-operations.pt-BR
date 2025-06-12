---
title: 'ACSD-53378: experiência de check-out aprimorada para clientes com catálogos de endereços extensos'
description: Aplique o patch ACSD-53378 para corrigir o problema do Adobe Commerce em que há problemas de desempenho causados por grandes volumes de endereços de clientes.
feature: Customers, Checkout
role: Admin
exl-id: 699d09fe-872f-44d3-88bb-b5b585e15067
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-53378: experiência de check-out aprimorada para clientes com catálogos de endereços extensos

O patch ACSD-53378 corrige o problema em que há problemas de desempenho causados por grandes volumes de endereços de clientes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 está instalado. A ID do patch é ACSD-53378. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho do Adobe Commerce fica muito lento se um cliente tiver um grande número de endereços.

Se a opção de configuração *[!UICONTROL Enable search address]* em **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** estiver ativada, o catálogo de endereços completo do cliente não será mais submetido ao processamento completo. O número de endereços de clientes processados é determinado pela configuração *[!UICONTROL Customer Addresses Limit]* em **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples do Administrador.
1. Crie um cliente com um catálogo de endereços extenso contendo 1000 endereços.
1. Navegue até o front-end e adicione o produto ao carrinho.
1. Abra a página do carrinho de compras.

<u>Resultados esperados</u>:

A contagem de endereços do cliente não afeta o tempo de resposta.

<u>Resultados reais</u>:

A página do carrinho de compras leva muito tempo para carregar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
