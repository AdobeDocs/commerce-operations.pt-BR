---
title: Arquitetura de vitrine unida
description: Saiba mais sobre o que uma loja acoplada significa no contexto de arquiteturas Adobe Commerce sem periféricos.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Arquitetura de vitrine combinada (herdada) da Adobe Commerce

A opção de implantação padrão atual para a maioria dos clientes comerciais inclui:

- Suporte a recursos de 100% em B2B e B2C
- Tema de referência maduro (Luma) que pode ser implantado/personalizado rapidamente
- Experiência de implementação de parceiros SI maduros
- Totalmente compatível com os recursos de comércio, como o Page Builder ou o Staging &amp; Preview
- Ampla compatibilidade com extensões no Adobe Commerce Marketplace

![Diagrama mostrando uma arquitetura de vitrine acoplada do Adobe Commerce](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Desvantagens da vitrine herdada

- **Sem cabeça**—Toda parte do aplicativo monolítico Adobe Commerce. Nenhuma separação de lógica e processos de negócios entre o front-end e o back-end.

- **Não PWA**—Embora o tema seja responsivo, o desempenho do site fica muito atrás do melhor PWA.

- **Arquitetura front-end (componentes da interface do usuário do Adobe Commerce)**—Especialistas em Adobe Commerce/PHP para trabalhar com base em vitrines legadas.

Antes de chegarmos às opções sem cabeça, vamos começar com a arquitetura de vitrine mais familiar. Se o headless fosse dissociado, esta seria a arquitetura de vitrine acoplada, mais comumente vista com nossas demonstrações Luma.

É aqui que os recursos de loja são totalmente integrados aos principais serviços de comércio, não separados pela camada GraphQL da API. Então, há muita lógica de negócios acoplada a esse tema. Essa abordagem não é imprudente e não é PWA.

Atualmente, essa é a opção mais comum que os comerciantes usam, pois tem suporte a recursos de 100% com recursos de comércio B2B e B2C. A comunidade está familiarizada com isso, há um ecossistema maduro de especialistas e tem ampla compatibilidade com as extensões do Adobe Commerce Marketplace.

No entanto, falta-lhe os benefícios de que falámos anteriormente. Sem a separação de camadas, há muitas dependências e possíveis pontos de falha quando as alterações são feitas. Não é tão produtivo quanto um PWA bem implementado e, se um comerciante não tiver experiência em desenvolvimento de Adobe Commerce ou PHP, ele precisará encontrar esses recursos.
