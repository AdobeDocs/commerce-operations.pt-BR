---
title: Arquitetura de referência corporativa
description: Saiba como implementar o Adobe Commerce usando a mais recente tecnologia de comércio combinável da Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Arquitetura de referência corporativa da Adobe Commerce

O Adobe Commerce é a plataforma baseada em experiência que combina flexibilidade técnica com facilidade de uso, tudo isso em um serviço de criação de experiências excepcionais que geram resultados comerciais.

A Commerce evoluiu para atender aos requisitos corporativos de desempenho, dimensionamento e segurança. A adoção de uma abordagem de implementação moderna que usa as mais recentes soluções de comércio combinável da Adobe é essencial para o sucesso dos negócios corporativos. Esta página descreve a abordagem moderna de implementação do Commerce em detalhes técnicos.

O diagrama de arquitetura a seguir ilustra o fluxo de dados entre o Adobe Commerce e todas as soluções da Adobe Experience Cloud.

![Diagrama de arquitetura mostrando como o Adobe Commerce se conecta às soluções da Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>Os fluxos de dados de alto nível mostrados no diagrama são consistentes na maioria das implementações corporativas. O componente principal que pode tornar as implementações exclusivas é a maneira como você cria seu catálogo (especialmente para B2B). Você deve mapear cuidadosamente a arquitetura do seu catálogo para as [APIs da Web do Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

A [infraestrutura do Adobe Commerce na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) é a base da implementação do Commerce. Ele fornece uma plataforma de hospedagem automatizada [secure](../../security-and-compliance/shared-responsibility.md) com uma abordagem de autoatendimento para criar, implantar, monitorar e gerenciar seu aplicativo da Commerce em um ambiente nativo em nuvem.

Consulte os seguintes detalhes técnicos do Cloud Foundation:

- [**Arquitetura em escala**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) — capacidade ajustada automaticamente para manter um desempenho estável e previsível
- [**Vários ambientes**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—Pré-provisionado com PHP, MySQL (MariaDB), Redis, RabbitMQ e tecnologias de mecanismo de pesquisa compatíveis para desenvolver, testar e implantar seu site
- [**Gerenciamento de configuração**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) — Arquivos de configuração de ambiente personalizáveis e CLI (interface de linha de comando) para gerenciar configurações de aplicativos, rotas, ações de compilação e implantação e notificações.
- [**Fluxo de trabalho baseado em Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) — crie e implante automaticamente após enviar alterações de código para desenvolvimento rápido e implantação contínua
- [**Observabilidade interna**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) — Ferramentas que combinam dados de log de várias fontes para ajudá-lo a gerenciar o desempenho do site e diagnosticar problemas
- [**Abrangente cobertura de API**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) e [REST](https://developer.adobe.com/commerce/webapi/rest) APIs para integrar o aplicativo Commerce principal com sistemas de terceiros e estender recursos do Commerce

## Integração com o Experience Cloud

O Adobe Commerce integra-se com todas as soluções da Experience Cloud para oferecer [experiências de comércio personalizadas em escala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

A [Conexão de Dados](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview) desbloqueia insights sobre o comportamento de compra dos compradores para que você possa criar experiências de compra personalizadas em todos os canais com outros produtos da Adobe Digital Experience.

>[!NOTE]
>
>Consulte os seguintes recursos para obter mais informações:
>
>- [blueprints de experiência digital](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) para obter mais detalhes técnicos.
>- Consulte [Personalizando a experiência do cliente](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integração com sistemas de terceiros

A Adobe fornece aos desenvolvedores pontos de extensão e ferramentas abrangentes para criar aplicativos que ampliam os principais recursos do Commerce e integram o Commerce a sistemas de terceiros (como CRMs, ERPS e PIMS). Essas ferramentas reduzem o custo total de propriedade da plataforma das seguintes maneiras:

- **Escalabilidade** — Os aplicativos podem ser dimensionados separadamente do software principal, permitindo maior eficiência e atualizações simplificadas.
- **Isolamento**-Um ambiente isolado significa que os desenvolvedores podem atualizar ou modificar suas extensões a seu critério, sem depender de uma versão principal.
- **Independência tecnológica** - Os desenvolvedores podem escolher qualquer pilha de tecnologia e linguagem de codificação que atenda às suas necessidades.

A Adobe fornece as seguintes ferramentas de desenvolvedor para criar integrações e personalizações:

- [**Malha de API para Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/)—Coordene e combine várias APIs, GraphQL, REST e outras fontes em um único ponto de extremidade de GraphQL consultável.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/)—Crie e implante aplicativos Web seguros e escalonáveis que estendam a funcionalidade do Commerce e se integrem a soluções de terceiros.
- [**Eventos**](https://developer.adobe.com/commerce/extensibility/events/) — Use disparadores de eventos personalizados para interagir com outras ferramentas de desenvolvimento extensíveis.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) — Use webhooks para acionar automaticamente interações entre o Commerce e sistemas de terceiros.
- [**Interface do Administrador SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)—Personalize e aprimore o Administrador do Commerce com novas páginas e recursos para seus comerciantes.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/) — acelere suas integrações de back-office com integrações de referência, scripts de integração e uma arquitetura padronizada.

>[!NOTE]
>
>Consulte [A abordagem moderna: extensibilidade efetiva no Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Serviços de vitrine

A Adobe fornece um conjunto avançado de serviços de merchandising inteligentes e combináveis para ajudá-lo a apoiar suas principais metas comerciais. Esses serviços também fornecem APIs essenciais para otimizar o desempenho em escala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview)—Forneça resultados mais inteligentes, mais rápidos e relevantes aos compradores com esta ferramenta de pesquisa habilitada por IA.
- [Recomendações de Produto](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview)—Adicione recomendações alimentadas por IA com base no comportamento do comprador, tendências populares, similaridade de produto e muito mais.
- [Serviço de Catálogo](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview)—Dê aos seus clientes uma experiência otimizada de produto enquanto aumenta o desempenho, melhora a escalabilidade e aumenta as conversões.
- [Serviços de Pagamento](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview)—Impulsione a satisfação do cliente oferecendo vários métodos de pagamento, incluindo prestações de pagamento sem juros, e uma única visão do processamento de pagamento, ordens e faturas.

## Loja headless

O comércio headless é o comércio iniciado pela API. O Adobe Commerce é totalmente headless com uma arquitetura dissociada que fornece todos os serviços e dados de comércio por meio de uma camada de API do GraphQL. Essa arquitetura permite que as equipes desenvolvam seus front-ends independentemente do aplicativo principal, fornecendo agilidade para criar e testar rapidamente novos pontos de contato com tecnologias emergentes.

O Adobe fornece uma moderna tecnologia headless de vitrine que inclui os mesmos benefícios e recursos oferecidos pelo [Edge Delivery Services](https://www.aem.live/home) com criação baseada em documentos, uma arquitetura de desempenho inovador e experimentação nativa pronta para uso. Ele aproveita a escala e o desempenho dos [serviços de vitrine](#storefront-services) da Adobe Commerce e a flexibilidade e conveniência dos [componentes drop-in](https://experienceleague.adobe.com/developer/commerce/storefront/) para fornecer recursos de comércio.

