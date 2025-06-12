---
title: 'ACSD-51379: as alterações no conteúdo de texto da página via  [!DNL Page Builder]  não são salvas'
description: Aplique a correção ACSD-51379 para corrigir o problema do Adobe Commerce em que as alterações feitas no conteúdo de texto de uma página via  [!DNL Page Builder]  não são salvas.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: as alterações no conteúdo de texto da página via [!DNL Page Builder] não são salvas

O patch ACSD-51379 corrige o problema em que as alterações feitas no conteúdo de texto de uma página via [!DNL Page Builder] não são salvas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 está instalado. A ID do patch é ACSD-51379. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

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

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
