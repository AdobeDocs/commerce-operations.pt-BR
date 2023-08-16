---
title: Práticas recomendadas para configurar sites, lojas e visualizações de loja
description: Conheça as práticas recomendadas para configurar sites, lojas e exibições de loja a fim de maximizar o desempenho do site.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Prática recomendada para configurar sites, lojas e visualizações de loja

Para obter o melhor desempenho do site, configure no máximo 50 sites, 50 lojas e 50 visualizações de loja para o Adobe Commerce em projetos de infraestrutura em nuvem.

>[!NOTE]
>
>Para o Adobe Commerce em infraestrutura em nuvem, as práticas recomendadas se aplicam especificamente ao ambiente de produção (e possivelmente à arquitetura Staging on Pro, sujeita a restrições de recursos) que teria mais recursos do que os ambientes de integração e desenvolvimento. Para integração (Pro e Starter) e ambientes de preparo (Starter), reduza o número de visualizações da loja para menos de 5 ou 10 (sujeito a revisão técnica).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Estratégias para melhorar o desempenho

Se o projeto exigir muitos sites, lojas ou visualizações de loja, você poderá usar as seguintes estratégias para melhorar o desempenho:

- Reestruturar o catálogo mudando a lógica para categorias
- Separe as listas de preços dos dados do catálogo usando o preço externo e um Sistema de Gerenciamento de Preços (PMS).
- Usar um armazenamento de dados noSQL alternativo como o Elasticsearch

## Possíveis impactos no desempenho

Sites e lojas são multiplicadores para dados de catálogo, portanto, ter muitos sites e lojas pode afetar negativamente o desempenho do site das seguintes maneiras:

- Tabelas de índice maiores aumentam o tempo necessário para concluir operações de indexação [Índice de preço].
- O aumento do tempo para recuperar a configuração do aplicativo degrada o tempo de resposta da loja para páginas de catálogo não armazenadas em cache.
- Aumentos significativos no tempo necessário para concluir as operações de salvamento no Administrador, pois os dados são salvos separadamente para cada site.


## Informações adicionais

- [Noções básicas sobre sites, lojas e visualizações de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Configurar vários sites ou lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
