---
user-guide-title: Guia de configuração
user-guide-description: Configurar os recursos e serviços do aplicativo Adobe Commerce ou Magento Open Source.
feature: Configuration
source-git-commit: 68c4cfc29735d2ea296f579ed0a0ff52db3fdd9f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Guia de configuração {#configuration-guide}

+ [Visão geral](overview.md)
+ Configuração geral {#setup}
   + [Inicialização e inicialização do aplicativo](bootstrap/initialization.md)
   + [Modos de aplicação](bootstrap/application-modes.md)
   + [parâmetros de Bootstrap](bootstrap/set-parameters.md)
   + [Criação de perfil](bootstrap/mage-profiler.md)
   + [Caminhos de diretório base](bootstrap/mage-directory.md)
+ Implantação {#deployment}
   + [Visão geral da implantação](deployment/overview.md)
   + [Implantação de computador único](deployment/single-machine.md)
   + [Implantação de pipeline](deployment/technical-details.md)
   + [Pré-requisitos](deployment/prerequisites.md)
   + [Configuração do sistema de desenvolvimento](deployment/development-system.md)
   + [Configuração do sistema de compilação](deployment/build-system.md)
   + [Configuração do sistema de produção](deployment/production-system.md)
   + [Permissões de acesso a sistemas de arquivos](deployment/file-system-permissions.md)
   + Exemplos {#examples}
      + [Uso de uma configuração compartilhada](deployment/example-shared-configuration.md)
      + [Uso de comandos da CLI](deployment/example-using-cli.md)
      + [Uso de variáveis de ambiente](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Visão geral do armazenamento em cache](cache/caching-overview.md)
   + [Tipos de cache](cache/cache-types.md)
   + [Opções de cache](cache/cache-options.md)
   + [Cache L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configurar Redis](cache/config-redis.md)
      + [Usar Redis para cache padrão](cache/redis-pg-cache.md)
      + [Usar Redis para armazenamento de sessão](cache/redis-session.md)
   + Verniz {#varnish}
      + [Visão geral do verniz](cache/config-varnish.md)
      + [Instalar verniz](cache/config-varnish-install.md)
   + [Servidor da Web](cache/config-varnish-server.md)
   + [Configurar o aplicativo do Commerce](cache/configure-varnish-commerce.md)
   + [Configuração avançada de verniz](cache/config-varnish-advanced.md)
   + [Limpeza de cache](cache/use-varnish-cache.md)
   + [Cache limpando várias instâncias de Verniz](cache/use-multiple-varnish-cache.md)
   + [Verificar configuração de verniz](cache/config-varnish-final.md)
   + [Bloco ESI de verniz](cache/use-varnish-esi.md)
   + [Cache de conteúdo estático](cache/static-content-signing.md)
+ Linha de comando {#cli}
   + [Ferramenta de linha de comando](cli/config-cli.md)
   + [Comandos comuns](cli/common-cli-commands.md)
   + [Habilitar registro](cli/enable-logging.md)
   + [Gerenciar o cache](cli/manage-cache.md)
   + [Gerenciar indexadores](cli/manage-indexers.md)
   + [Configurar trabalhos cron](cli/configure-cron-jobs.md)
   + [Compilar código](cli/code-compiler.md)
   + [Modo de operação](cli/set-mode.md)
   + [Iniciar consumidores da fila de mensagens](cli/start-message-queues.md)
   + [Marca-texto URN](cli/urn-highlighter.md)
   + [Relatórios de dependência](cli/dependency-reports.md)
   + [Localização](cli/localization.md)
   + Gerenciamento de configuração {#configuration-management}
      + [Definir valores](cli/set-configuration-values.md)
      + [Configurações de exportação](cli/export-configuration.md)
      + [Importar dados](cli/import-configuration.md)
   + Exibição estática {#static-view}
      + [Estratégias de implantação](cli/static-view-file-strategy.md)
      + [Implantar arquivos de exibição estáticos](cli/static-view-file-deployment.md)
   + [Criar ligações simbólicas](cli/create-symlinks.md)
   + [Executar testes de unidade](cli/unit-tests.md)
   + [Converter arquivos de layout](cli/convert-layout-files.md)
   + [Gerar dados para teste de desempenho](cli/generate-data.md)
   + [Executar utilitários de suporte (somente Commerce)](cli/run-support-utilities.md)
+ Arquivos de configuração {#files}
   + [Arquivos de configuração para implantação](reference/deployment-files.md)
   + [Tipos de configuração](reference/config-create-types.md)
   + [Arquivos do módulo](reference/module-files.md)
   + [Saída do módulo](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Caminhos de configuração {#paths}
   + [Geral](reference/config-reference-general.md)
   + [Extensão B2B](reference/config-reference-b2b.md)
   + [Catálogo](reference/config-reference-catalog.md)
   + [Clientes](reference/config-reference-customers.md)
   + [Métodos de pagamento](reference/config-reference-payment.md)
   + [Vendas](reference/config-reference-sales.md)
   + [Serviços](reference/config-reference-services.md)
   + [Configurações sensíveis e específicas do sistema](reference/config-reference-sens.md)
   + [Substituir definições de configuração](reference/override-config-settings.md)
+ Cron Jobs {#crons}
   + [Trabalhos e grupos do Cron](cron/custom-cron.md)
   + [Personalizar referência de crons](cron/custom-cron-reference.md)
   + [Configurar um trabalho cron personalizado](cron/custom-cron-tutorial.md)
+ Logs {#logs}
   + [Logs personalizados](logs/custom-logging.md)
   + [Interface do agente de log](logs/logger-interface.md)
   + [Registrar atividade do banco de dados](logs/database-activity.md)
   + [Gravar em um arquivo de log personalizado](logs/custom-log-files.md)
+ Filas de Mensagens {#message-queues}
   + [Estrutura da fila de mensagens](queues/message-queue-framework.md)
   + [Gerenciar filas de mensagens](queues/manage-message-queues.md)
   + [Configurar o Amazon MQ](queues/aws-mq.md)
   + [Consumidores](queues/consumers.md)
+ Vários sites {#multi-sites}
   + [Vários sites e visualizações](multi-sites/ms-overview.md)
   + [ID de Incremento da entidade de banco de dados](multi-sites/change-increment-id.md)
   + [Configurar no Administrador](multi-sites/ms-admin.md)
   + [Configurar com Nginx](multi-sites/ms-nginx.md)
   + [Configuração com o Apache](multi-sites/ms-apache.md)
+ Mecanismo de pesquisa {#search}
   + [Visão geral dos mecanismos de pesquisa](search/overview-search.md)
   + [Configurar mecanismo de pesquisa](search/configure-search-engine.md)
   + [Filtrar com palavras irrelevantes](search/search-stopwords.md)
+ Segurança {#security}
   + [Visão geral de segurança](security/overview.md)
   + [Hash de senha](security/password-hashing.md)
   + [Intoxicação de cache](security/cache-poisoning.md)
   + [PHP cron seguro](security/secure-cron-php.md)
   + [TXT de segurança](security/security-txt.md)
   + [Cabeçalho X-Frame-Options](security/xframe-options.md)
+ Armazenamento {#storage}
   + [Database profiler](storage/db-profiler.md)
   + Armazenamento remoto {#remote-storage}
      + [Módulo de armazenamento remoto](remote-storage/remote-storage.md)
      + [AWS S3 bucket](remote-storage/remote-storage-aws-s3.md)
      + [Redimensionamento de imagem](remote-storage/remote-storage-image-resize.md)
      + [Armazenamento remoto para nuvem](remote-storage/cloud-support.md)
   + Armazenamento de sessão {#session-storage}
      + [Local de armazenamento da sessão](storage/sessions.md)
      + [memcached para armazenamento de sessão](storage/memcached.md)
      + [memcached no CentOS](storage/memcache-centos.md)
      + [memcached no Ubuntu](storage/memcache-ubuntu.md)
   + Dividir banco de dados {#split-db}
      + [Visão geral da divisão do banco de dados](storage/multi-master.md)
      + [Configuração automática](storage/multi-master-masterdb.md)
      + [Configuração manual](storage/multi-master-manual.md)
      + [Verificar banco de dados dividido](storage/multi-master-verify.md)
      + [Replicação de banco de dados](storage/multi-master-replication.md)
      + [Reverter para um único banco de dados](storage/revert-split-database.md)
+ [Retornar aos Guias operacionais](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)