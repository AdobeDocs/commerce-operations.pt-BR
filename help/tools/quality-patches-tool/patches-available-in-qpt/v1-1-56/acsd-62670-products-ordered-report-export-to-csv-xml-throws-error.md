---
title: 'ACSD-62670: a exportação [!UICONTROL Ordered Products Report] para CSV e XML retorna o erro 404'
description: Aplique o patch ACSD-62670 para corrigir o problema do Adobe Commerce em que a exportação do [!UICONTROL Ordered Products Report] para CSV e XML gera um erro.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]* exportação para CSV e XML gera erro

O patch ACSD-62670 corrige o problema em que a exportação de *[!UICONTROL Ordered Products Report]* para CSV e XML gera um erro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.56 está instalado. A ID do patch é ACSD-62670. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de *[!UICONTROL Ordered Products Report]* para CSV e XML gera um erro.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o painel *Admin* e navegue até **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Tente exportar arquivos CSV ou do Excel.

<u>Resultados esperados</u>:

Os relatórios são exportados sem erros.

<u>Resultados reais</u>:

A exportação do *[!UICONTROL Ordered Products Report]* resulta no erro 404.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
