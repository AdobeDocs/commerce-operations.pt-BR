---
title: A guia [!UICONTROL Summary]
description: Saiba mais sobre a guia [!UICONTROL Summary] do  [!DNL Observation for Adobe Commerce].
exl-id: b07ed898-a211-4353-a1d4-1b71d4898b93
feature: Configuration, Observability
source-git-commit: 5a0455b61824cb1946e29dba3ff7bfd9d225b110
workflow-type: tm+mt
source-wordcount: '2494'
ht-degree: 0%

---

# A guia [!UICONTROL Summary]

A guia [!UICONTROL Summary] do [!DNL Observation for Adobe Commerce] destina-se a ver rapidamente alguns dos problemas enfrentados pelos sites para ajudá-lo a resolver automaticamente ou identificar possíveis causas raiz de problemas do site. As guias adicionais fornecem informações mais detalhadas sobre os serviços de componentes, banco de dados, infraestrutura e estados do processo.

## [!UICONTROL Transaction Overview]

![Visão geral da transação](../../assets/tools/transaction-overview.jpg)

### [O que é uma transação?](https://docs.newrelic.com/docs/apm/transactions/intro-transactions/transactions-new-relic-apm/#:%7E:text=transactions%20are%20reported.-,What%20is%20a%20transaction%3F,work%20in%20a%20software%20application.&text=For%20APM%2C%20it%20will%20frequency,when%20the%20response%20is%20sent)

&quot;Às [!DNL New Relic], uma transação é definida como uma unidade lógica de trabalho em um aplicativo de software. Especificamente, ele se refere às chamadas de função e chamadas de método que compõem essa unidade de trabalho. Geralmente se refere a uma transação da web, que representa uma atividade que acontece de quando o aplicativo recebe uma solicitação da web até quando a resposta é enviada.&quot;

### Tipos de transações:

**Web:** transações da Web são iniciadas com uma solicitação HTTP. Para a maioria das organizações, elas representam interações centradas no cliente e, portanto, são as transações mais importantes a serem monitoradas.

**Não-Web:** transações não-Web não são iniciadas com uma solicitação da Web. Eles podem incluir processos que não sejam processos de trabalho na Web, processos em segundo plano, scripts, atividade da fila de mensagens e outras tarefas.

Se você observar o quadro **[!UICONTROL Transaction Overview]** acima, houve quase 53.000 transações com uma pontuação APDEX média de 0,76, e 95% dessas transações ocorreram em menos de 2,313 segundos. Esse seria um quadro em que um período mais curto pode mostrar um desvio em relação à média atual se houver uma ocorrência de APDEX durante um período curto.

## [!UICONTROL 404 page errors frame]

O painel de monitoramento de erros ![404 mostrando incidentes de página não encontrados ao longo do tempo](../../assets/tools/404-page-errors.jpg)

O quadro **[!UICONTROL 404 page errors]** lista o [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) e a contagem de erros de página 404 para um período selecionado.

## [!UICONTROL % of Storage Free frame]

![Gráfico de utilização de armazenamento exibindo a porcentagem de espaço disponível em disco](../../assets/tools/percent-of-storage-free.jpg)

O quadro **[!UICONTROL % of Storage Free]** exibe o percentual médio livre das montagens de armazenamento em todos os nós do cluster. Por exemplo, se você tiver um cluster de três nós, o quadro mostrará o \&lt;ponto de montagem\>, \&lt;nome do ambiente\>. Esse quadro pode ser enganoso se houver uma variação entre três nós. Um exemplo de variação seria se o ponto de montagem livre `/data/mysql` fosse um valor diferente no cluster de três nós. Há um quadro na guia [!UICONTROL MySQL] que enquadra os pontos de montagem por nome de nó para ver com mais precisão o que é o armazenamento `/data/mysql` livre em cada nó.

## [!UICONTROL % of system memory that is free frame]

