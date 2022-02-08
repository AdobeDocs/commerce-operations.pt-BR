---
title: Opções de integração do Adobe Commerce
description: Explore suas opções para integrar outros sistemas à sua implementação do Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Pontos de integração e fluxos de dados típicos

Há duas abordagens principais para integrações e fluxos de dados, que são muito semelhantes, mas têm uma diferença principal.

## Monolítico

O diagrama a seguir descreve uma abordagem monolítica que usa o Adobe Commerce como sistema de back-end e aplicativo de vitrine:

![Diagrama monolítico do Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Cabeça

O diagrama a seguir descreve uma abordagem sem cabeçalho que usa o Adobe Commerce como o sistema de back-end integrado a um aplicativo personalizado DXP/CMS como o aplicativo de vitrine:

![Diagrama sem periféricos do Adobe Commerce](../../assets/playbooks/integration-headless.svg)

A única diferença entre a abordagem monolítica e sem interface é a integração de vitrine, que afeta a experiência do usuário para os clientes. A Monolítica usa a loja da Adobe Commerce diretamente para integrar com serviços de terceiros, enquanto a headless depende de sua própria loja para personalizar e integrar com os mesmos serviços. Alguns serviços como pagamento e logon único (SSO) precisam da loja e da personalização do Adobe Commerce para finalizar o fluxo de integração.

## Sistemas de terceiros

Alguns serviços populares já têm excelentes extensões para oferecer suporte à Adobe Commerce ou a soluções populares de vitrine, como PWA Studio, Adobe Experience Manager e Vue Storefront, que podem ser encontradas no mercado de extensões ou em sites de terceiros relacionados. Mesmo que não haja uma extensão existente, o esforço para implementar a integração entre o Adobe Commerce e outras vitrines sem periféricos é semelhante. Todos os serviços de terceiros geralmente têm documentos para explicar como integrar-se com eles. Estes serviços são apenas alguns exemplos; diversos países e mercados podem ter opções diferentes.

## Integrações empresariais

Para integrações de sistemas empresariais, que também são normalmente chamadas de integrações de backend, há um impacto no fluxo de dados dos negócios. Com base em diferentes tipos de negócios e necessidades, ele pode usar três opções de integração diferentes, que já introduzimos.

Os dados obrigatórios do produto, como SKUs, inventário e preços de base geralmente vêm de ERPs, enquanto os preços de venda são geralmente gerenciados por cada canal de vendas (por exemplo, Adobe Commerce) ou CPQ (B2B ou vendas privadas). Como os dados obrigatórios do produto (exceto o inventário) não são alterados com frequência, a prática recomendada é usar atualizações de lote agendadas por meio da API REST ou importação de arquivo em massa. Para o inventário, a prática recomendada é ter uma atualização completa diariamente para o inventário de produtos compartilhado com diferentes canais de vendas para evitar vendas excessivas. Além disso, faça alterações incrementais em seu ERP agendado em 24 horas.

O catálogo de produtos, os metadados e o conteúdo de marketing podem ser gerenciados separadamente por cada canal de vendas (por exemplo, Adobe Commerce) ou de um PIM central. Como os metadados também não são alterados com frequência, a prática recomendada é usar atualizações em lote agendadas por meio da API REST ou importação de arquivo em massa.

Os dados da ordem incluem dados de ordem, cotação (B2B), remessa, devolução e troca que são geralmente gerenciados de um sistema OMS e WMS centralizado. Os dados do pedido devem ser sincronizados o mais rápido possível, de modo que a API REST geralmente é a melhor opção. Para obter melhor desempenho, considere reduzir o número de chamadas de API. Para o status do pedido, remessas, devolução e troca de dados, considere programar APIs de atualização de lote REST em horas ou minutos.

Os dados B2B geralmente são gerenciados a partir de um CRM centralizado. Uma API em tempo real é usada para verificar clientes existentes e criar novos clientes. Para B2B, pode ser necessário introduzir mais APIs para sincronizar diferentes funcionários, grupos e listas de preços da empresa entre o Adobe Commerce e seu CRM ou CPQ.

Existem algumas outras integrações de sistema, como eDM, para marketing por email e inteligência de negócios para análise de dados de negócios, que geralmente são feitas por meio da REST API ou exportação/importação de arquivos, que geralmente são suportadas pelas extensões existentes.
