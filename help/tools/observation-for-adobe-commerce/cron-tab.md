---
title: A guia  [!DNL Cron]
description: Saiba mais sobre a  [!DNL Cron] guia de  [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# A guia [!DNL Cron]

Esta guia é uma tentativa de isolar rapidamente os problemas e as causas de [!DNL cron] problemas.

## [!UICONTROL Cron transaction duration in seconds]

![Duração da transação do Cron em segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

O quadro **[!UICONTROL Cron transaction duration in seconds]** exibe a duração da transação [!DNL crons] em segundos. Isso exibirá transações com longos tempos de execução. Um aprofundamento no APM mostrará mais detalhes sobre qual consulta a transação/operação pode estar sendo executada.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads por Nó](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

O quadro **[!UICONTROL MySQL Non-Sleeping Threads by Node]** mostra as threads Não Suspensas do MySQL por nó ao longo do período selecionado.

## [!UICONTROL SQL Trace count by path]

![Contagem de Rastreamento SQL por caminho](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

O quadro **[!UICONTROL SQL Trace count by path]** analisa as contagens de rastreamento do MySQL por caminho, o que pode ajudar a rastrear instruções SQL em um período selecionado.

## [!UICONTROL Cron database call]

![Chamada de banco de dados do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

O quadro **[!UICONTROL Cron database call]** analisa o número de chamadas [!DNL crons] para o banco de dados ao longo de um período selecionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueios de tabela de agendamento do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

O quadro **[!UICONTROL Cron schedule table locks]** analisa os bloqueios da tabela de agendamento [!DNL cron] em um período selecionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueios de tabela de agendamento do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

O quadro **[!UICONTROL Cron schedule clean cron fired]** verifica o número de [!DNL crons] limpos em um período selecionado. Se nenhum dado for exibido neste quadro, isso pode indicar um problema com a execução correta de [!DNL crons]. Se a agenda de trabalho [!DNL cron] não for limpa, [!DNL crons] não será executado de forma ideal e poderá demorar mais para ser executado.

## [!UICONTROL Cron schedule clean records details table]

![Tabela de detalhes de limpeza de registros do Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

A tabela **[!UICONTROL Cron schedule clean records details table]** fornece detalhes sobre o trabalho para limpar registros da tabela `cron_schedule` em um período selecionado.

## [!UICONTROL cron_schedule table updates]

![atualizações da tabela cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

O quadro **[!UICONTROL cron_schedule table updates]** verifica o número de [!DNL cron] atualizações de tabela agendadas em um período selecionado. A alta atividade de exclusão ou atualização desta tabela pode indicar um problema com [!DNL crons]. Além disso, o [!DNL crons] atualiza essa tabela quando ele é executado e concluído. Portanto, se não houver nenhuma atividade nessa tabela e houver [!DNL crons] configurado, poderá haver um problema com [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabelas de Operações de Armazenamento de Dados](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

O **[!UICONTROL Datastore Operations Tables]** analisa as operações de tabela de banco de dados, incluindo `SELECT`, `DELETE` e `UPDATE` em um período selecionado. Este quadro mostra as tabelas do banco de dados com a maior frequência de operação em relação a elas.
