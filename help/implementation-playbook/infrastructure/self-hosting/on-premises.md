---
title: Infraestrutura no local
description: Saiba mais sobre a infraestrutura local da Adobe Commerce e serviços em nuvem de terceiros.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Infraestrutura no local da Adobe Commerce

As motivações para iniciar uma nova implementação do Adobe Commerce ou mover uma implementação existente do Adobe Commerce no local para a nuvem são numerosas, mas os fatores estratégicos mais comuns são a redução dos gastos de capital, a diminuição dos custos contínuos, a melhoria da escalabilidade e da elasticidade, a melhoria do tempo de comercialização e a obtenção de melhorias na segurança e conformidade.

O diagrama a seguir mostra a arquitetura de referência para implantar o Adobe Commerce no local na infraestrutura AWS. Outros provedores de nuvem como o Azure, a Google Cloud e a Alibaba Cloud compartilham um design de infraestrutura semelhante e serviços homólogos.

![Diagrama que mostra a infraestrutura da Adobe Commerce de auto-hospedagem em serviços em nuvem de terceiros](/help/assets/playbooks/on-premises-infrastructure.svg)

Vamos aprofundar as funções e funções de cada aspecto da infraestrutura mostrado acima:

1. O Amazon Route 53 fornece configuração de DNS.

1. O AWS WAF é um firewall de aplicativo Web que protege o Adobe Commerce contra explorações comuns da Web.

1. O Amazon CloudFront é uma rede de entrega de conteúdo (CDN) rápida que acelera a distribuição de conteúdo estático e dinâmico da Web.

1. O primeiro balanceador de carga elástico distribui tráfego entre instâncias variadas em um grupo de dimensionamento automático da AWS em várias zonas de disponibilidade.

1. O Cache Varnish é um proxy reverso HTTP do acelerador de aplicação Web que armazena em cache. A versão corporativa, disponível no AWS Marketplace, é recomendada, pois tem melhores recursos para oferecer suporte a back-ends em nuvem e à limpeza de cache em hosts dinâmicos.

1. O segundo balanceador de carga elástico distribui o tráfego do cache varnish no grupo de dimensionamento automático da AWS de instâncias do Adobe Commerce em várias zonas de disponibilidade.

1. Instale a versão mais recente do Magento Open Source ou Adobe Commerce em instâncias do Amazon EC2. A instalação consiste no aplicativo Adobe Commerce, no servidor Web Nginx e no PHP. Crie a AMI (Amazon Machine Image) para iniciar novas instâncias em um grupo de Dimensionamento automático.

1. O Amazon Elasticsearch Service é um serviço de Elasticsearch gerenciado para pesquisa de catálogo do Adobe Commerce.

1. O Amazon ElastiCache para Redis fornece uma camada de armazenamento em cache para banco de dados.

1. Use o Amazon Aurora ou o AmazonRDS para simplificar a administração do banco de dados (incluindo alta disponibilidade e configuração multiprincipal).

1. O EFSMount Target facilita o mapeamento do Sistema de Arquivos Elástico do Amazon (AmazonEFS) para instâncias Varnish e Adobe Commerce.

1. Use o Amazon EFS para acessar a configuração compartilhada em ativos de mídia variados e compartilhados em instâncias do Adobe Commerce.

## Serviços em nuvem

Além de fornecer uma plataforma de tecnologia de suporte para ativar os processos DevOps no AWS em seu ambiente Adobe Commerce, a AWS fornece uma coleção de serviços que podem fornecer (na ausência de) ou aumentar suas soluções de gerenciamento de configuração de software (SCM) existentes. Isso inclui AWSCodeCommit, AWSCodeBuild, AWSCodePipeline e AWSCodeDeploy, o que permite um controle de origem gerenciado, criação, integração contínua/implantação contínua (CI/CD) e serviços de implantação.

## Migração para nuvem

A proposta de valor para migrar o Adobe Commerce para o AWS é aprimorada ainda mais pela disponibilidade de vários serviços que fornecem insight operacional e agilidade. O que queremos dizer é insight operacional na plataforma não apenas de uma perspectiva técnica (por exemplo, solicitações por hora), mas também de uma perspectiva operacional de negócios (por exemplo, pedidos por hora), especialmente quando os dois conjuntos de dados podem ser casados. Isso fornece uma visão em tempo quase real do desempenho da campanha, custos de operações da plataforma e um número quase infinito de outros indicadores.

A configuração do Adobe Commerce para o AWS pode substituir dependências de aplicativos específicas por alternativas totalmente gerenciadas disponíveis na nuvem. Por exemplo, em vez de hospedar diretamente um banco de dados relacional em instâncias do EC2, o banco de dados para muitos aplicativos pode ser facilmente substituído pelo Amazon Relational Database Service (AmazonRDS). A vantagem dessa estratégia é que a responsabilidade operacional dos componentes indiferenciados pode ser transferida para a AWS sem exigir alterações significativas no aplicativo principal.

Há várias opções de implantação disponíveis para executar o Adobe Commerce (versões Magento Open Source e Adobe Commerce) no AWS. A escolha mais adequada depende de seus requisitos de custo, escala, disponibilidade e flexibilidade, bem como das habilidades da AWS e Adobe Commerce de sua organização.

{{$include /help/_includes/hosting-related-links.md}}
