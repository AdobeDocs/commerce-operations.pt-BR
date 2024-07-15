---
title: Práticas recomendadas para blocos de conteúdo privado
description: Conheça as práticas recomendadas para configurar blocos de conteúdo privado para otimizar o desempenho da loja.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Práticas recomendadas para blocos de conteúdo privado

Quando um bloco de conteúdo privado contém a variável `_isScopePrivate`, o bloco não pode ser armazenado em cache. Como o bloco privado não é armazenado em cache, o Adobe Commerce deve recuperar os mesmos dados para cada solicitação do cliente, o que aumenta a carga do servidor.

Em vez de usar a variável `_isScopePrivate` para conteúdo privado, crie um bloco e um modelo para exibir dados agnósticos do usuário. Esses dados são substituídos por dados específicos do usuário pelo componente de interface do usuário do Adobe Commerce, que lida com dados de pré-renderização de maneira mais eficiente. Para obter instruções, consulte [Conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) em _[!DNL Commerce PHP Extensions Guide]_.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Possível impacto no desempenho

Sites que têm blocos de conteúdo privado contendo as variáveis `_isScopePrivate` acionam solicitações do AJAX para recuperar os mesmos dados para cada solicitação de cliente. Isso aumenta o tempo de resposta e usa recursos adicionais que poderiam ser usados para lidar com operações mais críticas para os negócios da loja, como registro do cliente, atualizações do carrinho de compras, envio de pedidos e transações de pagamento.

## Informações adicionais

- [Conteúdo privado](../../../performance/configuration.md#client-side-optimization-settings)
- [Solicitações AJAX de alta taxa de transferência causam desempenho insatisfatório](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
