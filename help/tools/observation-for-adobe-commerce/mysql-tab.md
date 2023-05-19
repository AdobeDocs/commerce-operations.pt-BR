---
title: A variável [!UICONTROL MySQL] guia
description: Saiba mais sobre o [!UICONTROL MySQL] guia de [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 0%

---

# A variável [!UICONTROL MySQL] guia

## [!UICONTROL MySQL% free storage by node]

![Armazenamento gratuito MySQL% por nó](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

Muitos problemas são causados pela falta de armazenamento do MySQL no armazenamento atribuído ao MySQL (`datadir` Configuração do MySQL, o padrão é `/data/mysql`) ou o `tmpdir` ficando sem espaço. O padrão `tmpdir` (configuração MySQL) é `/tmp`. A variável **[!UICONTROL MySQL% free storage by node]** o quadro observa o `/, /tmp` (se definido como uma montagem separada) e a variável `/data/mysql` porcentagem de armazenamento livre. A partir do MySQL versão 5.7 (MariaDB versão 10.2), descompactado `tmp` as tabelas são gravadas em um `tmp` tablespace no `/data/mysql` no arquivo (ibtmp1). Por padrão, esse arquivo é expandido automaticamente sem limite. Como é um tablespace, ele não diminuirá de tamanho e será redefinido para 12 MB quando o MySQL for reiniciado.

## [!UICONTROL MySQL Connections by Node]

![Conexões MySQL por nó](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

A variável **[!UICONTROL MySQL Connections by Node]** indica períodos de paralisações do nó do banco de dados ou grandes volumes de conexões.

## [!UICONTROL MySQL Node Summary]

![Resumo de nós do MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

A variável **[!UICONTROL MySQL Node Summary]** A tabela mostra detalhes do nó do banco de dados, como versão do software e tipo de instância (tamanho).

## [!UICONTROL Galera Number of Nodes in cluster]

![Número de nós do cluster](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

A variável **[!UICONTROL Galera Number of Nodes in cluster]** exibe informações dos logs do MySQL. À medida que os nós ingressam e saem de um cluster, somente as mensagens do período selecionado são exibidas. Se um nó sair do cluster antes do período, nenhuma mensagem existirá durante esse período. Se você suspeitar que o banco de dados pode estar em execução a menos de um nó, expanda o período para um período maior para ver se você pode ver informações adicionais. Se houver informações durante o período de tempo que indiquem menos do que todos os nós na variável [!DNL Galera] cluster, expanda o período para ver se você pode determinar quando o nó deixou o cluster.

## [!UICONTROL MySQL shutdowns and starts]

![O MySQL é encerrado e iniciado](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

A variável **[!UICONTROL MySQL shutdowns and starts]** O quadro detecta quando há um desligamento de um nó. A variável [!DNL Galera] os nós serão removidos e serão removidos automaticamente do [!DNL Galera] nó. Isso normalmente resultará em uma reinicialização do serviço MySQL.

## [!UICONTROL Galera log]

![Registro de galera](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

A variável **[!UICONTROL Galera log]** mostra as contagens de sinais específicos dos logs do MySQL relativos a [!DNL Galera] nós, seus estados e as alterações de estado do [!DNL Galera] cluster.

* &#39;%1047 O WSREP ainda não preparou o nó para uso do aplicativo (%node_not_prep_for_use&#39;)
* &#39;%\[ERROR\] WSREP: Falha ao ler de: wsrep_sst_xtrabackup-v2%&#39;) como &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: Processo concluído com erro: wsrep_sst_xtrabackup-v2 %&#39;) como &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) como &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;) como &#39;susp_node&#39;
* &#39;%member = 3/3 (unido/total)%&#39;) como&#39;3of3&#39;
* &#39;%member = 2/3 (unido/total)%&#39;) como&#39;2of3&#39;
* &#39;%member = 2/2%&#39;) como &#39;2of2&#39;
* &#39;%member = 1/2%&#39;) como &#39;1of2&#39;
* &#39;%member = 1/3%&#39;) como &#39;1of3&#39;
* &#39;%member = 1/1%&#39;) como &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) como&#39;sql_restart&#39;
* &#39;%Quorum: Nenhum nó com estado concluído:%&#39;) como &#39;no_node_count&#39;
* &#39;%WSREP: Membro 0%&#39;) como &#39;mem_0&#39;
* &#39;%WSREP: Membro 1.0%&#39;) como &#39;mem_1&#39;
* &#39;%WSREP: Membro 2%&#39;) como&#39;mem2&#39;
* &#39;%WSREP: Sincronizado com grupo, pronto para conexões&#39;) como &#39;pronto&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) como &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Note\] WSREP: Nova exibição de cluster: estado global:%&#39;) como &#39;galera_cluster_view_change&#39;

## [!UICONTROL Galera Log by Host]

![Log de Galera por Host](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

A variável **[!UICONTROL Galera Log by Host]** o quadro é igual ao **[!UICONTROL Galera log]** exceto que é dividido por nó para ajudar na solução de problemas.

## [!UICONTROL Database performance]

![Desempenho do banco de dados](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

A variável **[!UICONTROL Database performance]** mostra o desempenho do banco de dados durante solicitações específicas. Você pode ver cada métrica clicando nelas nos ícones coloridos abaixo do gráfico. Muitas das métricas chamadas no [Monitorando o Desempenho do Banco de Dados MySQL com o New Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) são encontrados neste quadro.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Contagem de Chamadas do Banco de Dados de Transações](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

A variável **[!UICONTROL Transaction Database Call Count]** quadro mostra o número de chamadas de banco de dados feitas por cada faceta de transação. Isso parece ser focado em linhas e não em instruções.

## [!UICONTROL Cron_schedule table updates]

![Atualizações de tabela Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

A variável **[!UICONTROL Cron_schedule table updates]** quadro exibe a duração máxima das atualizações do banco de dados na tabela cron_schedule para o período selecionado.

## [!UICONTROL Slow Query Traces]

![Rastreamentos de Consulta Lentos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

A variável **[!UICONTROL Slow Query Traces]** quadro exibe a tabela e o tipo de solicitação em que existem rastreamentos de consulta lenta. Um rastreamento de consulta lento é criado para transações de consulta que levam mais de cinco segundos. Importantes para este quadro são as consultas de atualização. Se uma tabela estiver sendo atualizada por `UPDATE`, `DELETE`, e `INSERT` podem bloquear tabelas por um período.

Par `SELECT` As instruções podem bloquear linhas se usadas com FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tabelas de operações de armazenamento de dados](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Alteração na tabela do Cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

A variável **[!UICONTROL Cron table change]** frame procura por mensagens de erro &quot;não foi possível adquirir bloqueio para o trabalho cron:&quot;, juntamente com um erro de memória PHP específico e bloqueios envolvendo o `cron_schedule` tabela. Se a variável `cron_schedule` A tabela está bloqueada (por exemplo, por um `DELETE` sendo executada em relação a ela), bloqueará a execução de outros crons.

## [!UICONTROL Deadlocks]

![Deadlocks](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

A variável **[!UICONTROL Deadlocks]** O quadro analisa as seguintes strings analisadas a partir dos logs do MySQL:

* &#39;%PHP erro fatal: tamanho de memória permitido de &#39;%&#39;) como php_mem_error
* &#39;%get lock; tente reiniciar a transação; a consulta era: DELETE FROM \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock para o trabalho cron: indexer_reindex_all_invalid%&#39;) como &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% lock para o trabalho cron: cron_schedule%&#39;) como &#39;lock_cron_schedule&#39;
* &#39;% lock para trabalho cron:%&#39;) como &#39;total_cron_lock&#39;
* &#39;%General error: 1205 Lock wait timeout aded%&#39;) as &#39;sql_1205_lock&#39;
* &#39;%ERROR 1213 (40001): Deadlock encontrado ao tentar obter lock%&#39;) como &#39;sql_1213_lock&#39;
* &#39;%SQLSTATE[40001]: falha de serialização: 1213 Deadlock encontrado (%) como &#39;sql_1213_lock2&#39;
* &#39;% lock para o trabalho cron: indexer_update_all_views%&#39;) como &#39;lock_indexer_update_all_views&#39;
* &#39;% lock para o trabalho cron: sales_grid_order_Invoice_async_insert%&#39;) como &#39;lock_sales_grid_order_Invoice_async_insert&#39;,
* &#39;% lock para o trabalho cron: staging_remove_updates%&#39;) as &#39;lock_staging_remove_updates&#39;
* &#39;% lock para o trabalho cron: sales_grid_order_ship_async_insert%&#39;) como &#39;lock_sales_grid_order_ship_async_insert&#39;
* &#39;% lock para o trabalho cron: amazon_payments_process_queued_returns%&#39;) como &#39;lock_amazon_payments_process_queued_returns&#39;
* &#39;% lock para a tarefa cron: sales_send_order_ship_emails%&#39;) como &#39;lock_sales_send_order_shipemails&#39;
* &#39;% lock para o trabalho cron: staging_synchronize_entities_period%&#39;) como &#39;lock_staging_synchronize_entities_period&#39;
* &#39;% lock para o trabalho cron: indexer_clean_all_changelogs%&#39;) as &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% lock para o trabalho cron: magento_targetTrule_index_reindex%&#39;) como &#39;lock_magento_targetTrule_index_reindex&#39;
* &#39;% lock para a tarefa cron: newsletter_send_all%&#39;) como &#39;lock_newsletter_send_all&#39;
* &#39;% lock para a tarefa cron: newsletter_send_all%&#39;) como &#39;lock_newsletter_send_all&#39;
* &#39;% lock para o trabalho cron: sales_send_order_emails%&#39;) como &#39;lock_sales_send_order_emails&#39;
* &#39;% lock para a tarefa cron: sales_send_order_creditmemo_emails%&#39;) como &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock para o trabalho cron: sales_grid_order_creditmemo_async_insert%&#39;) como &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% lock para o trabalho cron: bulk_cleanup%&#39;) como &#39;lock_bulk_cleanup&#39;
* &#39;% lock para o trabalho cron: flush_preview_quotas%&#39;) como &#39;lock_flush_preview_quotas&#39;
* &#39;% lock para a tarefa cron: sales_send_order_Invoice_emails%&#39;) como &#39;lock_sales_send_order_Invoice_emails&#39;
* &#39;% lock para a tarefa cron: sales_send_order_Invoice_emails%&#39;) como &#39;lock_sales_send_order_Invoice_emails&#39;
* &#39;% lock para o trabalho cron: captcha_delete_expired_images%&#39;) como &#39;lock_captcha_delete_expired_images&#39;
* &#39;% lock para o trabalho cron: magento_newrelicreporting_cron%&#39;) como &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% lock para o trabalho cron: outdated_authentication_failures_cleanup%&#39;) como &#39;lock_outdated_authentication_failures_cleanup&#39;
* &#39;% lock para o trabalho cron: send_notification%&#39;) como &#39;lock_send_notification&#39;
* &#39;% lock para o trabalho cron: magento_giftcardaccount_generage_codes_pool%&#39;) como &#39;lock_magento_giftcardaccount_generage_codes_pool&#39;
* &#39;% lock para o trabalho cron: catalog_product_frontend_actions_flush%&#39;) como &#39;lock_catalog_product_frontend_actions_flush&#39;
* &#39;% lock para o trabalho cron: mysqlmq_clean_messages%&#39;) como &#39;mysqlmq_clean_messages&#39;
* &#39;% lock para o trabalho cron: catalog_product_attribute_value_synchronize%&#39;) como &#39;lock_catalog_product_attribute_value_synchronize&#39;
* &#39;% lock para o trabalho cron: ddg_automation_importer%&#39;) como &#39;lock_ddg_automation_import&#39;
* &#39;% lock para o trabalho cron: ddg_automation_review_and_wishlist%&#39;) como &#39;lock_ddg_automation_review_and_wishlist&#39;
* &#39;% lock para o trabalho cron: captcha_delete_old_tries%&#39;) como &#39;lock_captcha_delete_old_tries&#39;
* &#39;% bloqueio para o trabalho cron: catalog_product_outdated_price_values_cleanup%&#39;) como &#39;lock_catalog_product_outdated_price_values_cleanup&#39;
* &#39;% lock para a tarefa cron: consumer_runner%&#39;) como &#39;lock_consumer_runner&#39;
* &#39;% lock para o trabalho cron: ddg_automation_customer_subscriber_guest_sync%&#39;) como &#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* &#39;% lock para o trabalho cron: get_amazon_capture_updates%&#39;) como &#39;lock_get_amazon_capture_updates&#39;
* &#39;% lock para o trabalho cron: get_amazon_authorization_updates%&#39;) como &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% lock para o trabalho cron: temando_process_platform_events%&#39;) como &#39;lock_temando_process_platform_events&#39;
* &#39;% lock para o trabalho cron: ddg_automation_status%&#39;) como &#39;lock_ddg_automation_status&#39;
* &#39;% lock para o trabalho cron: ddg_automation_status%&#39;) como &#39;lock_ddg_automation_status&#39;
* &#39;% bloqueio para o trabalho cron: sales_clean_orders%&#39;) como &#39;lock_sales_clean_orders&#39;
* &#39;% lock para o trabalho cron: catalog_index_refresh_price%&#39;) como &#39;lock_catalog_index_refresh_price&#39;
* &#39;% lock para o trabalho cron: magento_recompensa_balance_warning_notification%&#39;) como &#39;lock_magento_recompensa_balance_warning_notification&#39;
* &#39;% lock para o trabalho cron: analytics_update%&#39;) como &#39;lock_analytics_update&#39;
* &#39;% lock para o trabalho cron: messagequeue_clean_outdated_locks%&#39;) como &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock para o trabalho cron: messagequeue_clean_outdated_locks%&#39;) como &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock para o trabalho cron: staging_apply_version%&#39;) como &#39;lock_staging_apply_version&#39;
* &#39;% lock para a tarefa cron: magento_reforço_expire_points%&#39;) como &#39;lock_magento_recompensa_expire_points&#39;
* &#39;% lock para o trabalho cron: yotpo_yotpo_orders_sync%&#39;) como &#39;lock_yotpo_yotpo_orders_sync&#39;
* &#39;% lock para o trabalho cron: catalog_event_status_checker%&#39;) como &#39;lock_catalog_event_status_checker&#39;
* &#39;% lock para o trabalho cron: ddg_automation_campaign%&#39;) como &#39;lock_ddg_automation_campaign&#39;
* &#39;% lock para a tarefa cron: visitor_clean%&#39;) as &#39;lock_visitor_clean&#39;
* &#39;% lock para o trabalho cron: scconnector_verify_website%&#39;) como &#39;lock_scconnector_verify_website&#39;
* &#39;% lock para o trabalho cron: ddg_automation_email_templates%&#39;) como &#39;lock_ddg_automation_email_templates&#39;
* &#39;% lock para o trabalho cron: aggregate_sales_report_order_data%&#39;) como &#39;lock_aggregate_sales_report_order_data&#39;
* &#39;% lock para o trabalho cron: ddg_automation_catalog_sync%&#39;) como &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![Estatísticas do BD](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

A variável **[!UICONTROL DB Statistics]** o quadro exibe exclusões, gravações, linhas lidas, atualizações e consultas lentas por segundo.

## [!UICONTROL Request frequency]

![Frequência de solicitação](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![Erros de Banco de Dados](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

A variável **[!UICONTROL Database Errors]** quadro mostra uma variedade de bancos de dados [avisos e erros](https://mariadb.com/kb/en/mariadb-error-codes/):

* &#39;%Memory size alocado para a tabela temporária é mais de 20% de innodb_buffer_pool_size%&#39; como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) como &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco cheio%&#39;) como &#39;disk_full&#39;
* &#39;%Número do erro 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;reversão&#39;
* &#39;%Foreign key constraint falha para a tabela &#39;%&#39;) como &#39;Foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) como &#39;sql_1114_full&#39;&#39;%CRITICAL: SQLSTATE[HY000] [2006] O servidor MySQL desapareceu (%) como &quot;sql_went&quot;
* &#39;%SQLSTATE[HY000] [1040] Muitas conexões (%) como &#39;sql_1040&#39;
* &#39;%CRÍTICO: SQLSTATE[HY000] [2002]%&#39;) como &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) como &#39;sql_1047&#39;
* &#39;%[Aviso] Conexão cancelada (%) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: violação de restrição de integridade:%&#39;) como &#39;sql_23000&#39;
* &#39;%1205 Tempo limite de espera de bloqueio (%1) como &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Banco de dados desconhecido (%) como &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: tabela ou exibição base não encontrada:%&#39;) como &#39;sql_42S02&#39;
* &#39;%General error: 1114%&#39;) as &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Coluna não encontrada: 1054 Coluna desconhecida (%) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Erro de sintaxe ou violação de acesso:%&#39;) como&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: violação de cardinalidade:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE[2003]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Cliente com endereço IP (%) como &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Erro geral: 2014%&#39;) como &#39;sql_2014&#39;
* &#39;%1927 Conexão eliminada (%1927) como &#39;sql_1927&#39;
* &#39;%1062 \[ERRO\] InnoDB:%&#39;) as &#39;sql_1062_e&#39;
* &#39;%&#39;[Nota] WSREP: Liberando mapa de memória para disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Código de erro interno do MariaDB: 1146%&#39;) como &#39;sql_1146&#39;
* &#39;%Código de erro interno do MariaDB: 1062%&#39;) como &#39;sql_1062&#39; * &#39;%1062 [Aviso] InnoDB:%&#39;) como &#39;sql_1062_w&#39;
* &#39;%Código de erro interno do MariaDB: 1064%&#39;) como &#39;sql_1064&#39;
* &#39;%InDB: falha de asserção no arquivo &#39;%&#39;) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de processos em execução agora: 0%&#39;) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld obteve sinal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 Não é possível adicionar &#39;%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Erro geral: 3%&#39;) como &#39;cnt_wrt_tmp&#39;
* &#39;%General error: 1 %&#39;) como &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InDB: Erro (Chave duplicada)%&#39;) como &#39;innodb_dup_key&#39; DE SÉRIE TEMPORAL de Log

## [!UICONTROL DB Error Table]

![Tabela de Erros do BD](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

A variável **[!UICONTROL DB Error Table]** O quadro mostra as mesmas informações que o **[!UICONTROL Database Errors]** quadro, mas você pode vê-lo por nó e em um formato de tabela. Consulte [Códigos de erro do MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/) para obter mais informações.

## [!UICONTROL Database Traces]

![Rastreamentos de Banco de Dados](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

A variável **[!UICONTROL Database Traces]** O quadro mostra os rastreamentos do banco de dados por tipo na linha do tempo selecionada.

## [!UICONTROL Database processes]

![Processos de banco de dados](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

A variável **[!UICONTROL Database processes]** O quadro mostra os processos de banco de dados, ambientes e identificadores de nó.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads Não Suspensas do MySQL por Nó](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

A variável **[!UICONTROL MySQL Non-Sleeping Threads by Node]** mostra as threads de conexão com o banco de dados. Este quadro mostra as threads ativas.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL em execução e threads suspensos por ambiente](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

A variável **[!UICONTROL MySQL Running and Sleeping Threads by environment]** O quadro mostra conexões ativas e em repouso com o banco de dados. Se houver conexões com o banco de dados em que as consultas lentas entraram em suspensão, haverá conexões em suspensão. As conexões em suspensão podem ser consultas de banco de dados bloqueadas por linhas ou tabelas bloqueadas. Estas conexões em repouso também contêm conexões de trabalho do PHP.

## [!UICONTROL MySQL mem used by node]

![Mem MySQL usada pelo nó](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

A variável **[!UICONTROL MySQL mem used by node]** O quadro mostra o uso de memória do nó pelo MySQL. Em sites maiores, esse quadro pode ser barras contínuas com GBs de memória usados.

## [!UICONTROL Database mysql-slow.log]

![Banco de dados mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

A variável **[!UICONTROL Database mysql-slow.log]** quadro mostra os tipos de instrução de consulta que estavam no `mysql-slow.log` arquivo no período selecionado.
