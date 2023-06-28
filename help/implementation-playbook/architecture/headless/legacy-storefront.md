---
title: Arquitetura da frente de loja associada
description: Saiba mais sobre o que significa uma loja acoplada no contexto de arquiteturas headless Adobe Commerce.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Arquitetura de vitrine combinada (herdada) da Adobe Commerce

A opção de implantação padrão atual para a maioria dos clientes comerciais inclui:

- Suporte total a recursos em B2B e B2C
- Tema de referência madura (Luma) que pode ser implantado/personalizado rapidamente
- Experiência em implementação de parceiros de SI maduros
- Totalmente compatível com recursos de comércio como o Page Builder ou o Staging &amp; Preview
- Ampla compatibilidade com extensões no Adobe Commerce Marketplace

![Diagrama mostrando uma arquitetura de vitrine acoplada do Adobe Commerce](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Desvantagens da vitrine herdada

- **Sem headless**— Todas as partes do aplicativo monolítico Adobe Commerce. Sem separação de lógica e processos de negócios entre o front-end e o back-end.

- **Não é PWA**—Embora o tema seja responsivo, o desempenho do site fica muito atrás do melhor PWA da categoria.

- **Arquitetura de front-end (componentes da interface do usuário do Adobe Commerce)**—Especialistas em Adobe Commerce/PHP para utilizar vitrines herdadas.

Antes de entrarmos nas opções headless, vamos começar com a arquitetura de vitrine mais familiar. Se headless estiver dissociado, essa será a arquitetura de vitrine acoplada, mais comumente vista com nossas demonstrações do Luma.

É aqui que os recursos da loja são totalmente integrados aos principais serviços de comércio, não separados por essa camada de API do GraphQL. Então, há muita lógica de negócios acoplada a esse tema. Essa abordagem não é headless, e não é PWA.

Atualmente, essa é a opção mais comum que os comerciantes usam porque tem 100% de suporte a recursos com recursos B2B e B2C Commerce. A comunidade está familiarizada com ele, há um ecossistema maduro de conhecimento e ampla compatibilidade com as extensões do Adobe Commerce Marketplace.

No entanto, falta-lhe os benefícios de que falámos anteriormente. Sem a separação das camadas, há muitas dependências e pontos potenciais de falha quando as alterações são feitas. Ele não tem o mesmo desempenho de um PWA bem implementado e se um comerciante não tiver conhecimento especializado em desenvolvimento de Adobe Commerce ou PHP, ele terá que encontrar esses recursos.
