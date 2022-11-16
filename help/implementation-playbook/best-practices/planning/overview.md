---
title: Fase de planejamento da implementação
description: Saiba mais sobre as práticas recomendadas de implementação para a fase de planejamento de projetos da Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 78308f9cb3d2ebe8af41c42f9bb146409367ab6c
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Fase de planeamento

A fase de planejamento inclui as seguintes atividades:

- Agrupamento de requisitos
- Design arquitetônico
- Design do catálogo
- Escopo do projeto
- Provisionamento de conta
- Acesso do usuário
- Compra de extensão

As seções a seguir incluem informações de práticas recomendadas para a fase de planejamento.

## Agrupamento de requisitos

- **Configuração do aplicativo**
   - [Práticas recomendadas para configurar sites, lojas e visualizações de loja (infraestrutura de nuvem)](sites-stores-store-views.md)
   - [Como evitar — e corrigir — os cinco problemas de configuração mais comuns para sites do Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Práticas recomendadas para armazenamento em cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Armazenamento em cache de página inteira](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Tamanho da memória do OPcache](opcache-memory-size.md)
   - [Configuração de relatórios](reporting-configuration.md)

- **Configuração do banco de dados**
   - [Práticas recomendadas de configuração de banco de dados para implantações em nuvem &#x200B;](database-on-cloud.md)
   - [&#x200B; de configuração da conexão subordinada MySQL](configure-mysql-slave-connection-on-cloud.md)
   - [Uso de acionadores MySQL](mysql-triggers-usage.md)

- **Configuração de serviços**
   - [Configurar rapidamente](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [Novo Relic - Configurar canais de notificação](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Práticas recomendadas para &#x200B; de configuração do serviço Redis](redis-service-configuration.md)
   - [Prática recomendada do tamanho do cache do Realpath](realpath-cache-size.md)

## **Design arquitetônico**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Noções básicas sobre a arquitetura de referência global](../../../implementation-playbook/architecture/global-reference.md)

## **Design do catálogo**

Os tópicos a seguir descrevem as práticas recomendadas de otimização de desempenho para configurar seu catálogo do Adobe Commerce, incluindo os máximos recomendados para o número de categorias, SKUs eficazes do produto, variações do produto, atributos e opções do produto e muito mais.

- [Configuração de categoria](category-limits.md)
- [&#x200B; de configuração do produto](product-sku-limits.md)
- [Configuração da variação do produto](product-variations.md)
- [Configuração das opções do produto](product-options.md)
- [&#x200B; de configuração dos atributos do produto](product-attributes-and-options.md)
- [Configuração de paginação para listagens de produtos](product-listing-pagination.md)

## **Vendas e Marketing**

- [Práticas recomendadas para o limite do carrinho de produtos](product-cart.md)
- [Práticas recomendadas para configurar promoções](product-cart-promotions.md)

## **Escopo do projeto**

- [Escalonamentos de parceiros](partner-escalation.md)
- [Processamento de armazenamento de pagamentos](payment-processing-storage.md)

## **Extensões de compra**

- [Práticas recomendadas para usar extensões de terceiros no Adobe Commerce](extensions.md)
