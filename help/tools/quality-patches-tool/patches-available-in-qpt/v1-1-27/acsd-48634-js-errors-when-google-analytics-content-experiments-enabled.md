---
title: 'ACSD-48634: [!DNL JS] erros quando [!DNL Google Analytics Content Experiments] habilitado'
description: Aplique o patch ACSD-48634 para corrigir [!DNL JS] erros em uma página de atualização [!DNL staging] quando [!DNL Google Analytics Content Experiments] estiver habilitado.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] erros quando [!DNL Google Analytics Content Experiments] está habilitado

O patch ACSD-48634 corrige [!DNL JS] erros em uma página de atualização [!DNL staging] quando [!DNL Google Analytics Content Experiments] está habilitado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 está instalado. A ID do patch é ACSD-48634. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os erros [!DNL JS] ocorrem em uma página de atualização [!DNL staging] quando [!DNL Google Analytics Content Experiments] está habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Em **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, crie um site, uma loja e um **[!UICONTROL Store View]** adicionais. Verifique se o **[!UICONTROL Store View]** é *[!UICONTROL Enabled]*.
1. Configure **[!DNL Configure Google Analytics]** em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Para **[!DNL Main]** e sites adicionais [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* para outros campos, mas não os altere.
   * Para **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Desabilite **[!DNL Configure Google Analytics]** em **[!DNL Default Config]** [!DNL scope] alterando **[!UICONTROL Enable]** de *[!UICONTROL Yes]* para *[!UICONTROL No]*. Certifique-se de não alterar mais nada!
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crie e Edite qualquer **[!UICONTROL category]** e adicione uma atualização agendada para ele:
   * Qualquer nome, data inicial futura, data final futura e qualquer alteração em **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Salve a atualização e verifique se há erros em [!DNL browser developer console].

<u>Resultados esperados</u>:

Nenhum erro [!DNL JS] e as alterações na atualização [!DNL staging] foram salvas com êxito.

<u>Resultados reais</u>:

[!DNL JS] erros estão visíveis no console, o formulário está malformado e o [!DNL spinner] nunca é desabilitado após salvar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
