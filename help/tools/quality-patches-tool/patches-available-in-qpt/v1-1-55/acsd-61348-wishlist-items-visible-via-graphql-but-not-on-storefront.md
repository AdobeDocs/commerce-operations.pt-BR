---
title: 'ACSD-61348: itens da lista de desejos visíveis via GraphQL, mas não na loja'
description: Aplique o patch ACSD-61348 para corrigir o problema do Adobe Commerce em que os itens da lista de desejos são visíveis por meio do GraphQL, mas não na loja em um ambiente de vários sites.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: itens da lista de desejos visíveis via GraphQL, mas não na loja

O patch ACSD-61348 corrige o problema em que os itens da lista de desejos são visíveis por meio do GraphQL, mas não na loja em um ambiente com vários sites. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-61348. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens da lista de desejos são visíveis por meio do GraphQL, mas não na loja em um ambiente com vários sites.

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites.
1. Vá para **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** e defina **[!UICONTROL Share Customer Accounts]** como *[!UICONTROL Global]*.
1. Vá para **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** e defina **[!UICONTROL Enable Multiple Wish Lists]** como *Sim*.
1. Vá para **[!UICONTROL Config General]** > **[!UICONTROL Web]** e defina **[!UICONTROL Add Store Code to URLs]** como *Sim*.
1. Crie um produto simples e atribua-o ao segundo site.
1. Crie um cliente e faça logon.
1. Adicione um produto à lista de desejos.
1. Atribua o produto ao site padrão.
1. Vá para a página *[!UICONTROL Wishlist]* no site padrão.

<u>Resultados esperados</u>:

O produto está na lista de desejos.

<u>Resultados reais</u>:

Não há produtos na lista de desejos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
