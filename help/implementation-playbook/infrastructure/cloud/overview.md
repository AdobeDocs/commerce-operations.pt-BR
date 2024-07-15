---
title: Visão geral da infraestrutura em nuvem
description: Saiba mais sobre a Adobe Commerce na infraestrutura em nuvem.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Visão geral

Uma das opções mais populares de hospedagem gerenciada para o Adobe Commerce no AWS é oferecida pela própria Adobe Commerce. A infraestrutura do Adobe Commerce na nuvem é uma plataforma de hospedagem automatizada totalmente gerenciada para o software Adobe Commerce.

A infraestrutura do Adobe Commerce na nuvem é uma oferta de plataforma como serviço (PaaS) que permite a implantação rápida de vitrines da Web totalmente personalizáveis, seguras e escaláveis, combinadas com uma infraestrutura líder em hospedagem e Managed Services. Ela oferece dois planos com infraestruturas diferentes. Os planos do [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) do Adobe Commerce são mais adequados para lojas menores com menos complexidade e catálogos menores. Os planos do Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) foram projetados para lojas maiores com mais complexidade, catálogos de produtos maiores ou tráfego com pico. O Adobe determina a arquitetura apropriada com entrada de parceiros.

O Adobe Commerce está pronto para nuvem com uma infraestrutura de hospedagem em várias nuvens totalmente redundante que oferece desempenho otimizado, resiliência e escalabilidade elástica. Você pode executar com eficiência sua plataforma de comércio na rede de entrega de conteúdo (CDN) do Fastly e, com o New Relic para monitoramento e gerenciamento, você pode manter seu ambiente de loja funcionando sem problemas.

A Adobe Commerce oferece todos os benefícios da computação em nuvem moderna que são mais comumente associados às soluções SaaS, mantendo ainda a flexibilidade na personalização de software:

- Escalabilidade elástica
- Alta resiliência e disponibilidade
- Conformidade com o PCI
- Disponibilidade global e patches automatizados

![Diagrama mostrando os elementos de arquitetura do Adobe Commerce na infraestrutura de nuvem](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Benefícios

Outros benefícios da Adobe Commerce incluem:

- **Otimizado para Adobe Commerce**. Os scripts de criação desenvolvidos pela Adobe Commerce e a configuração de serviço garantem que cada instância seja ajustada e configurada corretamente para obter o melhor desempenho do comerciante.

- **Versões consistentes e seguras**. Todas as implantações de código são baseadas em Git para consistência e repetibilidade, com ambientes de produção somente leitura para segurança avançada.

- **Flexibilidade para parceiros**. Uma API REST completa e uma interface de linha de comando com script garantem a facilidade de integração com sistemas externos e a compatibilidade com os workflows de gerenciamento de código existentes.

- **Conjunto de ferramentas de implantação flexível**. Acelere, mescle, clone e elimine rapidamente ambientes ilimitados à vontade para tarefas de desenvolvimento, testes de controle de qualidade ou diagnósticos de problemas de produção.

- **Entrega em nuvem contínua**. Mude com confiança diretamente do desenvolvimento para o UAT e produção, de maneira contínua em todas as ramificações de código e equipes de desenvolvimento.

## Serviços de terceiros

Esta seção resume os principais serviços e ferramentas de terceiros para o Adobe Commerce em projetos de infraestrutura em nuvem. Consulte [Pilha de tecnologia](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) no _Guia da Nuvem_ para obter mais detalhes.

- **Fastly CDN**: à medida que os clientes acessam seu site e armazenam, as solicitações chegam ao Fastly para carregar as páginas em cache mais rapidamente. O Fastly WAF também fornece um serviço de proteção de DDoS.

- **New Relic**: fornece uma exibição completa dos aplicativos e do ambiente operacional. O New Relic permite combinar métricas principais de aplicativos móveis e de navegadores com serviços de suporte, armazenamentos de dados e hosts para que você possa otimizar o desempenho de forma holística e garantir o sucesso de cada iniciativa.

- **Composer**: gerencia dependências e atualizações no Adobe Commerce e fornece contexto sobre os pacotes incluídos, o que os pacotes fazem e como eles se encaixam.

- **Git**: fornece gerenciamento de código-fonte. O Git permite ramificação local, áreas de preparo convenientes e vários fluxos de trabalho com criação e implantação automáticas para desenvolvimento rápido e implantação contínua.

- **Platform-as-a-Service (PaaS)**: fornece uma infraestrutura pré-provisionada que inclui tecnologias PHP, MySQL, Redis, [!DNL RabbitMQ] e OpenSearch ou Elasticsearch.

- **Hospedagem de nuvem do AWS ou Azure**: capacita o IaaS (Infraestrutura como Serviço) subjacente, que oferece um ambiente escalável e seguro para vendas e varejo online.
