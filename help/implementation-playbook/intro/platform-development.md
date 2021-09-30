---
title: Princípios do desenvolvimento de plataformas
description: Entenda os princípios fundamentais de desenvolvimento da plataforma ao trabalhar com o Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Princípios do desenvolvimento da plataforma

Neste playbook, aprofundamos alguns dos principais padrões de desenvolvimento do Adobe Commerce, incluindo:

- Âmbito funcional e técnico em conformidade com o processo de desenvolvimento
- Práticas recomendadas de desenvolvimento alinhando com a arquitetura MVC
- Considerações arquitetônicas, incluindo o GRA
- Padrões de segurança contra script e exploração
- Práticas recomendadas de desenvolvimento de extensão
- Integrações de API da Web com REST, SOAP e GraphQL
- Melhorias de desempenho para codificação e infraestrutura
- Ferramentas, estratégias e metodologias de teste

Embora alguns implementadores de solução possam ter suas próprias preferências quando se trata das metodologias, processos e ferramentas usadas em um projeto de implementação, este manual se concentra nas práticas recomendadas e metodologias geralmente aceitas que podem ser compartilhadas na maioria das implementações.

Como qualquer grande projeto de TI, o Adobe Commerce baseia-se em padrões de codificação que aproveitam as práticas recomendadas e padronizações das tecnologias subjacentes (por exemplo, PHP/Zend,Symfony, JavaScript, jQuery e HTML), bem como padrões que foram estabelecidos no Adobe Commerce Coding Standard. Seguir essas normas é absolutamente necessário para eliminar erros e melhorar a qualidade e a manutenção do código personalizado.

## Comércio do Adobe na infraestrutura de nuvem

O Adobe Commerce on cloud Infrastructure é uma plataforma de hospedagem automatizada e gerenciada para o software Adobe Commerce. O Adobe Commerce on cloud Infrastructure vem com uma variedade de recursos adicionais que o diferenciam das implementações de Adobe e Magento Open Source:

![Informações sobre componentes do Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

O Adobe Commerce on cloud Infrastructure fornece uma infraestrutura pré-provisionada que inclui as tecnologias PHP, MySQL, Redis, RabbitMQ e Elasticsearch; um fluxo de trabalho baseado em Git com operações automáticas de criação e implantação para um desenvolvimento rápido e uma implantação contínua eficientes sempre que as alterações no código forem enviadas para um ambiente do Platform as a Service (PaaS); arquivos e ferramentas altamente personalizáveis de configuração do ambiente; e hospedagem AWS que oferece um ambiente escalável e seguro para vendas e varejo online.

![Informações sobre componentes do Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
