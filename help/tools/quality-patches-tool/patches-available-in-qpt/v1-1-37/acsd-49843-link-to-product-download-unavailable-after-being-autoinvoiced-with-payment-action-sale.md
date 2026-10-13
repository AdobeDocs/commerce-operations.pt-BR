---
title: 'ACSD 49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Aplique o patch ACSD-49843 para corrigir o problema do Adobe Commerce em que o link de download do produto fica indisponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definido como [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '510'
ht-degree: 0%
---
# ACSD-49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

O patch ACSD-49843 corrige o problema em que o link de download do produto fica indisponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definido como [!UICONTROL Intent Sale]. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. A ID do patch é ACSD-49843. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O link de download do produto não estará disponível depois que o item solicitado for faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] estiver definido como [!UICONTROL Intent Sale].

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce e navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Na lista suspensa [!UICONTROL Payment Action], selecione **[!UICONTROL Intent Sale]** e defina *[!UICONTROL Enable Card Payments]* como *Sim*.

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** e verifique se está definido como *&quot;Faturado&quot;*.
1. Na loja, faça logon como cliente.

   * Adicione qualquer produto para download e um produto simples ao carrinho.
   * Use [!DNL Braintree Pay] para fazer o pedido usando a opção de cartão.

1. Vá para **[!UICONTROL My Orders]** e veja se a fatura é criada automaticamente para o pedido e se ambos os status dos itens são *&quot;Faturados&quot;*.
1. Vá para **[!UICONTROL My Downloadable Products]** e observe que o link de download ainda não está disponível.
1. Em Admin, vá para esse pedido e crie uma remessa para ele.
1. Na loja, vá para **[!UICONTROL My Downloadable Products]** e observe que o link de download agora está disponível.

<u>Resultados esperados</u>:

O link de download está disponível quando o status do produto para download é *&quot;Faturado&quot;*.

<u>Resultados reais</u>:

O link para download não está disponível mesmo quando o status do produto disponível para download indica *&quot;Faturado&quot;*. Ela só estará disponível depois que uma remessa for criada para o produto físico.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
