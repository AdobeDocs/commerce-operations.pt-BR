---
title: '"O [!UICONTROL PHP] tab"'
description: Saiba mais sobre o [!UICONTROL PHP] guia de [!DNS Observation for Adobe Commerce].
source-git-commit: f71fc3b2a66a4cc0b0d7865138184135e4a874e0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# O [!UICONTROL PHP] guia

O **PHP** A guia mostra os problemas do processo PHP para fornecer uma análise mais profunda dos problemas PHP.

## [!UICONTROL PHP active process details]

![Detalhes do processo ativo PHP](../../assets/tools/php-active-process-details.jpg)

O **[!UICONTROL PHP active process details]** frame mostra os processos PHP, incluindo php-fpm, ao longo do período selecionado.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![Carga do processo PHP](../../assets/tools/php-process-load.jpg)

Este quadro mostra a carga da CPU dos processos PHP-FPM ao longo do período de tempo selecionado.

## [!UICONTROL PHP Memory detail]

![Detalhes da memória PHP](../../assets/tools/php-memory-detail.jpg)

O **[!UICONTROL PHP Memory detail]** quadro mostra o uso de memória de processos PHP no período selecionado.

## [!UICONTROL PHP CPU Utilization]

![Utilização da CPU PHP](../../assets/tools/php-cpu-utilization.jpg)

O **[!UICONTROL PHP CPU Utilization]** frame mostra a % de utilização da CPU de processos PHP no período selecionado.

## [!UICONTROL PHP Process states]

![Estados do processo PHP](../../assets/tools/php-process-states-image-1.jpg)

O **[!UICONTROL PHP Process states]** quadro mostra os estados do processo PHP no período selecionado. Ele será exibido quando os processos PHP forem encerrados e reiniciados. Cuidado com processos PHP terminados que não mostram reinicializações.

* &#39;%AVISO: A terminar ...%&#39;) como &#39;php_term&#39;
* AVISO &#39;%: saindo, adeus!%&#39;) como &#39;php_exit&#39;
* AVISO &#39;%: fpm está em execução, pid%&#39;) como &#39;fpm_start&#39;
* &#39;%AVISO: pronto para lidar com conexões%&#39;) como &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![Erros PHP](../../assets/tools/php-errors-image-1.jpg)

O **[!UICONTROL PHP Errors]** frame mostra o número de erros do trabalhador PHP no período selecionado. As mensagens de erro analisadas e exibidas incluem:

* &#39;%worker_connections não é suficiente%&#39;) como &#39;worker&#39;
* &#39;%PHP Erro fatal: Tamanho de memória permitido!%&#39;) como &#39;mem_size&#39;
* &#39;%saiu no sinal 11 (SIGSEGV)%&#39; como &#39;sig_11&#39;
* &#39;%saiu no sinal 7 (SIGBUS)%&#39; como &#39;sig_7&#39;
* &#39;%aumentar pm.start_servers%&#39;) como &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) como &#39;max_children_cnt&#39;
* &#39;%PHP Erro fatal: Tamanho de memória permitido de%&#39;) como &#39;mem_out_coun&#39;
* &#39;%Não é possível alocar memória para pool%&#39;) como &#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;) como &#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;) como &#39;opc_sv_comments&#39;
* &#39;%PHP Erro fatal: RedisException não capturado: ler erro em conexão%&#39;) como &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![contagem de processos PHP](../../assets/tools/php-processes-count.jpg)

O **[!UICONTROL PHP processes count]** frame mostra uma contagem de processos PHP no período selecionado.

## [!UICONTROL Database Errors]

![Erros do Banco de Dados](../../assets/tools/php-tab-database-errors.jpg)

O **[!UICONTROL Database Errors]** quadro mostra erros de banco de dados no período selecionado. Os erros analisados incluem:

* &#39;%O tamanho da memória alocado para a tabela temporária é superior a 20% de inocdb_buffer_pool_size%&#39;) como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) como &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco cheio%&#39;) como &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;rollback&#39;
* &#39;%Restrição de chave estrangeira falha para tabela%&#39;) como &#39;external_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) como &#39;sql_1114_full&#39;
* &#39;%CRÍTICO: SQLSTATE[HY000] [2006] O servidor MySQL sumiu%&#39;) como &#39;sql_Go&#39;
* &#39;%SQLSTATE[HY000] [1040] Muitas conexões%&#39;) como &#39;sql_1040&#39;
* &#39;%CRÍTICO: SQLSTATE[HY000] [2002]%&#39;) como &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) como &#39;sql_1047&#39;
* &#39;%[Aviso] Interconexão anulada%&#39;) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: Violação de restrição de integridade:%&#39;) como &#39;sql_23000&#39;
* &#39;%1205 Bloquear tempo limite de espera%&#39;) como &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Banco de dados desconhecido%&#39;) como &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: Tabela ou exibição base não encontrada:%&#39;) como &#39;sql_42S02&#39;
* &#39;%Erro geral: 1114%&#39;) como &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Coluna não encontrada: 1054 Unknown column%&#39;) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Erro de sintaxe ou violação de acesso:%&#39;) como &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Violação de cardinalidade:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Cliente com endereço IP%&#39;) como &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Erro geral: 2014%&#39;) como &#39;sql_2014&#39;
* &#39;%1927 A ligação foi eliminada%&#39;) como &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;%[Observação] WSREP: A transferir mapa de memória para o disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Código de erro interno de MariaDB: 1146%&#39;) como &#39;sql_1146&#39;
* &#39;%Código de erro interno de MariaDB: 1062%&#39;) como &#39;sql_1062&#39; ・ &#39;%1062 [Aviso] InnoDB:%&#39;) como &#39;sql_1062_w&#39;
* &#39;%Código de erro interno de MariaDB: 1064%&#39;) como &#39;sql_1064&#39;
* &#39;%InnoDB: Falha de asserção no arquivo%&#39;) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de processos em execução agora: 0%&#39;) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld got signal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 Não é possível adicionar%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Erro geral: 3%&#39;) como &#39;cnt_write_tmp&#39;
* &#39;%Erro geral: 1 %&#39;) como &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InnoDB: Erro (Chave duplicada)%&#39;) como &#39;inocdb_dup_key&#39;

## [!UICONTROL Database traces]

![Rastreamentos do banco de dados](../../assets/tools/php-tab-database-traces.jpg)

O **[!UICONTROL Database traces]** quadro mostra informações de rastreamento do banco de dados. Esse quadro se alinha à exibição resumida de transação APM da linha do tempo selecionada.

## [!UICONTROL Database mysql-slow.log]

![Banco de dados mysql-low.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

O **[!UICONTROL Database mysql-slow.log]** quadro mostra os tipos de instrução de consulta que estavam no `mysql-slow.log` ao longo do período de tempo selecionado.