![Gráfico de uso de memória do sistema mostrando a porcentagem de RAM disponível](../../assets/tools/percent-of-system-memory-that-is-free.jpg)

O quadro **% da memória do sistema que está livre** exibe, por nó, a quantidade de memória do sistema que está livre em cada nó.

## [!UICONTROL Swap memory free in bytes]

![memória livre de troca em bytes](../../assets/tools/swap-memory-free-in-bytes.jpg)

O quadro **[!UICONTROL Swap memory free in bytes]** exibe, por nó, a quantidade de memória SWAP livre no nó.

## [!UICONTROL CPU % by host]

![Percentual de CPU por host](../../assets/tools/cpu-percent-by-host.jpg)

A agregação de todos os ambientes e nós é exibida no quadro **[!UICONTROL CPU % by host]**. Você deve desmarcar os ambientes de não produção. Observe também quaisquer instâncias em que todos os nós do ambiente de produção não estejam presentes. Para obter mais dicas sobre alta utilização do CPU, consulte [Solucionar problemas de desempenho usando o New Relic no Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.html?lang=pt-BR).

## [!UICONTROL Alerts during timeframe]

![Painel de notificações de alerta que mostra incidentes dentro do período selecionado](../../assets/tools/alerts-during-timeframe.jpg)

O **[!UICONTROL Alerts during timeframe]** exibe todos os alertas, incluindo o [!UICONTROL Managed Alerts] adicionado pelo suporte da Adobe Commerce.

## [!UICONTROL CPU Usage]

![uso do CPU](../../assets/tools/cpu-usage.jpg)

Se o quadro **[!UICONTROL CPU Usage]** estiver em branco, isso indica que o aplicativo de infraestrutura [!DNL New Relic] não está habilitado. Se seu site está no Starter, você não vê essas informações. Se o seu site for Pro, abra um [tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=pt-BR) para habilitar o [!DNL New Relic Infrastructure] para o seu site.

## [!UICONTROL Average Response Time]

![tempo médio de resposta](../../assets/tools/average-response-time.jpg)

O gráfico **[!UICONTROL Average Response Time]** mostra o tempo médio de resposta para transações (Web e outras).

## [!UICONTROL Long duration cron_schedule updates]

![atualizações de cron_schedule de longa duração](../../assets/tools/long-duration-cron-schedule-updates.jpg)

A tabela **[!UICONTROL cron_schedule]** é gravada no início e no fim dos trabalhos cron. Trabalhos cron de longa duração podem indicar latência na atualização desta tabela, o que pode indicar empilhamento cron ou um problema com a forma como os crons são agendados.

## [!UICONTROL Response Code]

![código de resposta](../../assets/tools/response-code.jpg)

O quadro **[!UICONTROL Response Code]** é uma boa indicação do tráfego da Web e do código de resposta das solicitações. São [!DNL New Relic's] dados de transação, e são facetados pelo `httpResponseCode` retornado.

## [!UICONTROL Web Traffic volume compared with one week ago Magento Managed Alerts Information]

![volume de tráfego na web comparado com uma semana atrás](../../assets/tools/web-traffic-volume-compared.jpg)

Esse quadro exibe o volume de tráfego comparativo da Web da última semana e da semana atual.

## [!UICONTROL Deployment Log Entries]

![entradas do log de implantação](../../assets/tools/deployment-log-entries.jpg)

O quadro **[!UICONTROL Deployment Log Entries]** exibe uma contagem de entradas de log de implantação e de nuvem e compara as contagens pelo nome do log de implantação.

## [!UICONTROL Deployment State]

![estado da implantação](../../assets/tools/deployment-state.jpg)

O quadro **[!UICONTROL Deployment State]** enfoca fases de implantação específicas dos logs de implantação. Estes são alguns exemplos de fases contadas no log e o nome da faceta:

**Fases do Log de Implantação:**

* &#39;%Starting generate command%&#39;) como &#39;start_gen&#39;
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;) como &#39;apply_patches&#39;
* &#39;%Set flag: .static_content_deploy%&#39;) como &#39;SCD&#39;
* &#39;%NOTICE: comando de geração concluído (%) como &#39;gen_compl&#39;
* &#39;%NOTICE: implantação concluída (%) como &#39;deploy_compl&#39;
* &#39;%NOTA: iniciando pós-implantação.%&#39;) como &#39;start_deploy&#39;
* &#39;%NOTICE: a pós-implantação está concluída (%) como &#39;implantação&#39;
* &#39;%deploy-complete%&#39;) como &#39;cl_deploy_compl&#39;

