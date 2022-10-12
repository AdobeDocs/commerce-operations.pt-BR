---
user-guide-title: Guia de configuração
user-guide-description: Configure os recursos e serviços do aplicativo Adobe Commerce ou Magento Open Source.
source-git-commit: b872a61f74818990833ba6b48e061fa1ca69b7cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Guia de configuração {#configuration-guide}

+ [Visão geral](overview.md)
+ Configuração geral {#setup}
   + [Inicialização e inicialização do aplicativo](bootstrap/initialization.md)
   + [Modos de aplicativo](bootstrap/application-modes.md)
   + [Parâmetros de Bootstrap](bootstrap/set-parameters.md)
   + [Criação de perfis](bootstrap/mage-profiler.md)
   + [Caminhos do diretório base](bootstrap/mage-directory.md)
+ Implantação {#deployment}
   + [Visão geral da implantação](deployment/overview.md)
   + [Implantação de máquina única](deployment/single-machine.md)
   + [Implantação de pipeline](deployment/technical-details.md)
   + [Pré-requisitos](deployment/prerequisites.md)
   + [Configuração do sistema de desenvolvimento](deployment/development-system.md)
   + [Criar configuração do sistema](deployment/build-system.md)
   + [Configuração do sistema de produção](deployment/production-system.md)
   + [Permissões de acesso aos sistemas de arquivos](deployment/file-system-permissions.md)
   + Exemplos {#examples}
      + [Uso de uma configuração compartilhada](deployment/example-shared-configuration.md)
      + [Uso de comandos CLI](deployment/example-using-cli.md)
      + [Uso de variáveis de ambiente](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Visão geral do armazenamento em cache](cache/caching-overview.md)
   + [Tipos de cache](cache/cache-types.md)
   + [Opções de cache](cache/cache-options.md)
   + [Cache L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configurar Redis](cache/config-redis.md)
      + [Usar Redis para cache padrão](cache/redis-pg-cache.md)
      + [Use Redis para armazenamento de sessão](cache/redis-session.md)
   + Verniz {#varnish}
      + [Visão geral variável](cache/config-varnish.md)
      + [Instalar o Varnish](cache/config-varnish-install.md)
   + [Servidor da Web](cache/config-varnish-server.md)
   + [Configurar aplicativo do Commerce](cache/configure-varnish-commerce.md)
   + [Configuração Varnish avançada](cache/config-varnish-advanced.md)
   + [Limpeza de cache](cache/use-varnish-cache.md)
   + [Limpeza de cache em várias instâncias do Varnish](cache/use-multiple-varnish-cache.md)
   + [Verificar configuração Varna](cache/config-varnish-final.md)
   + [Bloco ESI Varno](cache/use-varnish-esi.md)
   + [Cache de conteúdo estático](cache/static-content-signing.md)
+ Linha de comando {#cli}
   + [Ferramenta Linha de comando](cli/config-cli.md)
   + [Comandos comuns](cli/common-cli-commands.md)
   + [Ativar registro](cli/enable-logging.md)
   + [Gerenciar o cache](cli/manage-cache.md)
   + [Gerenciar indexadores](cli/manage-indexers.md)
   + [Configurar trabalhos do cron](cli/configure-cron-jobs.md)
   + [Compilar código](cli/code-compiler.md)
   + [Modo de operação](cli/set-mode.md)
   + [Iniciar consumidores de fila de mensagens](cli/start-message-queues.md)
   + [Realce de URN](cli/urn-highlighter.md)
   + [Relatórios de dependência](cli/dependency-reports.md)
   + [Localização](cli/localization.md)
   + Gerenciamento de configurações {#configuration-management}
      + [Definir valores](cli/set-configuration-values.md)
      + [Exportar configurações](cli/export-configuration.md)
      + [Importar dados](cli/import-configuration.md)
   + Exibição estática {#static-view}
      + [Estratégias de implantação](cli/static-view-file-strategy.md)
      + [Implantar arquivos de visualização estáticos](cli/static-view-file-deployment.md)
   + [Criar links simbólicos](cli/create-symlinks.md)
   + [Executar testes de unidade](cli/unit-tests.md)
   + [Converter arquivos de layout](cli/convert-layout-files.md)
   + [Gerar dados para teste de desempenho](cli/generate-data.md)
   + [Executar utilitários de suporte (somente Comércio)](cli/run-support-utilities.md)
+ Arquivos de configuração {#files}
   + [Arquivos de configuração para implantação](reference/deployment-files.md)
   + [Tipos de configuração](reference/config-create-types.md)
   + [Arquivos de módulo](reference/module-files.md)
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
   + [Substituir configurações](reference/override-config-settings.md)
+ Trabalhos Cron {#crons}
   + [Trabalhos e grupos Cron](cron/custom-cron.md)
   + [Personalização de referência de crons](cron/custom-cron-reference.md)
   + [Configurar um trabalho cron personalizado](cron/custom-cron-tutorial.md)
+ Logs {#logs}
   + [Logs personalizados](logs/custom-logging.md)
   + [Interface do logger](logs/logger-interface.md)
   + [Atividade do banco de dados de log](logs/database-activity.md)
   + [Gravar em um arquivo de log personalizado](logs/custom-log-files.md)
+ Filas de Mensagens {#message-queues}
   + [Estrutura da fila de mensagens](queues/message-queue-framework.md)
   + [Gerenciar filas de mensagens](queues/manage-message-queues.md)
   + [Configurar o Amazon MQ](queues/aws-mq.md)
+ Vários sites {#multi-sites}
   + [Vários sites e visualizações](multi-sites/ms-overview.md)
   + [ID de Incremento da entidade de banco de dados](multi-sites/change-increment-id.md)
   + [Configurar no Administrador](multi-sites/ms-admin.md)
   + [Configurar com Nginx](multi-sites/ms-nginx.md)
   + [Configurar com o Apache](multi-sites/ms-apache.md)
+ Mecanismo de pesquisa {#search}
   + [Visão geral dos mecanismos de pesquisa](search/overview-search.md)
   + [Configurar mecanismo de pesquisa](search/configure-search-engine.md)
   + [Filtrar com paradas](search/search-stopwords.md)
+ Segurança {#security}
   + [Visão geral de segurança](security/overview.md)
   + [Hash de senha](security/password-hashing.md)
   + [Envenenamento de cache](security/cache-poisoning.md)
   + [Secure cron PHP](security/secure-cron-php.md)
   + [TXT de segurança](security/security-txt.md)
   + [Cabeçalho X-Frame-Options](security/xframe-options.md)
+ Armazenamento {#storage}
   + [Profiler do banco de dados](storage/db-profiler.md)
   + Armazenamento remoto {#remote-storage}
      + [Módulo de armazenamento remoto](remote-storage/remote-storage.md)
      + [Bucket do AWS S3](remote-storage/remote-storage-aws-s3.md)
      + [Redimensionamento de imagem](remote-storage/remote-storage-image-resize.md)
      + [Armazenamento remoto para nuvem](remote-storage/cloud-support.md)
   + Armazenamento de sessão {#session-storage}
      + [Local de armazenamento da sessão](storage/sessions.md)
      + [armazenado em cache para armazenamento de sessão](storage/memcached.md)
      + [armazenado em cache no CentOS](storage/memcache-centos.md)
      + [armazenado em cache no Ubuntu](storage/memcache-ubuntu.md)
   + Dividir Banco de Dados {#split-db}
      + [Visão geral da divisão do banco de dados](storage/multi-master.md)
      + [Configuração automática](storage/multi-master-masterdb.md)
      + [Configuração manual](storage/multi-master-manual.md)
      + [Verificar banco de dados dividido](storage/multi-master-verify.md)
      + [Replicação de banco de dados](storage/multi-master-replication.md)
      + [Reverter para banco de dados único](storage/revert-split-database.md)
