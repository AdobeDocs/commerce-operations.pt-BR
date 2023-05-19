---
title: Integre o [!DNL Site-Wide Analysis Tool]
description: Siga estas etapas para recuperar a variável [!DNL Upgrade Compatibility Tool] relatório do [!DNL Site-Wide Analysis Tool] no seu projeto do Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Integre o [!DNL Site-Wide Analysis Tool]

A variável [!DNL Site-Wide Analysis Tool] O fornece monitoramento, relatórios e recomendações de desempenho em tempo real 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade das instâncias do Adobe Commerce.

A variável [!DNL Upgrade Compatibility Tool] O agora está integrado ao [!DNL Site-Wide Analysis Tool] a fim de proporcionar às pessoas não técnicas a capacidade de gerir a [!DNL Upgrade Compatibility Tool] e obtenha uma [relatório](../upgrade-compatibility-tool/reports.md) contendo uma lista de problemas para cada arquivo.

Consulte a [[!DNL Site-Wide Analysis Tool] guia do usuário](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) para obter mais informações.

## Execute o [!DNL Upgrade Compatibility Tool] do [!DNL Site-Wide Analysis Tool]

Navegue até a [!DNL Site-Wide Analysis Tool] para o seu projeto e localize o [!DNL Upgrade Compatibility Tool] widget.

![Widget do UCT SWAT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Clique em **[!UICONTROL Run Upgrade Scan]**. A verificação pode levar algum tempo, dependendo do tamanho do projeto. Um ponteiro indica que a verificação está em andamento.

![Widget do UCT SWAT - Em andamento](../../assets/upgrade-guide/uct-swat-progress.png)

Após a conclusão da verificação, os resultados de alto nível são exibidos no widget.

![Widget do UCT SWAT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Clique em **[!UICONTROL Download Report]** para recuperar o [!DNL Upgrade Compatibility Tool] [relatório HTML](../upgrade-compatibility-tool/reports.md#html-report) e analise os detalhes.


>[!NOTE]
>
> Execução da [!DNL Upgrade Compatibility Tool] por meio da [!DNL Site-Wide Analysis Tool] O otimiza seus resultados e ajuda você a se concentrar em problemas novos e críticos para a atualização do target. Ele usa o [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e sempre mostra resultados comparando a versão do seu projeto com a versão mais recente lançada.
