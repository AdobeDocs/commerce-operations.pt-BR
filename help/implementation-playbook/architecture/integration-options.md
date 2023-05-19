---
title: Opções de integração do Adobe Commerce
description: Explore suas opções para integrar outros sistemas à implementação do Adobe Commerce.
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

![diagrama de monolito do Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Headless

O diagrama a seguir descreve uma abordagem headless que usa o Adobe Commerce como o sistema de back-end integrado a um aplicativo DXP/CMS/personalizado como o aplicativo da loja:

![Diagrama do Adobe Commerce headless](../../assets/playbooks/integration-headless.svg)

A única diferença entre a abordagem monolítica e headless é a integração de vitrines, que afeta a experiência do usuário para os clientes. O Monolithic usa a loja da Adobe Commerce diretamente para integrar-se com serviços de terceiros, enquanto o headless depende de sua própria loja para personalizar e integrar-se com os mesmos serviços. Alguns serviços, como pagamento e logon único (SSO), precisam de personalização da loja e do Adobe Commerce para finalizar o fluxo de integração.

## Sistemas de terceiros

Alguns serviços populares já têm excelentes extensões para oferecer suporte à Adobe Commerce ou soluções populares de vitrine, como PWA Studio, Adobe Experience Manager e Vue Storefront, que podem ser encontradas na loja de extensões ou em sites relacionados de terceiros. Mesmo que não haja uma extensão existente, o esforço para implementar a integração entre o Adobe Commerce e outras lojas headless é semelhante. Todos os serviços de terceiros geralmente têm documentos para explicar como integrar com eles. Estes serviços são apenas alguns exemplos; vários países e mercados podem ter escolhas diferentes.

## Integrações empresariais

Para integrações de sistemas corporativos, que normalmente também são chamadas de integrações de back-end, há um impacto no fluxo de dados dos negócios. Com base em diferentes tipos de negócios e necessidades, ele pode usar três opções de integração diferentes, que já introduzimos.

Dados obrigatórios do produto, como SKUs, inventário e preços base geralmente vêm de ERPs, enquanto os preços de vendas geralmente são gerenciados por cada canal de vendas (por exemplo, Adobe Commerce) ou CPQ (vendas B2B ou privadas). Como os dados obrigatórios do produto (exceto o inventário) não são alterados com frequência, a prática recomendada é usar atualizações em lote programadas por meio da API REST ou importação de arquivos em massa. Para o inventário, a prática recomendada é ter uma atualização completa diária do inventário de produtos que é compartilhado com diferentes canais de vendas para evitar vendas excessivas. Além disso, faça alterações incrementais em seu ERP programado em 24 horas.

O catálogo de produtos, os metadados e o conteúdo de marketing podem ser gerenciados separadamente por cada canal de vendas (por exemplo, Adobe Commerce) ou por um PIM central. Como os metadados também não são alterados com frequência, a prática recomendada é usar atualizações em lote programadas por meio da API REST ou importação de arquivos em massa.

Os dados do pedido incluem dados de pedido, cotação (B2B), remessa, devolução e troca que geralmente são gerenciados de um sistema OMS e WMS centralizado. Os dados de pedido devem ser sincronizados o mais rápido possível, de modo que a API REST geralmente é a melhor opção. Para obter melhor desempenho, considere reduzir o número de chamadas de API. Para os dados de status do pedido, remessas, devolução e troca, considere programar APIs de atualização em lote REST em horas ou minutos.

Os dados B2B geralmente são gerenciados a partir de um CRM centralizado. Uma API em tempo real é usada para verificar clientes existentes e criar novos clientes. Para B2B, pode ser necessário introduzir mais APIs para sincronizar diferentes funcionários, grupos e listas de preços da empresa entre o Adobe Commerce e seu CRM ou CPQ.

Há algumas outras integrações de sistema, como eDM para marketing por email e business intelligence para análise de dados de negócios — que geralmente são feitas por meio da API REST ou exportação/importação de arquivos, que geralmente são compatíveis com as extensões existentes.
