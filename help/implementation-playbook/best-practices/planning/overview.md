---
title: Fase de planejamento da implementação
description: Saiba mais sobre as práticas recomendadas de implementação para a fase de planejamento de projetos do Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Fase de planejamento

A fase de planejamento inclui as seguintes atividades:

- Projeto arquitetônico
- Design do catálogo
- Compra de extensão
- Escopo do projeto
- Coleta de requisitos
- Vendas e marketing

As seções a seguir incluem informações de práticas recomendadas para a fase de planejamento.

## Coleta de requisitos

<table>
<thead>
  <tr>
    <th>Prática recomendada</th>
    <th>Descrição</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Configuração do aplicativo</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configurar sites, lojas e visualizações de loja</a></td>
    <td>Configure sites, lojas e visualizações de loja para maximizar o desempenho do site.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Problemas comuns de configuração</a></td>
    <td>Corrija e evite os cinco problemas de configuração mais comuns nos sites do Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Armazenamento em cache</a></td>
    <td>Use as ferramentas de gerenciamento de cache para melhorar o desempenho do site.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Armazenamento em cache de página inteira</a></td>
    <td>Saiba como trabalhar com dados públicos ao implementar o armazenamento em cache na extensão do Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Tamanho da memória do OPcache</a></td>
    <td>Evite a degradação do desempenho com configurações específicas de consumo de memória OPcache.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Configurar relatórios</a></td>
    <td>Otimize o desempenho do site removendo o módulo de relatórios se não estiver sendo usado.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuração do banco de dados</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Configurar banco de dados para implantações em nuvem</a></td>
    <td>Defina as configurações do banco de dados e do aplicativo para melhorar o desempenho ao implantar o Adobe Commerce em projetos de infraestrutura em nuvem.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configurar MySQL</a></td>
    <td>Saiba como os acionadores MySQL e as conexões subordinadas afetam o desempenho do site e como usá-los de maneira eficaz.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuração de serviços</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Configurar o Fastly</a></td>
    <td>Configure os serviços do Fastly para o projeto de infraestrutura do Adobe Commerce na nuvem.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Configurar canais de notificação para o New Relic</a></td>
    <td>Acesse seu painel do New Relic e analise os dados de seu projeto do Adobe Commerce na infraestrutura em nuvem.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configurar Redis</a></td>
    <td>Melhore o desempenho do armazenamento em cache usando a implementação estendida do cache Redis para o Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Tamanho do cache do Realpath</a></td>
    <td>Otimize o desempenho atualizando a configuração do cache `readpath` do PHP para usar as configurações recomendadas.</td>
  </tr>
</tbody>
</table>

## Projeto arquitetônico

| Prática recomendada | Descrição |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [Arquitetura de referência global (GRA)](../../architecture/global-reference/examples.md) | Entenda os métodos comuns de organização de uma base de código GRA. |

## Design do catálogo

| Prática recomendada | Descrição |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Configuração de categoria](catalog-management.md#category-limits) | Configure categorias de produtos para obter o desempenho ideal. |
| [Configuração do produto&#x200B;](catalog-management.md#product-sku-limits) | Configure as SKUs do produto para obter o desempenho ideal. |
| [Configuração de variação do produto](catalog-management.md#product-variations) | Configure as variações do produto para obter o desempenho ideal. |
| [Configuração de opções do produto](catalog-management.md#product-options) | Configure as opções do produto para obter o desempenho ideal. |
| [Configuração de atributos de produto&#x200B;](catalog-management.md#product-attributes) | Configure os atributos do produto para obter o desempenho ideal. |
| [Configuração de paginação para listas de produtos](catalog-management.md#product-listing-pagination) | Configure a paginação de lista de produtos para obter o desempenho ideal. |

## Extensões

| Prática recomendada | Descrição |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Usando extensões de terceiros no Adobe Commerce](extensions.md) | Saiba como evitar problemas de desempenho causados por extensões de terceiros do Adobe Commerce. |

## Escopo do projeto

| Prática recomendada | Descrição |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Escalonamentos de parceiros](partner-escalation.md) | Prepare-se para escalonar um problema de parceiro com uma Equipe de conta da Adobe ou saiba como evitar um escalonamento. |
| [Processamento do armazenamento de pagamentos](payment-processing-storage.md) | Processe e armazene com segurança os detalhes de pagamento. |

## Vendas e marketing

| Prática recomendada | Descrição |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limites do carrinho de produtos](catalog-management.md#cart-limits) | Gerenciar limites do carrinho para obter o desempenho ideal. |
| [Configurando promoções](catalog-management.md#promotions) | Configure vendas e promoções para itens em um carrinho de compras. |
