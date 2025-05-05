---
title: 'ACSD-62689: Não é possível adicionar categorias em [!UICONTROL Related Product Rules] e widgets após profundidade 4'
description: Aplique o patch ACSD-62689 para corrigir o problema do Adobe Commerce em que um cliente não pode adicionar categorias em [!UICONTROL Related Product Rules] e widgets após o aninhamento na profundidade quatro.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
source-git-commit: 7aefd4f20580529a9da14776368bf2c3bbb3ff3c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: Não é possível adicionar categorias em *[!UICONTROL Related Product Rules]* e widgets após profundidade 4

>[!NOTE]
>
>Este patch foi substituído por [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md).

O patch ACSD-62689 corrige o problema em que um cliente não consegue adicionar categorias em *[!UICONTROL Related Product Rules]* e widgets após o aninhamento de profundidade quatro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62689. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um cliente não pode adicionar categorias em *[!UICONTROL Related Product Rules]* e widgets após o aninhamento de profundidade quatro.

<u>Etapas a serem reproduzidas</u>:

1. Crie duas categorias chamadas *[!UICONTROL Anchor]* e *[!UICONTROL Non-Anchor]* na categoria raiz padrão.
   * Verifique se o sinalizador *[!UICONTROL Is Anchor]* está desabilitado para a categoria *[!UICONTROL Non-Anchor]*.
1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Widgets]** e crie um widget.
1. Em *[!UICONTROL Layout Updates]*, selecione **[!UICONTROL Non-Anchor Categories]** no campo *[!UICONTROL Display on]*.
1. Clique em **[!UICONTROL Specific Categories]**.
1. Clique no ícone de seleção de categoria.
1. Expanda a categoria raiz.
1. Verifique as categorias. Ambos devem ser desativados e não podem ser selecionados.
1. Em *[!UICONTROL Layout Updates]*, selecione **[!UICONTROL Anchor Categories]** no campo *[!UICONTROL Display on]*. Depois, siga as etapas 5 e 6.
1. Verifique as categorias. Ambos devem ser ativados e selecionáveis.

<u>Resultados esperados</u>:

Na etapa 7, somente a categoria *[!UICONTROL Non-Anchor]* deve ser selecionável. Na etapa 9, a categoria *[!UICONTROL Anchor]* deve ser selecionável.

<u>Resultados reais</u>:

Na etapa 7, ambas as categorias não podem ser selecionadas. Na etapa 9, ambas as categorias podem ser selecionadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

