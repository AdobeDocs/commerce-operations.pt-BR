---
title: 'ACSD-48773: modelo de email de pontos de recompensa retirado da loja errada'
description: Aplique o patch ACSD-48773 para corrigir o problema do Adobe Commerce em que o modelo de email de pontos de premiação é retirado da loja errada.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%
---
# ACSD-48773: modelo de email de pontos de recompensa retirado da loja errada

O patch ACSD-48773 corrige o problema em que o modelo de email de pontos de premiação é retirado do armazenamento errado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-48773. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação do preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.

<u>Etapas a serem reproduzidas</u>:

1. Crie 2 sites, 2 lojas e 2 visualizações de loja.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** e habilite **[!UICONTROL Reviews]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Alterne para **[!DNL default website scope]** e defina o endereço **[!UICONTROL Customer Support Sender Email]**, (Por exemplo: *support_base@example.com*).
Alterne para **[!DNL second website scope]** e defina o endereço **[!UICONTROL Customer Support Sender Email]** com outro valor (Por exemplo: *support_second@example.com*).
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** e defina **[!UICONTROL Share Customer Accounts]** = *Por Site*.
1. Em **[!UICONTROL Reward Points]**, defina o seguinte:
   **[!UICONTROL Enable Reward Points Functionality]** = *Sim*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Sim*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** e conjunto **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** e definir **[!UICONTROL Email Sender]** = *Suporte ao Cliente*
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e configure as taxas de câmbio para o segundo site para **[!UICONTROL Points/Currency]** e **[!UICONTROL Currency/Points]**.
1. Crie uma conta de cliente no segundo site.
1. Faça logon como o cliente no segundo site.
1. Habilite **[!UICONTROL Subscribe]** para **[!UICONTROL Balance Updates]**.
1. Envie uma análise do produto.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Alterar o status da nova revisão para ***[!UICONTROL Approved]*** e **[!UICONTROL Save]**.
1. Aguarde a chegada do email.

<u>Resultados esperados</u>:

O email de atualização dos pontos de premiação deve ter sido enviado pelo remetente do email configurado no escopo do segundo site.

<u>Resultados reais</u>:

O email de atualização de pontos de premiação foi enviado pelo remetente de email configurado no escopo padrão do site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
