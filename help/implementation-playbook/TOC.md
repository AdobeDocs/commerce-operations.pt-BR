---
user-guide-title: Manual de implementação
user-guide-description: Saiba mais sobre as estratégias de planejamento e implementação de um site bem-sucedido do Adobe Commerce.
mini-toc-levels: 3
source-git-commit: 338a99f4f047640ac4bb944ac8599301cba5f646
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Manual de implementação {#implementation-playbook}

- [Visão geral](overview.md)
- Comércio {#intro}
   - [Sobre o Adobe Commerce](intro/about-commerce.md)
   - [Princípios do desenvolvimento da plataforma](intro/platform-development.md)
- Escopo do projeto {#project-scope}
   - [Conhecimento é poder](project-scope/knowledge.md)
   - [Principais partes interessadas](project-scope/key-stakeholders.md)
   - [Processo e linha do tempo](project-scope/process-timeline.md)
   - [Deliverables](project-scope/deliverables.md)
   - [Listas de verificação de requisitos](project-scope/requirement-checklists.md)
- Desenvolvimento {#development}
   - [Ferramentas da plataforma](development/platform-tools.md)
   - [Ferramentas de gestão de projetos](development/project-management-tools.md)
   - [Metodologia de execução do projeto](development/delivery.md)
   - [Controle de qualidade](development/quality-control.md)
- Planejamento e governança {#planning}
   - [Abordagem de delivery e planejamento](planning/delivery.md)
   - [Responsabilidade e propriedade](planning/ownership.md)
   - [Governança de projetos](planning/governance.md)
- Arquitetura e integrações {#architecture}
   - [Capacidades](architecture/capabilities.md)
   - [Estratégia de integração](architecture/integration-strategy.md)
   - [Estratégia de extensibilidade](architecture/extensibility-strategy.md)
   - [Opções de integração](architecture/integration-options.md)
   - [Arquitetura de referência global](architecture/global-reference.md)
   - Comércio livre {#headless}
      - [Benefícios](architecture/headless/benefits.md)
      - [Jornada sem cabeça](architecture/headless/journey-to-headless.md)
      - [Microsserviços](architecture/headless/microservices.md)
      - [Evolução da situação sem cabeça](architecture/headless/evolution.md)
      - [Arquitetura de vitrine combinada](architecture/headless/legacy-storefront.md)
      - [Arquitetura headless](architecture/headless/adobe-commerce.md)
- Infraestrutura e implantação {#infrastructure}
   - [Visão geral](infrastructure/overview.md)
   - [Infraestrutura no local](infrastructure/on-premises.md)
   - Infraestrutura em nuvem {#cloud}
      - [Visão geral](infrastructure/cloud/overview.md)
      - [Regiões](infrastructure/cloud/regions.md)
      - [Tecnologias](infrastructure/cloud/technology.md)
      - [Ambientes](infrastructure/cloud/environments.md)
      - [Serviços gerenciados](infrastructure/cloud/managed-services.md)
      - [Segurança e conformidade](infrastructure/cloud/security.md)
   - Otimização de desempenho {#performance}
      - [Problemas típicos](infrastructure/performance/optimization.md)
      - [Referenciais](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Disponibilidade do Launch {#launch}
   - [Visão geral](launch/overview.md)
   - [Etapas de pré-lançamento](launch/pre-launch-steps.md)
   - [Etapas do Launch](launch/launch-steps.md)
   - [Etapas pós-lançamento](launch/post-launch-steps.md)
- Manutenção e suporte {#maintenance}
   - [Visão geral](maintenance/overview.md)
   - [Serviços gerenciados da Adobe](maintenance/adobe-managed-services.md)
- Práticas recomendadas {#best-practices}
   - [Visão geral](best-practices/phases.md)
   - Planejamento {#planning}
      - [Visão geral](best-practices/planning/overview.md)
      - [Configuração de sites, lojas e visualizações de loja](best-practices/planning/sites-stores-store-views.md)
      - [Configuração de relatórios](best-practices/planning/reporting-configuration.md)
      - [Configuração do banco de dados para implantações em nuvem &#x200B;](best-practices/planning/database-on-cloud.md)
      - [&#x200B; de configuração da conexão subordinada MySQL](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [Uso de acionadores MySQL](best-practices/planning/mysql-triggers-usage.md)
      - [Configuração do serviço Redis](best-practices/planning/redis-service-configuration.md)
      - [Tamanho da memória do OPcache](best-practices/planning/opcache-memory-size.md)
      - [Tamanho do cache do Realpath](best-practices/planning/realpath-cache-size.md)
      - [Categorias](best-practices/planning/category-limits.md)
      - [Produto](best-practices/planning/product-sku-limits.md)
      - [Alterações do produto](best-practices/planning/product-variations.md)
      - [Opções de produto](best-practices/planning/product-options.md)
      - [Atributos do produto](best-practices/planning/product-attributes-and-options.md)
      - [Paginação da listagem de produtos](best-practices/planning/product-listing-pagination.md)
      - [Limite do carrinho do produto](best-practices/planning/product-cart.md)
      - [Promoções](best-practices/planning/product-cart-promotions.md)
      - [Extensões](best-practices/planning/extensions.md)
      - [Escalonamentos de parceiros](best-practices/planning/partner-escalation.md)
      - [Processamento de armazenamento de pagamentos](best-practices/planning/payment-processing-storage.md)
   - Desenvolvimento {#development}
      - [Visão geral](best-practices/development/overview.md)
      - [Otimização de imagem](best-practices/development/image-optimization.md)
      - [Solução de problemas](best-practices/development/troubleshooting.md)
      - [Otimizar arquivos CSS e JS](best-practices/development/optimize-css-js-files.md)
      - [Blocos de conteúdo privado](best-practices/development/private-content-block-configuration.md)
      - [Implantação de conteúdo estático](best-practices/development/static-content-deployment.md)
      - [Modificação de tabelas de banco de dados](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [Visão geral](best-practices/launch/overview.md)
      - [Serviço de Notificação de Segurança do Adobe](best-practices/launch/security-notification-service.md)
      - [Configurar o arquivo robots.txt](best-practices/launch/robots-txt.md)
      - [Evitar e responder a incidentes de segurança](best-practices/launch/prevent-respond-security-incident.md)
   - Manutenção {#maintenance}
      - [Visão geral](best-practices/maintenance/overview.md)
      - [Auditar o desempenho da frente](best-practices/maintenance/frontend-performance.md)
      - [Configuração do indexador](best-practices/maintenance/indexer-configuration.md)
      - [Processamento de pedidos](best-practices/maintenance/order-processing-configuration.md)
      - [Agendamento de atualizações do Administrador em sites de produção](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Serviços de atualização](best-practices/maintenance/update-services.md)
      - [Atualizar lista de verificação](best-practices/maintenance/upgrade-checklist.md)
      - [Resolver problemas de desempenho do banco de dados &#x200B;](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Pré-requisitos de atualização do Adobe Commerce 2.3.5 para o &#x200B; do MariaDB](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Retornar aos Guias Operacionais](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
