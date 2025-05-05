---
title: 'ACSD-50814: O usuário administrador não pode criar memorando de crédito'
description: Aplique o patch ACSD-50814 para corrigir o problema do Adobe Commerce em que um usuário administrador não pode criar um memorando de crédito.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: 87ee7166-7492-4948-9a85-a183ecf54fa7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-50814: o usuário administrador não pode criar memorando de crédito

O patch ACSD-50814 corrige o problema em que um usuário administrador não consegue criar um memorando de crédito. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é ACSD-50814. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um usuário administrador não pode criar um memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** e defina **[!UICONTROL Enable free shipping]** como *[!UICONTROL Yes]*
1. Novamente vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**, expanda as configurações de cálculo e defina:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. Expanda as configurações de exibição de preço e defina o [!UICONTROL Display shipping prices] = [!UICONTROL Including tax].
1. Expanda as configurações de exibição [!UICONTROL Orders], [!UICONTROL Invoices], [!UICONTROL Credit memo] e defina [!UICONTROL Display shipping amount] = [!UICONTROL Including tax].
1. Limpar caches.
1. Faça um pedido na vitrine.
1. Crie uma fatura para o pedido no administrador.
1. Crie um memorando de crédito.

<u>Resultados esperados</u>:

O memorando de crédito é criado.

<u>Resultados reais</u>:

O seguinte erro é lançado:

*A página não pode ser exibida devido ao erro*

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
