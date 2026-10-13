---
title: 'ACSD-62146: o endereço de faturamento selecionado desaparece na página de pagamento do check-out'
description: Aplique o patch ACSD-62146 para corrigir o problema do Adobe Commerce em que o endereço de faturamento selecionado desaparece na página de pagamento de check-out quando a pesquisa de endereço estiver ativada e o Limite de número de endereços do cliente estiver definido como 1.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 2a2f1afe-8a48-4beb-b78d-a894b685717d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-62146: o endereço de faturamento selecionado desaparece na página de pagamento do check-out

O patch ACSD-62146 corrige o problema em que o endereço de cobrança selecionado desaparece na página de pagamento de check-out quando a pesquisa de endereço está habilitada e o [!UICONTROL Number of Customer Addresses Limit] está definido como 1. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-62146. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O endereço de cobrança selecionado desaparece na página de pagamento do check-out quando a pesquisa de endereço está habilitada e o **[!UICONTROL Number of Customer Addresses Limit]** está definido como 1.

<u>Etapas a serem reproduzidas</u>:

1. Para habilitar a Pesquisa de Endereço, vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
1. Defina **[!UICONTROL Number of Customer Addresses Limit]** como 1.
1. Crie um cliente e adicione dois endereços diferentes.
1. Adicione um produto ao carrinho e prossiga para a finalização da compra.
1. Clique em **[!UICONTROL Change Address]** e use o pop-up para alterar o endereço.
1. Selecione Endereço 2 como o endereço de entrega.
1. Clique em **[!UICONTROL Next]** para prosseguir para a etapa de pagamento.
1. Verifique se o endereço de faturamento e de entrega são iguais.
1. Atualizar a página sem efetuar o pagamento.

<u>Resultados esperados</u>:

O endereço de entrega fica visível quando os endereços de faturamento e de entrega são iguais.

<u>Resultados reais</u>:

O endereço de cobrança padrão e o endereço de entrega selecionado não estão visíveis.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
