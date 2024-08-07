---
user-guide-title: Manual de implementação
user-guide-description: Saiba mais sobre as estratégias de planejamento e implementação de um site bem-sucedido do Adobe Commerce.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# Manual de implementação {#implementation-playbook}

- [Visão geral](overview.md)
- Commerce {#intro}
   - [Sobre o Adobe Commerce](intro/about-commerce.md)
   - [Princípios do desenvolvimento de plataformas](intro/platform-development.md)
- Escopo do projeto {#project-scope}
   - [Conhecimento é poder](project-scope/knowledge.md)
   - [Principais partes interessadas](project-scope/key-stakeholders.md)
   - [Processo e linha do tempo](project-scope/process-timeline.md)
   - [Entregáveis](project-scope/deliverables.md)
   - [Listas de verificação de requisitos](project-scope/requirement-checklists.md)
- Desenvolvimento {#development}
   - [Ferramentas da plataforma](development/platform-tools.md)
   - [Ferramentas de gerenciamento de projetos](development/project-management-tools.md)
   - [Metodologia de implementação do projeto](development/delivery.md)
   - [Controle de qualidade](development/quality-control.md)
- Planejamento e governança {#planning}
   - [Abordagem de entrega e planejamento](planning/delivery.md)
   - [Responsabilidade e propriedade](planning/ownership.md)
   - [Governança do projeto](planning/governance.md)
- Arquitetura e integrações {#architecture}
   - [Referência empresarial](architecture/enterprise-blueprint.md)
   - Arquitetura de referência global {#global-reference-architecture}
      - [Visão geral](architecture/global-reference/overview.md)
      - [Exemplos](architecture/global-reference/examples.md)
      - Desenvolvimento do compositor {#composer}
         - [Visão geral](architecture/global-reference/composer/overview.md)
         - [Estrutura de projeto](architecture/global-reference/composer/project-structure.md)
         - [Dicas e truques](architecture/global-reference/composer/tips-and-tricks.md)
- Infraestrutura e implantação {#infrastructure}
   - [Visão geral](infrastructure/overview.md)
   - Auto-hospedagem {#self-hosting}
      - [Visão geral](infrastructure/self-hosting/overview.md)
      - [Infraestrutura local](infrastructure/self-hosting/on-premises.md)
      - [Conceitos de segurança](infrastructure/self-hosting/security-concepts.md)
      - [Monitoramento de telemetria e ferramentas](infrastructure/self-hosting/monitoring-tools.md)
      - [Ideias de recuperação de desastres](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Dicas de desempenho](infrastructure/self-hosting/performance-tips.md)
   - Infraestrutura em nuvem {#cloud}
      - [Visão geral](infrastructure/cloud/overview.md)
      - [Regiões](infrastructure/cloud/regions.md)
      - [Tecnologias](infrastructure/cloud/technology.md)
      - [Segurança e conformidade](infrastructure/cloud/security.md)
   - Otimização de desempenho {#performance}
      - [Problemas típicos](infrastructure/performance/optimization.md)
      - [Referenciais](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Prontidão para inicialização {#launch}
   - [Visão geral](launch/overview.md)
   - [Etapas de pré-lançamento](launch/pre-launch-steps.md)
   - [Etapas de inicialização](launch/launch-steps.md)
   - [Etapas de inicialização do Post](launch/post-launch-steps.md)
- Manutenção e suporte {#maintenance}
   - [Visão geral](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Práticas recomendadas {#best-practices}
   - [Visão geral](best-practices/phases.md)
   - Planejando {#planning}
      - [Visão geral](best-practices/planning/overview.md)
      - [Gerenciamento de catálogo](best-practices/planning/catalog-management.md)
      - [Configuração de exibição de sites, lojas e lojas](best-practices/planning/sites-stores-store-views.md)
      - [Configuração de relatórios](best-practices/planning/reporting-configuration.md)
      - [Configuração do banco de dados para implantações em nuvem&#x200B;](best-practices/planning/database-on-cloud.md)
      - [Configuração do MySQL](best-practices/planning/mysql-configuration.md)
      - [Configuração do serviço Redis](best-practices/planning/redis-service-configuration.md)
      - [Tamanho da memória do OPcache](best-practices/planning/opcache-memory-size.md)
      - [Tamanho do cache do Realpath](best-practices/planning/realpath-cache-size.md)
      - [Extensões](best-practices/planning/extensions.md)
      - [Escalonamentos de parceiros](best-practices/planning/partner-escalation.md)
      - [Processamento de armazenamento de pagamentos](best-practices/planning/payment-processing-storage.md)
   - Desenvolvimento {#development}
      - [Visão geral](best-practices/development/overview.md)
      - [Práticas recomendadas gerais](best-practices/development/general.md)
      - [Gerenciamento de código](best-practices/development/code-management.md)
      - [Revisão do código](best-practices/development/code-review.md)
      - [Depuração](best-practices/development/debugging.md)
      - [Tratamento de exceções](best-practices/development/exception-handling.md)
      - [Ramificação Git](best-practices/development/git-branching.md)
      - [Redimensionamento da imagem do catálogo](best-practices/development/catalog-image-resizing.md)
      - [Otimização de imagem](best-practices/development/image-optimization.md)
      - [Solução de problemas](best-practices/development/troubleshooting.md)
      - [Otimizar arquivos CSS e JS](best-practices/development/optimize-css-js-files.md)
      - [Blocos de conteúdo privado](best-practices/development/private-content-block-configuration.md)
      - [Implantação de conteúdo estático](best-practices/development/static-content-deployment.md)
      - [Modificação de tabelas de banco de dados](best-practices/development/modifying-core-and-third-party-tables.md)
      - [Modificando código principal e de terceiros](best-practices/development/modifying-core-and-third-party-code.md)
   - Iniciar {#launch}
      - [Visão geral](best-practices/launch/overview.md)
      - [Configurar rastreadores da Web](best-practices/launch/robots-txt.md)
      - [Proteger seu site e sua infraestrutura](best-practices/launch/security-best-practices.md)
   - Manutenção {#maintenance}
      - [Visão geral](best-practices/maintenance/overview.md)
      - [Auditoria de desempenho de front-end](best-practices/maintenance/frontend-performance.md)
      - [Otimizar o desempenho de back-end](best-practices/maintenance/backend-performance.md)
      - [Configuração do indexador](best-practices/maintenance/indexer-configuration.md)
      - [Patches em escala](best-practices/maintenance/patching-at-scale.md)
      - [Processamento do pedido](best-practices/maintenance/order-processing-configuration.md)
      - [Resolver problemas de desempenho do banco de dados](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Responder a incidentes de segurança](best-practices/maintenance/respond-to-security-incident.md)
      - [Agendando atualizações de administrador em sites de produção](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Serviços de atualização](best-practices/maintenance/update-services.md)
      - [Lista de verificação de atualização](best-practices/maintenance/upgrade-checklist.md)
      - [Pré-requisitos de atualização para o MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [Retornar aos Guias Operacionais](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
