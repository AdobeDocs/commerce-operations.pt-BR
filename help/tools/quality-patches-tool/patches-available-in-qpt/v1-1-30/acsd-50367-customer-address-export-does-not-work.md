---
title: 'ACSD-50367: a exportação de endereço do cliente não funciona com o atributo de seleção múltipla'
description: Aplique o patch ACSD-50367 para corrigir o problema do Adobe Commerce em que a exportação de endereço do cliente não funciona quando um atributo de seleção múltipla **&grave;Endereço do cliente&grave;** sem valores é criado.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367: a exportação de endereço do cliente não funciona

O patch ACSD-50367 corrige o problema em que a exportação de endereço do cliente não funciona quando um atributo **`Customer Address`** de seleção múltipla sem valores é criado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é ACSD-50367. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de endereço do cliente não funciona quando um atributo de seleção múltipla **`Customer Address`** sem valores é criado.

<u>Pré-requisitos</u>:

Crie um cliente com um endereço.

<u>Etapas a serem reproduzidas</u>:

1. Criar um atributo de seleção múltipla **`Customer Address`** em **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** e selecione **`Customer Address`** tipo de entidade.
1. Exporte os endereços do cliente. Você verá que nada é exportado.
1. Exclua o atributo de seleção múltipla **`Customer Address`** e exporte os endereços do cliente novamente. Dessa vez, o arquivo CSV dos endereços é gerado.

<u>Resultados esperados</u>:

Os endereços do cliente podem ser exportados como um arquivo CSV quando um atributo de seleção múltipla **`Customer Address`** é criado.

<u>Resultados reais</u>:

Os endereços do cliente não podem ser exportados como um arquivo CSV quando um atributo de seleção múltipla **`Customer Address`** é criado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
