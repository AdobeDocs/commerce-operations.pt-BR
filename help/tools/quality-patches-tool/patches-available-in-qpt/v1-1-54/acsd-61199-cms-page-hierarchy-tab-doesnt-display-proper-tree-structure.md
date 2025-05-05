---
title: "ACSD-61199: a guia da página [!UICONTROL Hierarchy] do CMS não exibe a estrutura de árvore adequada"
description: Aplique o patch ACSD-61199 para corrigir o problema do Adobe Commerce em que a guia *[!UICONTROL Hierarchy]* da página do CMS não exibe uma estrutura de árvore adequada ao editar uma página do CMS com um *[!UICONTROL Hierarchy]* existente.
feature: Page Content
role: Admin, Developer
source-git-commit: bbe4e272d3a8bd82163bdd718d006a314287b650
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# ACSD-61199: a guia [!UICONTROL Hierarchy] da página do CMS não exibe a estrutura de árvore apropriada

O patch ACSD-61199 corrige o problema em que a guia *[!UICONTROL Hierarchy]* da página do CMS não exibe uma estrutura de árvore adequada ao editar uma página do CMS com um *[!UICONTROL Hierarchy]* existente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61199. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A guia *[!UICONTROL Hierarchy]* da página do CMS não exibe uma estrutura de árvore adequada ao editar uma página do CMS com um *[!UICONTROL Hierarchy]* existente.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Criar um novo **[!UICONTROL CMS page]**. Ele é adicionado à raiz do site no *[!UICONTROL Hierarchy]*.
1. Salve a página.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Adicione quaisquer outras páginas existentes ao *[!UICONTROL Hierarchy]*.
1. Salve o *[!UICONTROL Hierarchy]*.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Edite qualquer uma das páginas existentes e abra o *[!UICONTROL Hierarchy]*.

<u>Resultados esperados</u>:

O *[!UICONTROL Hierarchy]* é carregado conforme esperado.

<u>Resultados reais</u>:

O *[!UICONTROL Hierarchy]* não está carregado na guia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
