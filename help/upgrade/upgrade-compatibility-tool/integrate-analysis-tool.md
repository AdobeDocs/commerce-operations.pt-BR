---
title: Integrar o [!DNL Site-Wide Analysis Tool]
description: Siga estas etapas para recuperar o relatório do [!DNL Upgrade Compatibility Tool] no painel [!DNL Site-Wide Analysis Tool] do seu projeto do Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Integrar o [!DNL Site-Wide Analysis Tool]

O [!DNL Site-Wide Analysis Tool] fornece monitoramento, relatórios e recomendações de desempenho em tempo real 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade das instâncias do Adobe Commerce.

O [!DNL Upgrade Compatibility Tool] agora está integrado ao [!DNL Site-Wide Analysis Tool] para fornecer a capacidade para que pessoas não técnicas executem o [!DNL Upgrade Compatibility Tool] e obtenham um [relatório](../upgrade-compatibility-tool/reports.md) contendo uma lista de problemas para cada arquivo.

Consulte o [[!DNL Site-Wide Analysis Tool] guia do usuário](/help/tools/site-wide-analysis-tool/access.md) para obter mais informações.

## Executar o [!DNL Upgrade Compatibility Tool] a partir do [!DNL Site-Wide Analysis Tool]

Navegue até o painel [!DNL Site-Wide Analysis Tool] do seu projeto e localize o widget [!DNL Upgrade Compatibility Tool].

![Widget da SWAT do UCT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Clique em **[!UICONTROL Run Upgrade Scan]**. A verificação pode levar algum tempo, dependendo do tamanho do projeto. Um ponteiro indica que a verificação está em andamento.

![Widget da SWAT do UCT - Em andamento](../../assets/upgrade-guide/uct-swat-progress.png)

Após a conclusão da verificação, os resultados de alto nível são exibidos no widget.

![Widget do UCT SWAT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Clique em **[!UICONTROL Download Report]** para recuperar o [!DNL Upgrade Compatibility Tool] [relatório do HTML](../upgrade-compatibility-tool/reports.md#html-report) e examinar os detalhes.


>[!NOTE]
>
> Executar o [!DNL Upgrade Compatibility Tool] por meio do [!DNL Site-Wide Analysis Tool] otimiza os resultados e ajuda você a se concentrar em problemas novos e críticos para a atualização de destino. Ela usa a opção [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e sempre mostra resultados comparando a versão do seu projeto com a versão mais recente lançada.
