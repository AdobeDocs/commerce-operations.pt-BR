---
title: Princípios do desenvolvimento de plataformas
description: Entenda os princípios fundamentais de desenvolvimento da plataforma ao trabalhar com o Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
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

Como qualquer grande projeto de TI, a Adobe Commerce baseia-se em padrões de codificação que utilizam práticas recomendadas e padronizações das tecnologias subjacentes (por exemplo, PHP/Zend, Symfony, JavaScript, jQuery e HTML), bem como padrões que foram estabelecidos no Adobe Commerce Coding Standard. Seguir essas normas é absolutamente necessário para eliminar erros e melhorar a qualidade e a manutenção do código personalizado.

## Adobe Commerce na infraestrutura de nuvem

A infraestrutura em nuvem Adobe Commerce é uma plataforma de hospedagem gerenciada e automatizada para o software Adobe Commerce. A infraestrutura em nuvem do Adobe Commerce vem com vários recursos adicionais que a diferenciam das implementações locais do Adobe Commerce e do Magento Open Source:

![Infográficos do componente Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

A infraestrutura em nuvem do Adobe Commerce fornece uma infraestrutura pré-provisionada que inclui PHP, MySQL, Redis, [!DNL RabbitMQ]e tecnologias Elasticsearch; um fluxo de trabalho baseado em Git com operações automáticas de criação e implantação para um desenvolvimento rápido e uma implantação contínua eficientes sempre que as alterações no código forem enviadas para um ambiente do Platform as a Service (PaaS); arquivos e ferramentas altamente personalizáveis de configuração do ambiente; e hospedagem da AWS que oferece um ambiente escalável e seguro para vendas e varejo online.

![Infográficos do componente Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
