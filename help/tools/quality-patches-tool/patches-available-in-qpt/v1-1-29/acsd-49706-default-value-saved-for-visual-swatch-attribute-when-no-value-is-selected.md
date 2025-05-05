---
title: 'ACSD-49706: Valor padrão salvo para o atributo de amostra visual quando nenhum valor é selecionado'
description: Aplique o patch ACSD-49706 para corrigir o problema do Adobe Commerce em que um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: Valor padrão salvo para o atributo de amostra visual quando nenhum valor é selecionado

O patch ACSD-49706 corrige o problema em que um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49706. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Clique em **[!UICONTROL Add New Attribute]**.
1. Preencha os campos.

   * Por exemplo, escolha o tipo de entrada *[!UICONTROL Visual Swatch]* e adicione várias opções (como *Vermelho*, *Verde*). Escolha uma dessas opções como padrão.
   * Clique em **[!UICONTROL Save Attribute]**.

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Edite o conjunto de atributos *[!UICONTROL Default]*.
1. Mover *[!UICONTROL New Attribute]* da coluna *[!UICONTROL Unassigned Attributes]* para a pasta *[!UICONTROL Product Details]* na coluna do meio.

   * Clique em **[!UICONTROL Save]**.

1. Crie um novo produto usando o conjunto de atributos *[!UICONTROL Default]*.

   * Deixe o *[!UICONTROL New Attribute]* vazio e salve-o.

1. Depois de salvo, um valor aparece em *[!UICONTROL New Attribute]*.

<u>Resultados esperados</u>:

Nenhum valor é atribuído a *[!UICONTROL New Attribute]* por padrão.

<u>Resultados reais</u>:

Um valor padrão é aplicado ao atributo ao salvar um produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
