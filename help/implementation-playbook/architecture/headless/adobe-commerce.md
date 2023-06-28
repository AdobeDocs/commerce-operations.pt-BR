---
title: Arquitetura headless do Adobe Commerce
description: Saiba mais sobre o que torna exclusiva a abordagem de arquitetura headless do Adobe Commerce.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Arquitetura headless do Adobe Commerce

A vantagem da arquitetura da Adobe Commerce é que ela não é uma proposta radical e um comerciante pode encontrar a combinação certa de soluções para seus negócios. Eles podem criar um PWA alimentado por PWA Studio para a experiência principal do site ou usar o Adobe Experience Manager como a camada em jornadas complexas do cliente, tudo isso enquanto criam um front-end personalizado para experimentar com novos pontos de contato. Nenhuma outra plataforma pode igualar os benefícios do tempo de entrada no mercado e a flexibilidade que a Adobe Commerce oferece com sua arquitetura headless.

![Diagrama mostrando uma arquitetura de vitrine do Adobe Commerce headless](../../../assets/playbooks/headless-storefront-architecture.svg)

Cada abordagem não é mutuamente exclusiva. Os clientes podem criar seu próprio front-end (head), usar o PWA Studio para experiências da Web/dispositivos móveis e/ou usar o Adobe Experience Manager para a loja (em uma implantação completa ou híbrida).

O Adobe Commerce sempre permitiu implantações headless com REST APIs. Embora o REST seja eficiente, especialmente para o processamento em massa, quando se trata de headless, as APIs do GraphQL permitem um desenvolvimento mais rápido por meio de uma experiência de desenvolvedor intuitiva, maior flexibilidade permitindo alterações que não afetam as APIs existentes e melhor desempenho, minimizando a quantidade de dados recuperados apenas para o que é necessário.

O GraphQL é um padrão do setor para APIs de alto desempenho, usado por muitas das principais plataformas de comércio eletrônico. Isso é bom, pois significa que é uma solução comprovada e que existe experiência no mercado.

Embora o Adobe Commerce tenha uma vitrine acoplada como opção, não é necessário que um comerciante use essa front-end herdada do Adobe Commerce. Um comerciante pode aproveitar os melhores serviços comerciais da Adobe Commerce para lidar com os processos de negócios de back-end e, usando nossas APIs de vitrine, integrar sua própria vitrine dissociada para impulsionar a experiência de front-end.

Agora, vejamos as várias opções headless.

## PWA Studio

O primeiro é um aplicativo web progressivo criado com o PWA Studio. Parte disso é possibilitado pelo fato de que um PWA é uma loja headless dissociada do back-end de comércio. Com o PWA Studio, os comerciantes podem criar PWA de alto desempenho, confiáveis e econômicos no Adobe Commerce para oferecer as melhores experiências da Web, tanto em dispositivos móveis quanto em desktops. Com o passar do tempo, a vitrine acoplada será ultrapassada como a opção padrão.

A maioria dos comerciantes entende a direção que a indústria está indo em direção no que diz respeito a PWA e muitos bloqueadores potenciais estão sendo removidos rapidamente.

Semana a semana, o número de parceiros que acumulam experiência no PWA Studio aumenta e temos um número cada vez maior de lançamentos de clientes. A atualização mais recente do PWA Studio incluiu a extensibilidade que ajudará a fazer um progresso significativo na compatibilidade com as extensões do Adobe Commerce Marketplace.

Muitos comerciantes podem sentir que não estão prontos para headless e PWA porque exigem muita confiança nos desenvolvedores. Um dos grandes benefícios de ter o aplicativo de comércio e o head desenvolvidos pela Adobe Commerce é que ele ajuda a garantir a compatibilidade entre os recursos de comércio.

Para tornar os PWA mais acessíveis e fáceis de gerenciar para nossos comerciantes, capacitamos os usuários empresariais a gerenciar alterações diárias de conteúdo, criar novas páginas de aterrissagem e muito mais usando o Page Builder. Juntos, esses dois poderosos recursos permitem agilizar o marketing de todos os dispositivos e experiências.

## Adobe Experience Manager

Combinação eficiente para suas necessidades de conteúdo e gerenciamento de ativos digitais, o Adobe Experience Manager ajuda os comerciantes a colocar experiências personalizadas e orientadas por conteúdo no mercado mais rapidamente, combinando o gerenciamento de ativos digitais com o poder do aprendizado de máquina, do conteúdo viabilizado pela Adobe Sensei e do gerenciamento de jornadas do cliente.

O Adobe Commerce mais o Adobe Experience Manager é uma história poderosa na qual o mecanismo de comércio permite que as empresas habilitem o comércio por meio de interfaces de clientes viabilizadas pelo Adobe Experience Manager.

## Cabeçalhos personalizados

A opção final a ser discutida aqui é a opção de criar um front-end personalizado. Essa opção é para empresas que têm experiência existente e desenvolvedores internos qualificados em uma pilha de front-end específica, como o React. Se eles não tiverem habilidades no desenvolvimento tradicional de front-end do Adobe Commerce, poderão decidir que é mais econômico criar seu próprio front-end personalizado do React.

Naturalmente, esse modelo requer fortes habilidades e recursos de desenvolvimento de front-end de integração de clientes ou sistemas, e você não obtém os benefícios da compatibilidade nativa com coisas como o Page Builder que você obtém com o PWA Studio. Sempre que um comerciante estiver construindo algo completamente personalizado, ele poderá perder vantagens no mercado.

Os front-ends personalizados também permitem inovações e experimentação. Há muita conversa sobre RA/RV ou comércio de voz, e uma arquitetura como a da Adobe Commerce permite que os comerciantes explorem essas opções sem afetar suas lojas na Web existentes.
