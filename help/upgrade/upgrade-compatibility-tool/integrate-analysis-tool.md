---
title: Integrar o  [!DNL Site-Wide Analysis Tool]
description: Siga estas etapas para recuperar o relatório [!DNL Upgrade Compatibility Tool] do painel [!DNL Site-Wide Analysis Tool] do seu projeto do Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Integrar o [!DNL Site-Wide Analysis Tool]

O [!DNL Site-Wide Analysis Tool] fornece monitoramento, relatórios e recomendações de desempenho em tempo real 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade das instâncias do Adobe Commerce.

O [!DNL Upgrade Compatibility Tool] agora está integrado ao [!DNL Site-Wide Analysis Tool] para fornecer a capacidade para que pessoas não técnicas executem o [!DNL Upgrade Compatibility Tool] e obtenham um [relatório](../upgrade-compatibility-tool/reports.md) contendo uma lista de problemas para cada arquivo.

Consulte o [[!DNL Site-Wide Analysis Tool] guia do usuário](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/site-wide-analysis-tool/access) para obter mais informações.

## Executar o [!DNL Upgrade Compatibility Tool] a partir do [!DNL Site-Wide Analysis Tool]

Navegue até o painel [!DNL Site-Wide Analysis Tool] do seu projeto e localize o widget [!DNL Upgrade Compatibility Tool].

![Widget da SWAT do UCT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Clique em **[!UICONTROL Run Upgrade Scan]**. A verificação pode levar algum tempo, dependendo do tamanho do projeto. Um ponteiro indica que a verificação está em andamento.

![Widget da SWAT do UCT - Em andamento](../../assets/upgrade-guide/uct-swat-progress.png)

Após a conclusão da verificação, os resultados de alto nível são exibidos no widget.

![Widget do UCT SWAT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Clique em **[!UICONTROL Download Report]** para recuperar o [!DNL Upgrade Compatibility Tool] [relatório de HTML](../upgrade-compatibility-tool/reports.md#html-report) e examinar os detalhes.


>[!NOTE]
>
> Executar o [!DNL Upgrade Compatibility Tool] por meio do [!DNL Site-Wide Analysis Tool] otimiza os resultados e ajuda você a se concentrar em problemas novos e críticos para a atualização de destino. Ela usa a opção [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e sempre mostra resultados comparando a versão do seu projeto com a versão mais recente lançada.
