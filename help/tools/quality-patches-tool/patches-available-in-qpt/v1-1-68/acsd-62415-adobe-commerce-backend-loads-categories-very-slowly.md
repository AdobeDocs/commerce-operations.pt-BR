---
title: 'ACSD-62415: o back-end do Adobe Commerce carrega [!UICONTROL Categories] muito lentamente'
description: Aplique o patch ACSD-62415 para corrigir o problema do Adobe Commerce em que o desempenho da página [!UICONTROL Categories] no painel [!UICONTROL Admin] é carregado muito lentamente quando um grande número de categorias de âncora está presente.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: o back-end do Adobe Commerce carrega **[!UICONTROL Categories]** muito lentamente quando categorias de âncora estão presentes

O patch ACSD-62415 corrige o problema em que o desempenho da página **[!UICONTROL Categories]** no painel **[!UICONTROL Admin]** é carregado muito lentamente quando um grande número de categorias de âncora está presente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-62415. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página **[!UICONTROL Categories]** no painel **[!UICONTROL Admin]** é carregada muito lentamente quando há um grande número de categorias de âncora presentes.

<u>Etapas a serem reproduzidas</u>:

1. Gerar categorias de âncora 3K.
1. Abra a página **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** no painel **[!UICONTROL Admin]**.

<u>Resultados esperados</u>:

A página **[!UICONTROL Categories]** é carregada rapidamente e a consulta não deve ser repetida 1.000 vezes.

<u>Resultados reais</u>:

O carregamento leva de 7 a 20 segundos e a consulta é executada mais de 1.000 vezes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
