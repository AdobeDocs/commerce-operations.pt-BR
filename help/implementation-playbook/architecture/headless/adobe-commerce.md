---
title: Arquitetura Adobe Commerce sem periféricos
description: Saiba mais sobre o que torna a arquitetura sem periféricos do Adobe Commerce exclusiva.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Arquitetura Adobe Commerce sem periféricos

O benefício da arquitetura da Adobe Commerce é que ela não é uma proposta de tudo ou nada e um comerciante pode encontrar a combinação correta de soluções para seus negócios. Eles podem criar um PWA com PWA Studio para sua experiência principal no site ou usar o Adobe Experience Manager como camada em jornadas complexas do cliente, enquanto criam uma interface personalizada para experimentar novos pontos de contato. Nenhuma outra plataforma pode igualar o tempo para os benefícios do mercado e a flexibilidade que a Adobe Commerce oferece com sua arquitetura sem periféricos.

![Diagrama mostrando uma arquitetura de vitrine do Adobe Commerce sem periféricos](../../../assets/playbooks/headless-storefront-architecture.svg)

Cada abordagem não é mutuamente exclusiva. Os clientes podem criar sua própria interface (cabeçalho), usar o PWA Studio para experiências Web/móveis e/ou usar o Adobe Experience Manager para o vidro (em uma implantação completa ou híbrida).

A Adobe Commerce sempre permitiu implantações sem periféricos com APIs REST. Embora o REST seja poderoso, especialmente para processamento em massa, quando se trata de APIs GraphQL sem interface, permite um desenvolvimento mais rápido por meio de uma experiência intuitiva de desenvolvedor, maior flexibilidade permitindo alterações que não afetam as APIs existentes e melhor desempenho, minimizando a quantidade de dados recuperados somente para o que é necessário.

GraphQL é um padrão do setor para APIs de desempenho, que é usado por muitas das principais plataformas de comércio eletrônico. Isso é bom, já que isso significa que é uma solução comprovada e conhecimento existe no mercado.

Embora a Adobe Commerce tenha uma loja acoplada como uma opção, não é necessário de forma alguma que um comerciante use essa interface herdada do Adobe Commerce. Um comerciante pode aproveitar os melhores serviços comerciais da Adobe Commerce para lidar com os processos de negócios de back-end e, usando nossas APIs de loja, integrar sua própria loja dissociada para impulsionar a experiência de front-end.

Agora, vamos dar uma olhada nas várias opções sem cabeça.

## PWA Studio

O primeiro é um aplicativo web progressivo criado com o PWA Studio. Parte disso é ativada pelo fato de um PWA ser uma vitrine sem cabeça dissociada do back-end comercial. Com o PWA Studio, os comerciantes podem criar PWA de alto desempenho, confiáveis e econômicas, além do Adobe Commerce, para oferecer as melhores experiências da Web, tanto em dispositivos móveis quanto em desktop. Com o passar do tempo, isso ultrapassará a loja acoplada como opção padrão.

A maioria dos comerciantes entende a direção que o setor está seguindo em relação aos PWA e muitos bloqueadores potenciais estão sendo removidos rapidamente.

Semana após semana, o número de parceiros que formam conhecimento no PWA Studio cresce e temos um número cada vez maior de lançamentos de clientes. A atualização mais recente da extensibilidade PWA Studio incluiu o que ajudará a fazer progressos significativos na compatibilidade com as extensões do Adobe Commerce Marketplace.

Muitos comerciantes podem sentir que não estão prontos para PWA e sem interface, pois exigem uma forte dependência dos desenvolvedores. Um dos grandes benefícios de ter tanto o aplicativo comercial quanto o chefe desenvolvidos pela Adobe Commerce é ajudar a garantir a compatibilidade entre os recursos de comércio.

Para tornar o PWA mais acessível e fácil de gerenciar para nossos comerciantes, capacitamos os usuários empresariais a gerenciar alterações de conteúdo do dia a dia, criar novas páginas de aterrissagem e mais usando o Page Builder. Esses dois recursos poderosos juntos permitem que a velocidade comercialize em todos os dispositivos e experiências.

## Adobe Experience Manager

Uma combinação poderosa para suas necessidades de gerenciamento de conteúdo e ativos digitais, a Adobe Experience Manager ajuda os comerciantes a obter experiências personalizadas e orientadas por conteúdo no mercado mais rapidamente, combinando o gerenciamento de ativos digitais com o poder do aprendizado de máquina, o conteúdo alimentado pela Adobe Sensei e o gerenciamento de jornadas do cliente.

O Adobe Commerce plus Adobe Experience Manager é uma história poderosa, na medida em que o mecanismo de comércio permite que as empresas habilitem o comércio por meio de interfaces de clientes que são acionadas pela Adobe Experience Manager.

## Cabeçalhos personalizados

A opção final para discutir aqui é a de construir uma frente personalizada. Essa opção é para empresas que possuem experiência e desenvolvedores internos qualificados em uma pilha de primeiro plano específica, como o React. Se eles não tiverem habilidades no desenvolvimento de primeiro plano tradicional da Adobe Commerce, poderão decidir que é mais econômico criar seu próprio front-end personalizado do React.

Naturalmente, esse modelo requer integração forte de clientes ou sistemas, além de habilidades e recursos de desenvolvimento de primeiro plano, e você não obtém o benefício da compatibilidade nativa com coisas como o Page Builder que você obtém com o PWA Studio. Sempre que um comerciante estiver criando algo totalmente personalizado, poderá perder tempo para comercializar.

Os front-ends personalizados também permitem inovações e experimentação. Fala-se muito de ARV/VR ou comércio de voz, e uma arquitetura como a da Adobe Commerce permite que os comerciantes explorem essas opções sem afetar suas lojas da Web existentes.
