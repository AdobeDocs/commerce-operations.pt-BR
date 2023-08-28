---
title: Fase de planejamento da implementação
description: Saiba mais sobre as práticas recomendadas de implementação para a fase de planejamento de projetos do Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Fase de planejamento

A fase de planejamento inclui as seguintes atividades:

- Coleta de requisitos
- Projeto arquitetônico
- Design do catálogo
- Escopo do projeto
- Provisionamento de conta
- Acesso do usuário
- Compra de extensão

As seções a seguir incluem informações de práticas recomendadas para a fase de planejamento.

## Coleta de requisitos

- **Configuração do aplicativo**
   - [Práticas recomendadas para configurar sites, lojas e visualizações de loja (infraestrutura em nuvem)](sites-stores-store-views.md)
   - [Como evitar — e corrigir — os cinco problemas de configuração mais comuns nos sites do Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Práticas recomendadas para armazenamento em cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Armazenamento em cache de página inteira](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Tamanho da memória do OPcache](opcache-memory-size.md)
   - [Configuração de relatórios](reporting-configuration.md)

- **Configuração do banco de dados**
   - [Práticas recomendadas de configuração de banco de dados para implantações em nuvem&#x200B;](database-on-cloud.md)
   - [Configuração do MySQL&#x200B;](mysql-configuration.md)

- **Configuração de serviços**
   - [Configurar o Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Configurar canais de notificação](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Práticas recomendadas para a configuração do serviço Redis&#x200B;](redis-service-configuration.md)
   - [Prática recomendada de tamanho de cache do Realpath](realpath-cache-size.md)

## **Projeto arquitetônico**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Noções básicas sobre a arquitetura de referência global](../../../implementation-playbook/architecture/global-reference/overview.md)

## **Design do catálogo**

Os tópicos a seguir descrevem as práticas recomendadas de otimização de desempenho para configurar o catálogo do Adobe Commerce, incluindo os máximos recomendados para o número de categorias, SKUs eficazes do produto, variações do produto, atributos e opções do produto e muito mais.

- [Configuração de categoria](catalog-management.md#category-limits)
- [Configuração do produto&#x200B;](catalog-management.md#product-sku-limits)
- [Configuração da variação do produto](catalog-management.md#product-variations)
- [Configuração das opções do produto](catalog-management.md#product-options)
- [Configuração dos atributos do produto&#x200B;](catalog-management.md#product-attributes)
- [Configuração de paginação para listagens de produtos](catalog-management.md#product-listing-pagination)

## **Vendas e marketing**

- [Práticas recomendadas para limite do carrinho de produtos](catalog-management.md#cart-limits)
- [Práticas recomendadas para configurar promoções](catalog-management.md#promotions)

## **Escopo do projeto**

- [Escalonamentos de parceiros](partner-escalation.md)
- [Processamento de armazenamento de pagamentos](payment-processing-storage.md)

## **Extensões de compra**

- [Práticas recomendadas para usar extensões de terceiros no Adobe Commerce](extensions.md)
