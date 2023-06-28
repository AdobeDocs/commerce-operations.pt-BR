---
title: Visão geral da infraestrutura em nuvem
description: Saiba mais sobre o Adobe Commerce na infraestrutura em nuvem.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Visão geral

Uma das opções mais populares de hospedagem gerenciada para o Adobe Commerce no AWS é oferecida pela própria Adobe Commerce. A infraestrutura do Adobe Commerce na nuvem é uma plataforma de hospedagem automatizada totalmente gerenciada para o software Adobe Commerce.

A infraestrutura do Adobe Commerce na nuvem é uma oferta de plataforma como um serviço (PaaS) que permite a implantação rápida de vitrines da Web totalmente personalizáveis, seguras e escaláveis, combinadas com uma infraestrutura líder em hospedagem e serviços gerenciados. Ela oferece dois planos com infraestruturas diferentes. O Adobe Commerce Starter é mais adequado para lojas menores com menos complexidade e catálogos menores. O Adobe Commerce Pro foi criado para lojas maiores com mais complexidade, catálogos de produtos maiores ou tráfego que atinge o pico. A Adobe Commerce determinará a arquitetura apropriada com a entrada de parceiros.

O Adobe Commerce está pronto para nuvem com uma infraestrutura de hospedagem em várias nuvens totalmente redundante que oferece desempenho otimizado, resiliência e escalabilidade elástica. Você pode executar com eficiência sua plataforma de comércio na rede de entrega de conteúdo (CDN) do Fastly e, com o New Relic para monitoramento e gerenciamento, você pode manter seu ambiente de loja funcionando sem problemas.

A Adobe Commerce oferece todos os benefícios da computação em nuvem moderna que são mais comumente associados às soluções SaaS: escalabilidade elástica, alta resiliência e disponibilidade, conformidade com o PCI, disponibilidade global e aplicação de patches automatizada, mantendo ainda a flexibilidade na personalização de software exigida por nossos comerciantes.

![Diagrama que mostra os elementos de arquitetura do Adobe Commerce na infraestrutura em nuvem](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Benefícios

Outros benefícios da Adobe Commerce incluem:

- **Otimizado para o Adobe Commerce**. Os scripts de criação desenvolvidos pela Adobe Commerce e a configuração de serviço garantem que cada instância seja ajustada e configurada corretamente para obter o desempenho ideal do comerciante.

- **Versões consistentes e seguras**. Todas as implantações de código são baseadas em Git para consistência e repetibilidade, com ambientes de produção somente leitura para segurança avançada.

- **Flexibilidade para parceiros**. Uma API REST completa e uma interface de linha de comando com script garantem a facilidade de integração com sistemas externos e a compatibilidade com os workflows de gerenciamento de código existentes.

- **Conjunto de ferramentas de implantação flexível**. Acelere, mescle, clone e elimine rapidamente ambientes ilimitados à vontade para tarefas de desenvolvimento, testes de controle de qualidade ou diagnósticos de problemas de produção.

- **Entrega em nuvem contínua**. Mude com confiança diretamente do desenvolvimento para o UAT e produção, de maneira contínua em todas as ramificações de código e equipes de desenvolvimento.

## Serviços de terceiros

Vamos também analisar o software que torna os benefícios da Adobe Commerce uma realidade.

![Diagrama que mostra o Adobe Commerce na pilha de tecnologia de infraestrutura em nuvem](../../../assets/playbooks/cloud-tech-stack.svg)

- CDN do Fastly: À medida que os clientes acessam seu site e armazenam, as solicitações acessam o Fastly para carregar as páginas em cache mais rapidamente. O Fastly WAF também fornece serviço de proteção de DDoS.

- O New Relic oferece uma visão completa de seus aplicativos e ambiente operacional. Ele permite combinar métricas principais de aplicativos móveis e de navegadores com serviços de suporte, armazenamentos de dados e hosts para que você possa otimizar o desempenho de forma holística e garantir o sucesso de cada iniciativa.

- O Composer gerencia dependências e atualizações no Adobe Commerce e fornece contexto sobre os pacotes incluídos, o que os pacotes fazem e como eles se encaixam.

- Git é o código nos repositórios. Ele permite ramificação local, áreas de preparo convenientes e vários fluxos de trabalho com criação e implantação automáticas para desenvolvimento rápido e implantação contínua.

- A Platform-as-a-Service (PaaS) fornece uma infraestrutura pré-provisionada que inclui PHP, MySQL, Redis, [!DNL RabbitMQ]e OpenSearch ou Elasticsearch.

- A hospedagem em nuvem do AWS ou Azure capacita o Infrastructure-as-a-Service (IaaS) subjacente, que oferece um ambiente escalável e seguro para vendas e varejo online.
