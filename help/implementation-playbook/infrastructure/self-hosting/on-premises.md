---
title: Infraestrutura local
description: Saiba mais sobre a infraestrutura local do Adobe Commerce e serviços em nuvem de terceiros.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Infraestrutura local do Adobe Commerce

As motivações para iniciar uma nova implementação do Adobe Commerce ou mover uma implementação existente do Adobe Commerce no local para a nuvem são numerosas, mas os fatores estratégicos mais comuns são reduzir as despesas de capital, diminuir os custos contínuos, melhorar a escalabilidade e a elasticidade, melhorar o tempo de entrada no mercado e obter melhorias na segurança e na conformidade.

O diagrama a seguir mostra a arquitetura de referência para implantar o Adobe Commerce no local na infraestrutura do AWS. Outros provedores de nuvem, como Azure, Google Cloud e Alibaba Cloud, compartilham um design de infraestrutura semelhante e serviços homólogos.

![Diagrama mostrando a infraestrutura do Adobe Commerce de auto-hospedagem em serviços de nuvem de terceiros](/help/assets/playbooks/on-premises-infrastructure.svg)

Vamos nos aprofundar nas funções de cada aspecto da infraestrutura mostrada acima:

1. O Amazon Route 53 fornece a configuração de DNS.

1. O AWS WAF é um firewall de aplicativo da Web que protege o Adobe Commerce contra explorações comuns da Web.

1. O Amazon CloudFront é uma rede de entrega rápida de conteúdo (CDN) que acelera a distribuição de conteúdo estático e dinâmico da Web.

1. O primeiro balanceador de carga de aplicativo de Balanceamento de carga Elástico distribui o tráfego entre instâncias de Verniz em um grupo de Dimensionamento automático do AWS em várias Zonas de Disponibilidade.

1. O Cache de verniz é um acelerador de aplicativo web que armazena em cache proxy reverso HTTP. A versão corporativa, disponível no AWS Marketplace, é recomendada porque tem melhores recursos para dar suporte a back-ends em nuvem e à limpeza de cache em hosts dinâmicos.

1. O segundo balanceador de carga de aplicativo do Balanceamento de carga Elástico distribui o tráfego do Cache de Verniz pelo grupo Escalonamento automático do AWS de instâncias do Adobe Commerce em várias Zonas de Disponibilidade.

1. Instale a versão mais recente do Adobe Commerce em instâncias do Amazon EC2. A instalação consiste no aplicativo Adobe Commerce, servidor Web Nginx e PHP. Crie a Amazon Machine Image (AMI) para iniciar novas instâncias em um grupo de Dimensionamento automático.

1. O Amazon Elasticsearch Service é um serviço de Elasticsearch gerenciado para pesquisa de catálogo do Adobe Commerce.

1. O Amazon ElastiCache for Redis fornece uma camada de cache para o banco de dados.

1. Use o Amazon Aurora ou AmazonRDS para simplificar a administração do banco de dados (incluindo alta disponibilidade e configuração multimestre).

1. O EFSMount Target facilita o mapeamento do Amazon Elastic File System (AmazonEFS) para instâncias de Verniz e Adobe Commerce.

1. Use o Amazon EFS para acessar a configuração compartilhada em ativos de mídia verniz e compartilhado em instâncias do Adobe Commerce.

## Serviços em nuvem

Além de fornecer uma plataforma de tecnologia de suporte para a ativação de processos DevOps no AWS em torno de seu ambiente Adobe Commerce, a AWS fornece uma coleção de serviços que podem fornecer (na ausência de) ou aumentar suas soluções existentes de gerenciamento de configuração de software (SCM). Isso inclui AWSCodeCommit, AWSCodeBuild, AWSCodePipeline e AWSCodeDeploy, que permitem um controle de origem gerenciado, build, integração/implantação contínua (CI/CD) e serviços de implantação.

## Migração para a nuvem

A proposta de valor para migrar o Adobe Commerce para o AWS é aprimorada ainda mais pela disponibilidade de vários serviços que fornecem insight operacional e agilidade. O que queremos dizer é uma visão operacional da plataforma não apenas de uma perspectiva técnica (por exemplo, solicitações por hora), mas também de uma perspectiva operacional de negócios (por exemplo, pedidos por hora), especialmente quando os dois conjuntos de dados podem ser casados. Isso fornece uma análise quase em tempo real do desempenho da campanha, dos custos de operações da plataforma e de um número quase infinito de outros indicadores.

A configuração do Adobe Commerce para o AWS pode substituir dependências específicas do aplicativo por alternativas totalmente gerenciadas disponíveis na nuvem. Por exemplo, em vez de hospedar diretamente um banco de dados relacional em instâncias EC2, o banco de dados de muitos aplicativos pode ser facilmente substituído pelo Amazon Relational Database Service (AmazonRDS). O benefício dessa estratégia é que a responsabilidade operacional de componentes não diferenciados pode ser transferida para a AWS sem exigir alterações significativas no aplicativo principal.

Há várias opções de implantação disponíveis para executar o Adobe Commerce no AWS. A escolha mais apropriada depende de suas necessidades de custo, escala, disponibilidade e flexibilidade, bem como das habilidades de AWS e Adobe Commerce de sua organização.

{{$include /help/_includes/hosting-related-links.md}}
