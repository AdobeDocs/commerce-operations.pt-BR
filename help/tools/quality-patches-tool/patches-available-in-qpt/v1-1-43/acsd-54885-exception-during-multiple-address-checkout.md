---
title: "ACSD-54885: exceção durante a finalização de vários endereços quando o administrador faz logon como cliente"
description: Aplique o patch ACSD-54885 para corrigir o problema do Adobe Commerce em que ocorre um erro durante a verificação de vários endereços quando o administrador está usando a funcionalidade *[!UICONTROL Login as Customer]*.
feature: Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885: exceção durante a finalização de vários endereços quando o administrador faz logon como cliente

O patch ACSD-54885 corrige o problema em que um erro ocorre durante o check-out de vários endereços quando o administrador está usando a funcionalidade *[!UICONTROL Login as Customer]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-54885. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro durante o check-out de vários endereços quando o administrador está usando a funcionalidade *[!UICONTROL Login as Customer]*.

<u>Etapas a serem reproduzidas</u>:

1. Certifique-se de que *[!UICONTROL Login as Customer]* esteja habilitado. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Crie um produto simples.
1. Crie uma nova conta de cliente com um endereço.
1. Vá para a conta do cliente no back-end:

   * Vá para a guia **[!UICONTROL Account Information]** e defina *[!UICONTROL Allow remote shopping assistance]* = *Sim*.
   * Clique em **[!UICONTROL Login as Customer]**.

1. Adicione o produto ao carrinho e prossiga para *[!UICONTROL Checkout with multiple addresses]*.
1. Atualize a quantidade do produto.
1. Tente voltar para o carrinho de compras.

<u>Resultados esperados</u>:

Você pode atualizar o carrinho e usar a finalização de vários endereços.

<u>Resultados reais</u>:

Você recebe o seguinte erro ao voltar ao carrinho de compras.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
