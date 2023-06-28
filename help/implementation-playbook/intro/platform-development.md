---
title: Princípios do desenvolvimento de plataformas
description: Entenda os princípios fundamentais de desenvolvimento de plataformas ao trabalhar com o Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Princípios do desenvolvimento de plataformas

Neste manual, analisamos em detalhes alguns dos principais padrões de desenvolvimento do Adobe Commerce, incluindo:

- Âmbito funcional e técnico em conformidade com o processo de desenvolvimento
- Práticas recomendadas de desenvolvimento alinhadas à arquitetura MVC
- Considerações de arquitetura, incluindo GRA
- Padrões de segurança contra scripts e explorações
- Práticas recomendadas de desenvolvimento de extensão
- Integrações da API da Web com REST, SOAP e GraphQL
- Melhorias de desempenho para codificação e infraestrutura
- Ferramentas, estratégias e metodologias de teste

Embora alguns implementadores de soluções possam ter suas próprias preferências quando se trata de metodologias, processos e ferramentas usados em um projeto de implementação, este manual se concentra em práticas recomendadas e metodologias geralmente aceitas que podem ser compartilhadas na maioria das implementações.

Como qualquer projeto de TI grande, o Adobe Commerce é construído com base em padrões de codificação que aproveitam as práticas recomendadas e padronizações das tecnologias subjacentes (por exemplo, PHP/Zend, Symfony, JavaScript, jQuery e HTML), bem como padrões que foram estabelecidos no Adobe Commerce Coding Standard. Seguir esses padrões é uma necessidade absoluta para eliminar bugs e melhorar a qualidade e a capacidade de manutenção do código criado de forma personalizada.

## Adobe Commerce na infraestrutura em nuvem

A infraestrutura do Adobe Commerce na nuvem é uma plataforma de hospedagem gerenciada e automatizada para o software Adobe Commerce. A infraestrutura do Adobe Commerce na nuvem vem com uma variedade de recursos adicionais que a diferenciam das implementações locais do Adobe Commerce e do Magento Open Source:

![Infográficos de componentes do Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

O Adobe Commerce na infraestrutura em nuvem fornece uma infraestrutura pré-provisionada que inclui PHP, MySQL, Redis, [!DNL RabbitMQ]e Elasticsearch; um fluxo de trabalho baseado em Git com operações automáticas de criação e implantação para desenvolvimento rápido e implantação contínua eficientes sempre que as alterações de código forem enviadas para um ambiente de Plataforma como um Serviço (PaaS); arquivos e ferramentas de configuração de ambiente altamente personalizáveis; e hospedagem AWS que oferece um ambiente escalável e seguro para vendas e varejo online.

![Infográficos de componentes do Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
