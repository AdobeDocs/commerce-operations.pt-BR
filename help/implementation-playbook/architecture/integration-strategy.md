---
title: Estratégia de integração do Adobe Commerce
description: Revise as estratégias e opções de integração para sua implementação do Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Estratégia de integração do Adobe Commerce

A capacidade de integrar sua plataforma é &quot;inegociável&quot;. As empresas querem que suas plataformas de comércio eletrônico sejam acessíveis a partir de vários pontos de contato e perfeitamente integradas a seus sistemas de tecnologia, especialmente seu ERP. A personalização, a escalabilidade global e a acessibilidade também desempenham um papel na compra da plataforma final.

Uma abordagem de integração holística para sistemas de loja e back-end é compatível com APIs GraphQL eficientes, APIs REST abrangentes e importação de arquivos em lote entre a Adobe Commerce e outros sistemas ou serviços.

A API do GraphQL do Adobe Commerce fornece cobertura abrangente para vitrines que você pode usar para integrar-se a outras vitrines, incluindo:

- Plataformas de experiência digital (DXPs) como Adobe Experience Manager e Bloomreach
- Sistemas de gerenciamento de conteúdo (CMS) como Drupal e WordPress
- Aplicativo de vitrine personalizado moderno, como Adobe Commerce, PWA Studio e Vue Storefront

O GraphQL fornece uma resposta eficiente e específica para cada canal, sem a busca excessiva de dados e uma implantação ágil de novos recursos de ponto de contato. Ele também é frequentemente escolhido para integrar com canais de vendas, como aplicativos nativos móveis, POS, IoT, canais sociais e canais de comércio de transmissão ao vivo, como Facebook, Google, Instagram, WeChat e TikTok.

A API REST do Adobe Commerce oferece cobertura abrangente de configuração do sistema e recursos de gerenciamento de dados, incluindo produtos e catálogos; carrinho, cotação e finalização; clientes, conta e empresas; e pedidos e devoluções. As APIs REST são compatíveis com operações em massa, vários modos de autenticação e autorização granular, portanto, as APIs REST geralmente são escolhidas para se integrarem a sistemas corporativos, incluindo:

- Sistemas de planejamento de recursos corporativos (ERP) como SAP
- Sistemas de gerenciamento de informações de produto (PIM) como o Akeneo
- Sistemas de gerenciamento de relacionamento com o cliente (CRM) como Salesforce
- Sistemas de gerenciamento de pedidos (OMS) como MOM, Manhattan e SAP
- Warehouse Management System (WMS) ou logística de terceiros (3PL) como Oracle, NetSuite e SAP WM
- Configurar, Preço, Cotação (CPQ) como o SalesforceCPQ
- Gerenciamento de ativos digitais (DAM) como o Adobe DAM.

As importações de arquivos em lote também são consideradas uma boa opção para integrar sistemas corporativos como ERPs e PIMs, já que esses dados não são alterados com frequência e você geralmente tem melhor desempenho com as importações de arquivos programadas. Portanto, as importações de arquivos em lote geralmente são escolhidas para sincronização de dados em massa diária/semanal e sincronizações de dados completas mensais, enquanto as APIs REST são escolhidas para sincronização de alteração de dados incremental, para melhor desempenho. Isso também é considerado apenas um trabalho agendado, mas pode ser feito com frequência — possivelmente a cada 15 minutos a 1 hora — dependendo das necessidades dos negócios.

## Opções de integração

A Adobe Commerce oferece três opções flexíveis de integração:

- Integração direta de sistema para sistema com conectores pré-construídos. Alguns sistemas podem já ter extensões do Adobe Commerce no Adobe Commerce Marketplace ou em seu próprio site.

- Integração de sistema para sistema por meio de middleware personalizado. A solução middleware personalizada implantada será usada para mapeamento, tradução e gerenciamento de dados de processo.

- Integração de sistema para sistema por meio do iPaaS (Integration Platform-as-a-Service), também conhecido como EAI (Enterprise Application Integration Platform), como Mulesoft, Boomi e Software AG.

![Opções de integração do Adobe Commerce](../../assets/playbooks/integration-options.svg)

Embora as integrações em tempo real sejam normalmente desejadas, elas não são necessárias para alguns cenários. O Adobe Commerce oferece suporte nativo [!DNL RabbitMQ] como o barramento de mensagens para habilitar processos assíncronos, o que é recomendado para alguns dados que não são necessários para a troca em tempo real, mas para a atualização com a troca de arquivos em lote ou a API do processo de dados em lote REST para o processamento assíncrono.
