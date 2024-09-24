---
title: "ACSD-51379: as alterações no conteúdo de texto da página via  [!DNL Page Builder] não são salvas"
description: Aplique a correção ACSD-51379 para corrigir o problema do Adobe Commerce em que as alterações feitas no conteúdo de texto de uma página via  [!DNL Page Builder]  não são salvas.
feature: Page Builder, Page Content
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: as alterações no conteúdo de texto da página via [!DNL Page Builder] não são salvas

O patch ACSD-51379 corrige o problema em que as alterações feitas no conteúdo de texto de uma página via [!DNL Page Builder] não são salvas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 está instalado. A ID do patch é ACSD-51379. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações feitas no conteúdo de texto de uma página via [!DNL Page Builder] não são salvas.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Admin.
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Crie uma página de teste com uma linha e um elemento de texto na guia **[!UICONTROL Content]**.
1. Salve a página e retorne à guia **[!UICONTROL Content]**.
1. Edite o texto selecionando-o e alterando-o.

   **Observação:** o problema só poderá ser reproduzido se o texto for selecionado e alterado sem a ativação do editor.

1. Clique no botão **[!UICONTROL Save and Close]** na página de teste.
1. Abra a página de teste novamente e verifique a guia **[!UICONTROL Content]**.

<u>Resultados esperados</u>:

O novo texto é salvo com sucesso para elementos de texto originais e duplicados.

<u>Resultados reais</u>:

O elemento de texto foi duplicado com sucesso, mas o novo texto não foi salvo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