## [!UICONTROL IP Frequency]

![Frequência de IP](../../assets/tools/ip-frequency.jpg)

O quadro **[!UICONTROL IP Frequency]** conta os status (&#39;MISS&#39; e &#39;PASS&#39;) para cada IP dos logs [!DNL Fastly]. As solicitações da Web com esses status chegam ao servidor de origem e adicionarão carga ao servidor. Ele mostra os vinte principais endereços em frequência. Esse quadro pode ser usado para detectar ataques de IP ou origens de carga pesada em um site.

## [!UICONTROL IP Response – top 20 URLs in duration]

![resposta ip - as 20 URLs principais em duração](../../assets/tools/ip-response-top-20-urls.jpg)

O quadro **[!UICONTROL IP Response – top 20 URLs in duration]** exibe as URLs com maior duração em resposta. Ele pode indicar arquivos de imagem ou páginas grandes, API ou páginas com a maior duração de resposta.

## [!UICONTROL API Calls by IP]

![chamadas de api por ip](../../assets/tools/api-calls-by-ip.jpg)

O quadro **[!UICONTROL API Calls by IP]** ajuda a identificar tráfego intenso nas APIs e nos endereços IP que fazem solicitações das URLs da API.

## [!UICONTROL API Calls by IP, details by URL]

![Análise de solicitação de API mostrando chamadas agrupadas por endereço IP e URL de ponto de extremidade](../../assets/tools/api-calls-by-ip-details-by-url.jpg)

O quadro **[!UICONTROL API Calls by IP, details by URL]** fornece detalhes de tráfego intenso em relação às APIs e detalhes das URLs que fazem as solicitações.

## [!UICONTROL IP Frequency Rate per minute]

![taxa de frequência ip por minuto](../../assets/tools/ip-frequency-rate-per-minute.jpg)

Às vezes, é difícil saber qual endereço IP tem mais solicitações nos outros quadros. O quadro **[!UICONTROL IP Frequency Rate per minute]** mostra a taxa por minuto por endereço IP.

## [!UICONTROL Potential Bots]

![bots em potencial](../../assets/tools/potential-bots.jpg)

O quadro **[!UICONTROL Potential Bots]** analisa as solicitações com um nome request_user_agent como NULL ou &#39;%bot%&#39;. Normalmente, o request_user_agent &#39;%bot%&#39; segue a configuração da política no arquivo `robots.txt`.

## [!UICONTROL Transaction Errors]

![erros de transação](../../assets/tools/transaction-errors.jpg)

O quadro **[!UICONTROL Transaction Errors]** exibe a contagem de erros de transação de [!DNL New Relic].

## [!UICONTROL Nginx access by node]

Acesso de ![nginx por nó](../../assets/tools/nginx-access-by-node.jpg)

O quadro **[!UICONTROL Nginx access by node]** analisa as contagens de `access.log` por nó. É útil ver se a carga está distribuída uniformemente. Geralmente, mostra quando um nó cai. O quadro também mostra a carga no site.

## [!UICONTROL Galera Log]

![log de galera](../../assets/tools/galera-log.jpg)

[[!DNL Galera]](https://galeracluster.com/library/galera-documentation.pdf) é usado para o cluster de banco de dados. Esse quadro focaliza sinais específicos do cluster [!UICONTROL Galera]. Os sinais se concentram nos nós que entram e saem do cluster, o que é um comportamento normal para manter a integridade dos dados do banco de dados. Os nós são mantidos sincronizados à medida que o estado do cluster [!UICONTROL Galera] é alterado.

**Lista de [!UICONTROL Galera] alterações de estado:**

* &#39;%1047 O WSREP ainda não preparou o nó para uso do aplicativo (%node_not_prep_for_use&#39;)
* &#39;%\[ERROR\] WSREP: Falha ao ler de: wsrep_sst_xtrabackup-v2%&#39;) como &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: Processo concluído com erro: wsrep_sst_xtrabackup-v2 %&#39;) como &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) como &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;) como &#39;susp_node&#39;
* &#39;%member = 3/3 (unido/total)%&#39;) como &#39;3of3&#39;
* &#39;%member = 2/3 (unido/total)%&#39;) como &#39;2of3&#39;
* &#39;%member = 2/2%&#39;) como &#39;2of2&#39; * &#39;%member = 1/2%&#39;) como &#39;1of2&#39; * &#39;%member = 1/3%&#39;) como &#39;1of3&#39;
* &#39;%member = 1/1%&#39;) como &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) como &#39;sql_restart&#39;
* &#39;%Quorum: Nenhum nó com estado concluído:%&#39;) como &#39;no_node_count&#39;
* &#39;%WSREP: Membro 0%&#39;) como &#39;mem_0&#39;
* &#39;%WSREP: Membro 1.0%&#39;) como &#39;mem_1&#39;
* &#39;%WSREP: Membro 2%&#39;) como &#39;mem2&#39;
* &#39;%WSREP: Sincronizado com grupo, pronto para conexões&#39;) como &#39;pronto&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) como &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Note\] WSREP: Nova exibição de cluster: estado global:%&#39;) como &#39;galera_cluster_view_change&#39;

Esses sinais podem indicar problemas de armazenamento, memória ou query se o estado mudar com frequência.

## [!UICONTROL Database errors]

![erros do banco de dados](../../assets/tools/database-errors.jpg)

**Lista de mensagens ou erros de banco de dados detectados:**

* &#39;%Memory size alocado para a tabela temporária é mais de 20% de innodb_buffer_pool_size%&#39;) como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) como &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco cheio%&#39;) como &#39;disk_full&#39;
* &#39;%Número do erro 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;reversão&#39;
* &#39;%Foreign key constraint falha para a tabela &#39;%&#39;) como &#39;Foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) como &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2006\] O servidor MySQL desapareceu%&#39;) como &#39;sql_went&#39;
* &#39;%SQLSTATE\[HY000\] \[1040\] Muitas conexões%&#39;) como &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2002\]%&#39;) as &#39;sql_2002&#39;
* &#39;%SQLSTATE\[08S01\]:%&#39;) como &#39;sql_1047&#39;
* &#39;%\[Aviso\] Conexão cancelada%&#39;) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE\[23000\]: violação de restrição de integridade:%&#39;) como &#39;sql_23000&#39;
* &#39;%1205 Tempo limite de espera de bloqueio (%1) como &#39;sql_1205&#39;
* &#39;%SQLSTATE\[HY000\] \[1049\] Banco de dados desconhecido%&#39;) como &#39;sql_1049&#39;
* &#39;%SQLSTATE\[42S02\]: Tabela ou exibição base não encontrada:%&#39;) como &#39;sql_42S02&#39;
* &#39;%General error: 1114%&#39;) as &#39;sql_1114&#39;
* &#39;%SQLSTATE\[40001\]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE\[42S22\]: Coluna não encontrada: 1054 Coluna desconhecida%&#39;) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE\[42000\]: Erro de sintaxe ou violação de acesso:%&#39;) como &#39;sql_42000&#39;
* &#39;%SQLSTATE\[21000\]: Violação de cardinalidade:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE\[22003\]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE\[HY000\] \[9000\] Cliente com endereço IP%&#39;) como &#39;sql_9000&#39;
* &#39;%SQLSTATE\[HY000\]: Erro geral: 2014%&#39;) como &#39;sql_2014&#39;
* &#39;%1927 Conexão eliminada (%1927) como &#39;sql_1927&#39;
* &#39;%1062 \[\ERRO\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;%\[Nota\] WSREP: Liberando mapa de memória para disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Código de erro interno do MariaDB: 1146%&#39;) como &#39;sql_1146&#39;
* &#39;%Internal MariaDB (código de erro: 1062%&#39;) as &#39;sql_1062&#39; * &#39;%1062 \[Aviso\] InnoDB:%&#39;) as &#39;sql_1062_w&#39;
* &#39;%Código de erro interno do MariaDB: 1064%&#39;) como &#39;sql_1064&#39;
* &#39;%InDB: falha de asserção no arquivo &#39;%&#39;) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de processos em execução agora: 0%&#39;) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld obteve sinal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 Não é possível adicionar &#39;%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE\[HY000\]: Erro geral: 3%&#39;) como &#39;cnt_wrt_tmp&#39;
* &#39;%General error: 1 %&#39;) como &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InDB: Erro (Chave duplicada)%&#39;) como &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![rastreamentos do banco de dados](../../assets/tools/database-traces.jpg)

O quadro **[!UICONTROL Database traces]** verifica os dados da entidade [sql trace](https://docs.newrelic.com/docs/apm/transactions/transaction-traces/transaction-traces-database-queries-page/) de [!DNL New Relic] e retorna o caminho do rastreamento.

## [!UICONTROL Database mysql-slow.log]

![banco de dados mysql-slow.log](../../assets/tools/database-mysql-slow-log.jpg)

O quadro **[!UICONTROL Database mysql-slow.log]** faz uma contagem de entradas no [mysql-slow.log](https://dev.mysql.com/doc/refman/5.7/en/slow-query-log.html) por tipo de solicitação de consulta. Ele isola visualmente intervalos de tempo que podem ser de interesse no mysql-slow.log (log de consultas lentas). Consultas de tabelas sem índices ou consultas que atualizam tabelas grandes podem bloquear outras consultas.

## [!UICONTROL Redis synchronization from Log]

![redis sincronização do log](../../assets/tools/redis-synchronization-from-log.jpg)

[[!DNL Redis]](https://redis.io/about/) é um repositório de estrutura de dados na memória de código aberto (BSD licenciado) usado como banco de dados, cache e agente de mensagens. Ele pode fazer cache de banco de dados e sessão, se configurado. O quadro **[!UICONTROL Redis synchronization from Log]** focaliza a [[!DNL Redis] sincronização](https://redis.io/docs/latest/operate/oss_and_stack/management/replication/). Quanto maior o conjunto de dados [!DNL Redis], mais provável será que haja problemas com a sincronização (mais dados para manter sincronizados).

**[!DNL Redis]erros e mensagens:**

* &#39;%Sincronização SLAVE: sem espaço restante no dispositivo (%SLAVE synchronization: No space left on device%) as &#39;space&#39;
* &#39;%Server started, Redis version%&#39;) como &#39;serv_start&#39;
* &#39;%O servidor está pronto para aceitar conexões&#39;) como &#39;pronto&#39;
* &#39;%Conexão com mestre perdida.%&#39;) como &#39;mstr_lost&#39;
* &#39;%+sentinela%&#39;) como &#39;+sentinela&#39;
* &#39;%-sdown sentinel%&#39;) como &#39;-sentinal&#39;
* &#39;%-sdown slave%&#39;) como &#39;-slave&#39;, &#39;%+sdown slave%&#39;) como &#39;+slave&#39;
* &#39;%-failover-abort-not-elected master (mymaster%&#39;) como &#39;-failover&#39;
* &#39;%+failover-abort-not-elected master (mymaster%&#39;) como &#39;+failover&#39;
* &#39;%Partial resynchronization not possible (no cached master)%&#39;) as &#39;part_sync_err&#39;
* &#39;%MASTER anulou a replicação com um erro: ERR Can%&#39;) como &#39;mstr_sync_err&#39;
* &#39;%Master não dá suporte a PSYNC ou está em estado de erro (%) como &#39;mstr_psync_err&#39;
* &#39;%SLAVE sync: Concluído com êxito (%&#39;) como &#39; slv_sync_suc&#39;
* &#39;%MASTER anulou a replicação com um erro: ERR Pode%&#39;) como &#39;mstr_sync_err,count&#39;
* &#39;%OOM comando não permitido quando usado memória%&#39;) como &#39; max_mem_err&#39;
* &#39;%CredisException(código: 0): erro de leitura na conexão%&#39;) como &#39;credis_read_error&#39;
* &#39;%Uncaught RedisException:%&#39;) como &#39;redis_excp_err&#39;
* &#39;%psync agendado para ser fechado o mais rápido possível para a substituição do buffer de saída&#39;) como &#39;output_buf_err&#39;

## [!UICONTROL PHP process states]

![estados do processo PHP](../../assets/tools/php-process-states.jpg)

A forma como os processos PHP se comportam depende da [configuração](https://www.php.net/manual/en/install.fpm.configuration.php). A configuração é complexa, com muitas variáveis e opções. O quadro **[!UICONTROL PHP process states]** ajuda você a entender quando os processos PHP são terminados e reiniciados.

### [!UICONTROL PHP errors]

![erros do php](../../assets/tools/php-errors.jpg)

O quadro **[!UICONTROL PHP errors]** mostra o número de erros de PHP com workers no intervalo de tempo selecionado. Para obter mais informações, consulte [configurações do Adobe Commerce PHP](../../installation/prerequisites/php-settings.md).

**Mensagens e erros de PHP:**

* &#39;%worker_connections are not insufficient%&#39;) como &#39;worker&#39;
* Erro fatal &#39;%PHP: tamanho de memória permitido!%&#39;) como &#39;mem_size&#39;
* &#39;%exited on signal 11 (SIGSEGV)%&#39;) como &#39;sig_11&#39;
* &#39;%exited on signal 7 (SIGBUS)%&#39;) como &#39;sig_7&#39;
* &#39;%aumente pm.start_servers%&#39;) como &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) como &#39;max_children_cnt&#39;
* &#39;%PHP Erro fatal: tamanho de memória permitido de &#39;%&#39;) como &#39;mem_exhst_count&#39;
* &#39;%Unable to allocate memory for pool%&#39;) como &#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;) como &#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;) como &#39;opc_sv_comments&#39;
* &#39;%PHP Erro fatal: RedisException não detectada: erro de leitura na conexão &#39;%&#39;) como &#39;php_exc&#39;

## [!UICONTROL PHP processes]

![processos php](../../assets/tools/php-processes.jpg)

[PHP-FPM](https://php-fpm.org/) é um [!UICONTROL FastCGI Process Manager] usado por [!DNL Nginx]. Para saber mais sobre os requisitos do sistema, consulte [requisitos de versão do PHP mapeados para versões do Adobe Commerce](../../installation/system-requirements.md). O quadro **[!UICONTROL PHP processes]** mostra o número de processos PHP em execução em um determinado momento na linha do tempo selecionada.

## [!UICONTROL Secondary processes]

![processos secundários](../../assets/tools/secondary-processes.jpg)

Processos secundários podem afetar a resposta do local. O quadro **[!UICONTROL Secondary processes]** indica um ou mais processos que podem estar adicionando carga ao site. O banco de dados tem principalmente os processos mais secundários em execução.

## [!UICONTROL Traffic vs Week Ago]

![tráfego vs semana atrás](../../assets/tools/traffic-vs-week-ago.jpg)

O quadro **[!UICONTROL Traffic vs Week Ago]** verifica o tráfego do site (solicitações) dos logs [!DNL Fastly] com status de cache (&#39;MISS&#39;, &#39;PASS&#39;). Essas solicitações adicionam carga aos servidores de origem. Esse quadro exibe o volume de solicitação da Web comparativo da semana atual e da semana passada durante o mesmo período.

## [!UICONTROL Fastly Cache]

![Cache Rápido](../../assets/tools/fastly-cache.jpg)

O quadro **[!UICONTROL Fastly Cache]** mostra uma exibição agregada do status do cache das solicitações dos logs [!DNL Fastly]. Se você selecionar ERRO, ele mostrará a porcentagem de erros nas solicitações. Normalmente, isso aumenta quando o servidor de origem não responde com rapidez suficiente às solicitações de página.

## [!UICONTROL Page Rendering]

![Métricas de desempenho da página mostrando a análise do tempo de renderização](../../assets/tools/page-rendering.jpg)

O quadro **[!UICONTROL Page Rendering]** exibe a duração média da renderização de página da semana atual a partir da origem de exibição de página de [!DNL New Relic] em comparação à semana anterior durante o mesmo período de tempo.

## [!UICONTROL Page loading detail]

![Detalhamento detalhado do desempenho de carregamento da página mostrando os componentes de tempo de carregamento](../../assets/tools/page-loading-detail.png)

O quadro **[!UICONTROL Page loading detail]** descreve os eventos de carregamento de página. Ela detalha os significados dessas facetas. Esta é a consulta executada para este quadro:

`SELECT percentile(timeToResponseStart, 50) AS 'first byte', percentile(firstPaint, 50) as 'First paint', percentile(firstContentfulPaint, 50) as 'First contentful paint', percentile(timeToDomContentLoadedEventEnd, 50) AS 'DOM content loaded', percentile(duration, 50) AS 'Window load + AJAX' FROM BrowserInteraction TIMESERIES`

## [!UICONTROL Transactions – Avg, Max, Min]

![transações - média, máx, mín](../../assets/tools/transactions-avg-max-min.jpg)

A duração da transação é em segundos. Dependendo da transação, ela poderá afetar outras transações se for de longa duração. As transações listadas em nome e as durações são para o período específico. Se houver um período de tempo de problema conciso, redimensione o seletor de data/hora [!DNL Observation for Adobe Commerce] para esse período de tempo estreito.

## [!UICONTROL Admin Activities]

![atividades do administrador](../../assets/tools/admin-activities.jpg)

O quadro **[!UICONTROL Admin Activities]** identifica transações com um usuário administrador.

## [!UICONTROL Order transactions (default?)]

![Padrão de transações da ordem](../../assets/tools/order-transactions-default.jpg)

O quadro **[!UICONTROL Order transactions (default?)]** procura transações `request.headers.host` de transações, onde o nome = `WebTransaction/Action/checkout/onepage/success`. Se o URL de sucesso do pedido for diferente, esse quadro não terá dados.

## [!UICONTROL Elasticsearch Index information]

![informações de índice de elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

**[Status do Elasticsearch:](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)**

* Verde: Todos os compartilhamentos são atribuídos.
* Amarelo: todos os compartilhamentos primários são atribuídos, mas um ou mais compartilhamentos de réplica não são atribuídos. Se um nó no cluster falhar, alguns dados poderão ficar indisponíveis até que esse nó seja reparado.
* Vermelho: um ou mais fragmentos principais não foram atribuídos, portanto, alguns dados não estão disponíveis. Isso pode ocorrer brevemente durante a inicialização do cluster, conforme os compartilhamentos principais são atribuídos.

## [!UICONTROL Elasticsearch Errors]

![erros de elasticsearch](../../assets/tools/elasticsearch-errors.jpg)

**[!DNL Elasticsearch]erros:**

* &#39;%all_shards failed%&#39; como &#39;all_shards_failed&#39;
* &#39;%NoNodesAvailableException%&#39; como &#39;no_alive_nodes&#39;
* &#39;%PHP Erro fatal: Erro não detectado: Parâmetros incorretos para Elasticsearch%&#39; como &#39;error_param&#39;
* &#39;%Você pode corrigir esse problema atualizando o serviço Elasticsearch na infraestrutura do Magento Cloud para a versão%&#39; como &#39;ver_err&#39;
* Status de integridade de &#39;%cluster alterado de \[YELLOW\] para \[RED\] (motivo:%&#39; como &#39;yel_red&#39;
* &#39;%No space left on device%&#39; como &#39;no_space&#39;
* &#39;% Falha ao executar &lbrack;SearchRequest&lbrace;searchType=%&#39; as &#39;failed_query&#39;

## [!UICONTROL Cron view]

![exibição do cron](../../assets/tools/cron-view.jpg)

O quadro **[!UICONTROL Cron view]** procura no log de cron o equilíbrio entre o número de crons iniciado e o número de crons terminando.


## [!UICONTROL Cron error]

![erro de cron](../../assets/tools/cron-error.png)

**Erros Cron do cron.log:**

* &#39;%_stg%&#39; como &#39;stg_crons&#39;
* &#39;%Não foi possível adquirir bloqueio para o trabalho cron%&#39; como &#39;cron_lock&#39;
* &#39;%General error: 2006 O servidor MySQL desapareceu%&#39; como &#39;mysql_has_went_away&#39;
* &#39;%error%&#39; como &#39;erro&#39;
* &#39;%Erro geral: 1205 tempo limite de espera de bloqueio excedido%&#39; as sql_1205_cron

## [!UICONTROL cron_schedule table updates]

![atualizações da tabela cron_schedule](../../assets/tools/cron-schedule-table-updates.jpg)

O quadro **[!UICONTROL cron_schedule table updates]** observa a duração máxima em segundos, em que as atualizações de operações de armazenamento de dados envolvem a tabela cron_schedule. Ela é facetada no tipo de solicitação SQL.

## [!UICONTROL Datastore Operations Tables]

![tabelas de operações de armazenamento de dados](../../assets/tools/datastore-operations-tables.jpg)

Este quadro **[!UICONTROL Datastore Operations Tables]** exibe as 25 principais operações por tempo de duração, nome da tabela e tipo de solicitação SQL. Passe o mouse sobre os picos para ver detalhes de qual tabela estava sendo acessada e por que tipo de solicitação.

## [!UICONTROL Cache Flush]

![liberação de cache](../../assets/tools/cache-flush.jpg)

**Liberações de cache detectadas:**

* &#39;%config%&#39; como &#39;config_cache_flush&#39;
* &#39;%layout%&#39; como &#39;layout_cache_flush&#39;
* &#39;%block_html%&#39; como &#39;block_html_cache_flush&#39;
* &#39;%collections%&#39; como &#39;collections_cache_flush&#39;
* &#39;%refletion%&#39; como &#39;refletion_cache_flush&#39;
* &#39;%db_ddl%&#39; como &#39;db_ddl_cache_flush&#39;
* &#39;%compilation_config%&#39; como &#39;compilation_config_cache_flush&#39;
* &#39;%eav%&#39; como &#39;eav_cache_flush&#39;
* &#39;%customer_notification%&#39; como &#39;cust_notif_cache_flush&#39;
* &#39;%config_integration%&#39; como &#39;config_integ_cache_flush&#39;
* &#39;%config_integration_api%&#39; como &#39;config_integ_api_cache_flush&#39;
* &#39;%full_page%&#39; como &#39;full_page_cache_flush&#39;
* &#39;%config_webservice%&#39; como &#39;config_webserv_cache_flush&#39;
* &#39;%translate%&#39; como &#39;translate_cache_flush&#39;
