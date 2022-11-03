---
title: Práticas recomendadas para blocos de conteúdo privado
description: Conheça as práticas recomendadas para configurar blocos de conteúdo privado a fim de otimizar o desempenho da vitrine.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Práticas recomendadas para blocos de conteúdo privado

Quando um bloco de conteúdo privado contém a variável `_isScopePrivate` , o bloco não pode ser armazenado em cache. Como o bloco privado não é armazenado em cache, a Adobe Commerce deve recuperar os mesmos dados para cada solicitação de cliente que aumenta a carga do servidor.

Em vez de usar o `_isScopePrivate` para conteúdo privado, crie um bloco e um modelo para exibir dados agnósticos do usuário. Esses dados são substituídos por dados específicos do usuário pelo Adobe Commerce [componente da interface do usuário](https://glossary.magento.com/ui-component/), que lida com dados de pré-renderização de forma mais eficiente. Para obter instruções, consulte [Conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) no _[!DNL Commerce PHP Extensions Guide]_.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Potencial impacto no desempenho

Sites com blocos de conteúdo privado que contêm a variável `_isScopePrivate` As variáveis acionam AJAX solicitações para recuperar os mesmos dados para cada solicitação do cliente. Isso aumenta o tempo de resposta e usa recursos adicionais que podem ser usados para lidar com mais operações de vitrine críticas para os negócios, como registro de clientes, atualizações de carrinhos de compras, envio de pedidos e transações de pagamento.

## Informações adicionais

- [Conteúdo privado](../../../performance/configuration.md#client-side-optimization-settings)
- [Solicitações de AJAX de alta taxa de transferência causam baixo desempenho](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


