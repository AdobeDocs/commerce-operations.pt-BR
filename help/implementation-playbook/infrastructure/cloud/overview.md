---
title: Visão geral da infraestrutura na nuvem
description: Saiba mais sobre o Adobe Commerce na infraestrutura de nuvem.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Visão geral

Uma das opções mais populares de hospedagem gerenciada para o Adobe Commerce no AWS é oferecida pela própria Adobe Commerce. A infraestrutura em nuvem Adobe Commerce é uma plataforma de hospedagem totalmente gerenciada e automatizada para o software Adobe Commerce.

A infraestrutura em nuvem Adobe Commerce é uma oferta de plataforma como serviço (PaaS) que permite a implantação rápida de vitrines da Web totalmente personalizáveis, seguras e escaláveis, combinadas com uma infraestrutura líder em hospedagem e serviços gerenciados. Oferece dois planos com infraestruturas diferentes. O Adobe Commerce Starter é mais adequado para lojas menores com menos complexidade e catálogos menores. O Adobe Commerce Pro foi criado para grandes lojas com mais complexidade, catálogos de produtos maiores ou tráfego que atinge o pico. A Adobe Commerce determinará a arquitetura apropriada com a entrada dos parceiros.

A Adobe Commerce está pronta para nuvem com uma infraestrutura de hospedagem em nuvem totalmente redundante que oferece desempenho otimizado, resiliência e escalabilidade elástica. Você pode executar com eficiência sua plataforma de comércio na Rede de entrega de conteúdo (CDN) da Fastly e, com o New Relic para monitoramento e gerenciamento, pode manter o ambiente da loja funcionando sem problemas.

A Adobe Commerce oferece todos os benefícios da computação em nuvem moderna que são mais comumente associados às soluções de SaaS: escalabilidade elástica, alta resiliência e disponibilidade, conformidade com o PCI e disponibilidade global e correção automatizada, mantendo ao mesmo tempo a flexibilidade na personalização de software que nossos comerciantes exigem.

![Diagrama mostrando elementos arquitetônicos do Adobe Commerce na infraestrutura de nuvem](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Benefícios

Outros benefícios do Adobe Commerce incluem:

- **Otimizado para Adobe Commerce**. Os scripts de criação e a configuração de serviço desenvolvidos pela Adobe Commerce garantem que cada instância seja ajustada e configurada corretamente para obter o melhor desempenho do comerciante.

- **Versões consistentes e seguras**. Todas as implantações de código são baseadas em Git para garantir consistência e repetibilidade, com ambientes de produção somente leitura para garantir a segurança mais rígida.

- **Flexibilidade para os parceiros**. Uma API REST completa e uma interface de linha de comando com script garantem a facilidade de integração com sistemas externos e a compatibilidade com fluxos de trabalho de gerenciamento de código existentes.

- **Conjunto de ferramentas de implantação flexível**. Gire, mescle, clone e remova rapidamente ambientes ilimitados à vontade para tarefas de desenvolvimento, teste de controle de qualidade ou diagnóstico de problemas de produção.

- **Delivery contínuo de nuvem**. Mude com confiança do desenvolvimento para o UAT para a produção, de maneira contínua, em todas as ramificações de código e equipes de desenvolvimento.

## Serviços de terceiros

Vamos também analisar o software que torna os benefícios da Adobe Commerce uma realidade.

![Diagrama mostrando o Adobe Commerce na pilha de tecnologia de infraestrutura de nuvem](../../../assets/playbooks/cloud-tech-stack.svg)

- CDN rápido: À medida que os clientes acessam seu site e armazenam, as solicitações acessam com rapidez para carregar páginas em cache mais rápido. O WAF Fastly também fornece serviço de proteção de DDoS.

- O novo Relic oferece uma exibição completa de seus aplicativos e do ambiente operacional. Ele permite combinar métricas principais de aplicativos móveis e de navegadores com serviços de suporte, armazenamentos de dados e hosts para que você possa otimizar o desempenho de forma holística e garantir o sucesso de todas as iniciativas.

- O Composer gerencia dependências e atualizações no Adobe Commerce e fornece contexto sobre os pacotes incluídos, o que os pacotes fazem e como eles se encaixam.

- O Git é seu código em repositórios. Ele permite ramificações locais, áreas de preparo convenientes e vários fluxos de trabalho com criação e implantação automáticas para um desenvolvimento rápido e implantação contínua eficientes.

- A Platform-as-Service (PaaS) fornece uma infraestrutura pré-provisionada que inclui as tecnologias PHP, MySQL, Redis, RabbitMQ e Elasticsearch.

- A hospedagem em nuvem da AWS ou do Azure capacita a infraestrutura subjacente como um serviço (IaaS), que oferece um ambiente escalável e seguro para vendas e varejo online.
