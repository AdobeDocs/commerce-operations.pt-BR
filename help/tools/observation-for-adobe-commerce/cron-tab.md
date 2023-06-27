---
title: A variável [!DNL Cron] guia
description: Saiba mais sobre o [!DNL Cron] guia de [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# A variável [!DNL Cron] guia

Esta guia é uma tentativa de isolar rapidamente os problemas e as causas de [!DNL cron] problemas.

## [!UICONTROL Cron transaction duration in seconds]

![Duração da transação do Cron em segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

A variável **[!UICONTROL Cron transaction duration in seconds]** exibições de quadro [!DNL crons] duração da transação em segundos. Isso exibirá transações com longos tempos de execução. Um aprofundamento no APM mostrará mais detalhes sobre qual consulta a transação/operação pode estar sendo executada.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads Não Suspensas do MySQL por Nó](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

A variável **[!UICONTROL MySQL Non-Sleeping Threads by Node]** mostra as threads Não Suspensas do MySQL por nó ao longo do período selecionado.

## [!UICONTROL SQL Trace count by path]

![Contagem de Rastreamento SQL por caminho](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

A variável **[!UICONTROL SQL Trace count by path]** O quadro verifica as contagens de rastreamento do MySQL por caminho, o que pode ajudar a rastrear instruções SQL em um período selecionado.

## [!UICONTROL Cron database call]

![Chamada de banco de dados do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

A variável **[!UICONTROL Cron database call]** quadro observa o número de [!DNL crons] chamada ao banco de dados em um período selecionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueios de tabela de agendamento do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

A variável **[!UICONTROL Cron schedule table locks]** quadro procura em [!DNL cron] bloqueios de tabela de agendamento em um período selecionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueios de tabela de agendamento do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

A variável **[!UICONTROL Cron schedule clean cron fired]** quadro observa o número de [!DNL crons] limpo em um período selecionado. Se nenhum dado for exibido nesse quadro, isso pode indicar um problema com [!DNL crons] execução correta. Se a variável [!DNL cron] a programação do trabalho não é limpa, [!DNL crons] não serão executados de forma ideal e poderão levar mais tempo para serem executados.

## [!UICONTROL Cron schedule clean records details table]

![Tabela de detalhes de limpeza de registros do cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

A variável **[!UICONTROL Cron schedule clean records details table]** A tabela fornece detalhes sobre o trabalho do qual limpar registros `cron_schedule` tabela em um período selecionado.

## [!UICONTROL cron_schedule table updates]

![atualizações de tabela cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

A variável **[!UICONTROL cron_schedule table updates]** quadro observa o número de [!DNL cron] atualizações de tabela programadas em um período selecionado. A alta atividade de exclusão ou atualização dessa tabela pode indicar um problema com [!DNL crons]. Além disso, [!DNL crons] atualizar esta tabela quando eles forem executados e concluídos, caso não haja atividades nesta tabela e não houver [!DNL crons] configurado, pode haver um problema com [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabelas de operações de armazenamento de dados](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

A variável **[!UICONTROL Datastore Operations Tables]** verifica as operações de tabela de banco de dados, incluindo `SELECT`, `DELETE`, e `UPDATE` em um período selecionado. Este quadro mostra as tabelas do banco de dados com a maior frequência de operação em relação a elas.
