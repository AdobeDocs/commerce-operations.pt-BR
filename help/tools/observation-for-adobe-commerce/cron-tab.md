---
title: '"O [!UICONTROL Cron] tab"'
description: Saiba mais sobre o [!UICONTROL Cron] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# O [!UICONTROL Cron] guia

Esta guia é uma tentativa de isolar rapidamente os problemas e as causas de problemas de cron.

## [!UICONTROL Cron transaction duration in seconds]

![Duração da transação Cron em segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

O **[!UICONTROL Cron transaction duration in seconds]** quadro exibe crons transaction duration em segundos. Isso exibirá as transações que têm tempos de execução longos. Um mergulho mais profundo no APM mostrará mais detalhes sobre qual query a transação/operação pode estar sendo executada.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![Threads que não dormem MySql por nó](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

O **[!UICONTROL MySql Non-Sleeping Threads by Node]** mostra os threads MySql Non-Sleeping por nó no período de tempo selecionado.

## [!UICONTROL SQL Trace count by path]

![Contagem de Rastreio SQL por caminho](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

O **[!UICONTROL SQL Trace count by path]** O frame procura as contagens de rastreamento do MySql por caminho, o que pode ajudar a rastrear instruções SQL em um período selecionado.

## [!UICONTROL Cron database call]

![Chamada de banco de dados Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

O **[!UICONTROL Cron database call]** O frame procura o número de crons que chamam o banco de dados em um período selecionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueios da tabela de programação de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

O **[!UICONTROL Cron schedule table locks]** O quadro observa os bloqueios da tabela de programação de cron em um período selecionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueios da tabela de programação de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

O **[!UICONTROL Cron schedule clean cron fired]** O frame procura o número de crons limpos em um período selecionado. Se nenhum dado for exibido nesse quadro, isso pode indicar um problema com os crons sendo executados corretamente. Se o cronograma de tarefas do cron não for limpo, os crons não serão executados de maneira ideal e poderão demorar mais para serem executados.

## [!UICONTROL Cron schedule clean records details table]

![Tabela de detalhes de registros de limpeza de programação de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

O **[!UICONTROL Cron schedule clean records details table]** a tabela fornece detalhes sobre a tarefa para limpar registros da `cron_schedule` em um período selecionado.

## [!UICONTROL cron_schedule table updates]

![atualizações da tabela cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

O **[!UICONTROL cron_schedule table updates]** O frame procura o número de atualizações de tabela programadas do cron em um período selecionado. A alta atividade na exclusão ou atualização desta tabela pode indicar um problema com crons. Além disso, os crons atualizam essa tabela quando são executados e concluídos, de modo que, se não houver atividade nessa tabela e houver crons configurados, poderá haver um problema com os crons.

## [!UICONTROL Datastore Operations Tables]

![Tabelas de operações do armazenamento de dados](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

O **[!UICONTROL Datastore Operations Tables]** observa as operações da tabela do banco de dados, incluindo `SELECT`, `DELETE`e `UPDATE` em um período selecionado. Este quadro mostra as tabelas do banco de dados com a maior frequência de operação em relação a elas.
