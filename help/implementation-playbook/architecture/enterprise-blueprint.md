---
title: Arquitetura de referência corporativa
description: Saiba como implementar o Adobe Commerce usando a tecnologia de comércio combinável mais recente da Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: c2f6b7125f1a611e94f807999787fee48a0e5ece
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Arquitetura de referência corporativa da Adobe Commerce

O Adobe Commerce é a plataforma baseada em experiência que combina flexibilidade técnica com facilidade de uso, tudo isso em um serviço de criação de experiências excepcionais que geram resultados comerciais.

A Commerce evoluiu para atender aos requisitos corporativos de desempenho, dimensionamento e segurança. A adoção de uma abordagem de implementação moderna que usa as soluções comerciais combináveis mais recentes do Adobe é essencial para o sucesso dos negócios corporativos. Esta página descreve a abordagem moderna de implementação do Commerce em detalhes técnicos.

O diagrama de arquitetura a seguir ilustra o fluxo de dados entre o Adobe Commerce e todas as soluções da Adobe Experience Cloud.

![Diagrama da arquitetura que mostra como o Adobe Commerce se conecta às soluções Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoom=&quot;yes&quot;}

>[!NOTE]
>
>Os fluxos de dados de alto nível mostrados no diagrama são consistentes na maioria das implementações corporativas. O componente principal que pode tornar as implementações exclusivas é a maneira como você cria seu catálogo (especialmente para B2B). Você deve mapear cuidadosamente sua arquitetura de catálogo para o [APIs da Web do Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) O é a base da implementação do Commerce. Fornece uma [seguro](../../security-and-compliance/shared-responsibility.md) plataforma de hospedagem automatizada com uma abordagem de autoatendimento para criar, implantar, monitorar e gerenciar seu aplicativo da Commerce em um ambiente nativo em nuvem.

Consulte os seguintes detalhes técnicos do Cloud Foundation:

- [**Arquitetura dimensionada**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Capacidade ajustada automaticamente para manter um desempenho estável e previsível
- [**Vários ambientes**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—Pré-provisionado com PHP, MySQL (MariaDB), Redis, RabbitMQ e tecnologias de mecanismo de pesquisa compatíveis para desenvolver, testar e implantar seu site
- [**Gerenciamento de configuração**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)— arquivos de configuração personalizáveis do ambiente e CLI (Command-Line Interface, interface de linha de comando) para gerenciar configurações de aplicativos, rotas, ações de criação e implantação e notificações.
- [**Fluxo de trabalho baseado no Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow)— crie e implante automaticamente depois de enviar alterações de código para desenvolvimento rápido e implantação contínua
- [**Observabilidade integrada**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)— ferramentas que combinam dados de registro de várias origens para ajudá-lo a gerenciar o desempenho de seu site e diagnosticar problemas
- [**Cobertura abrangente da API**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) e [REST](https://developer.adobe.com/commerce/webapi/rest) APIs para integrar o aplicativo principal do Commerce a sistemas de terceiros e estender os recursos do Commerce

## Integração com o Experience Cloud

A Adobe Commerce integra-se com todas as soluções de Experience Cloud para oferecer [experiências de comércio personalizadas em escala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Conexão de dados](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) O desbloqueia insights sobre o comportamento de compra dos compradores para que você possa criar experiências de compra personalizadas em todos os canais com outros produtos da Adobe Digital Experience.

>[!NOTE]
>
>Consulte [Blueprints de experiência digital](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) para obter mais detalhes técnicos.


## Integração com sistemas de terceiros

O Adobe fornece aos desenvolvedores pontos de extensão e ferramentas abrangentes para criar aplicativos que ampliam os principais recursos do Commerce e integram o Commerce a sistemas de terceiros (como CRMs, ERPS e PIMS). Essas ferramentas reduzem o custo total de propriedade da plataforma das seguintes maneiras:

- **Escalabilidade**— os aplicativos podem ser dimensionados separadamente do software principal, permitindo maior eficiência e upgrades simplificados.
- **Isolamento**-Um ambiente isolado significa que os desenvolvedores podem atualizar ou modificar suas extensões a seu critério, sem depender de uma versão principal.
- **Independência tecnológica**-Os desenvolvedores podem escolher qualquer tecnologia que esteja empilhada e linguagens de codificação que atendam às suas necessidades.

O Adobe fornece as seguintes ferramentas de desenvolvedor para criar integrações e personalizações:

- [**Malha de API para o Construtor de aplicativos Adobe Developer**](https://developer.adobe.com/graphql-mesh-gateway/)— coordene e combine várias APIs, GraphQL, REST e outras origens em um único endpoint do GraphQL consultável.
- [**Construtor de aplicativos**](https://developer.adobe.com/app-builder/docs/overview/)— crie e implante aplicativos Web seguros e dimensionáveis que ampliem a funcionalidade do Commerce e integrem-se a soluções de terceiros.
- [**Eventos**](https://developer.adobe.com/commerce/extensibility/events/)—Use acionadores de eventos personalizados para interagir com outras ferramentas de desenvolvimento extensíveis.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/)—Use webhooks para acionar automaticamente interações entre o Commerce e sistemas de terceiros.
- [**SDK da interface do usuário do administrador**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)—Personalize e aprimore o administrador do Commerce com novas páginas e recursos para seus comerciantes.

## Serviços de vitrine

O Adobe fornece um conjunto avançado de serviços de merchandising inteligentes e combináveis para ajudá-lo a apoiar suas principais metas comerciais. Esses serviços também fornecem APIs essenciais para otimizar o desempenho em escala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)— forneça resultados mais inteligentes, mais rápidos e relevantes para os compradores com essa ferramenta de pesquisa alimentada por IA.
- [Recommendations do produto](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)—Adicione recomendações alimentadas por IA com base no comportamento do comprador, tendências populares, similaridade de produtos e muito mais.
- [Serviço de catálogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview)— proporcione aos clientes uma experiência otimizada com os produtos enquanto aumenta o desempenho, melhora a escalabilidade e aumenta as conversões.
- [Payment Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)— conduza a satisfação do cliente oferecendo vários métodos de pagamento, inclusive parcelas sem juros, e uma visão única do processamento de pagamentos, pedidos e faturas.

## Loja headless

O comércio headless é o comércio iniciado pela API. O Adobe Commerce é totalmente headless com uma arquitetura dissociada que fornece todos os serviços e dados de comércio por meio de uma camada de API do GraphQL. Essa arquitetura permite que as equipes desenvolvam seus front-ends independentemente do aplicativo principal, fornecendo agilidade para criar e testar rapidamente novos pontos de contato com tecnologias emergentes.

O Adobe fornece uma tecnologia de vitrine headless moderna que inclui os mesmos benefícios e recursos oferecidos pelo [Edge Delivery Services](https://www.aem.live/home) com criação baseada em documentos, uma arquitetura de desempenho inédita e experimentação nativa pronta para uso. Ele aproveita a escala e o desempenho do Adobe Commerce [serviços de vitrine](#storefront-services) e a flexibilidade e conveniência da [componentes suspensos](https://experienceleague.adobe.com/developer/commerce/storefront/) para fornecer recursos de comércio.

