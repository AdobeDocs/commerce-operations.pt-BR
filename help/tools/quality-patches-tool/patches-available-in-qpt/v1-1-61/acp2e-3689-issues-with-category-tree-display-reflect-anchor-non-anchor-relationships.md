---
title: 'ACP2E-3689: Vários problemas com a árvore de categoria são exibidos em níveis mais profundos e refletem relações de âncora/não âncora'
description: Aplique o patch ACP2E-3689 para corrigir o problema do Adobe Commerce com a exibição da árvore de categoria em mais de profundidade quatro aninhamento e refletindo relações de âncora/não âncora.
feature: Categories, Page Content
role: Admin, Developer
source-git-commit: af8b7b44274b828b3f60f92fd78f9f3d3983abb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# ACP2E-3689: Vários problemas com a árvore de categoria são exibidos em níveis mais profundos e refletem relações de âncora/não âncora

>[!NOTE]
>
>Este patch substitui o [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) para as versões 2.4.7 e posteriores.

O patch ACP2E-3689 corrige vários problemas com a exibição da árvore de categoria em mais de profundidade quatro aninhamento e refletindo relações de âncora/não âncora. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACP2E-3689. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A árvore de categorias em níveis mais profundos (4+) não é exibida corretamente e está refletindo relações de âncora/não âncora.

<u>Etapas a serem reproduzidas</u>:

1. Configurar uma árvore de categorias com categorias aninhadas de mais de quatro níveis.
1. Expanda a árvore de categorias no Administrador que aparece em locais diferentes:
   1. Configure um [!UICONTROL Related Products Rule] e defina uma condição com base em categorias.
   1. Crie um widget e em [!UICONTROL Layout Updates] selecione [!UICONTROL Anchor categories].

<u>Resultados esperados</u>:

Todos os níveis da árvore de categorias são exibidos corretamente.

<u>Resultados reais</u>:

Somente os primeiros níveis (&lt;4) da árvore de categorias estão disponíveis.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
