---
title: '"Integre o [!DNL Site-Wide Analysis Tool]"'
description: Siga estas etapas para recuperar o [!DNL Upgrade Compatibility Tool] relatório do [!DNL Site-Wide Analysis Tool] painel em seu projeto do Adobe Commerce.
source-git-commit: 1fc12289125a5954243e177a0c21505234eb2e81
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Integre o [!DNL Site-Wide Analysis Tool]

O [!DNL Site-Wide Analysis Tool] O oferece monitoramento, relatórios e recomendações em tempo real, 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade das instâncias do Adobe Commerce.

O [!DNL Upgrade Compatibility Tool] agora está integrado ao [!DNL Site-Wide Analysis Tool] , a fim de proporcionar às pessoas não técnicas a capacidade de gerirem a [!DNL Upgrade Compatibility Tool] e obtenha um [relatório](../upgrade-compatibility-tool/reports.md) contendo uma lista de problemas para cada arquivo.

Consulte a [[!DNL Site-Wide Analysis Tool] guia do usuário](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) para obter mais informações.

## Execute o [!DNL Upgrade Compatibility Tool] do [!DNL Site-Wide Analysis Tool]

Navegue até o [!DNL Site-Wide Analysis Tool] painel para o seu projeto e localize a variável [!DNL Upgrade Compatibility Tool] widget.

![Dispositivo SWAT UCT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Clique em **[!UICONTROL Run Upgrade Scan]**. A verificação pode levar algum tempo, dependendo do tamanho do projeto. Um ponteiro indica que a verificação está em andamento.

![Dispositivo SWAT UCT - Em progresso](../../assets/upgrade-guide/uct-swat-progress.png)

Após a conclusão da verificação, os resultados de alto nível são exibidos no widget.

![Dispositivo SWAT UCT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Clique em **[!UICONTROL Download Report]** para recuperar o [!DNL Upgrade Compatibility Tool] [relatório HTML](../upgrade-compatibility-tool/reports.md#html-report) e revise os detalhes.


>[!NOTE]
>
> Executar o [!DNL Upgrade Compatibility Tool] através da [!DNL Site-Wide Analysis Tool] O otimiza seus resultados e ajuda você a se concentrar em problemas novos e críticos para sua atualização de destino. Ele usa a variável [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e sempre mostra resultados comparando a versão do seu projeto com a versão mais recente lançada.
