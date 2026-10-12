---
title: Práticas recomendadas para configurar sites, lojas e visualizações de loja
description: Conheça as práticas recomendadas para configurar sites, lojas e exibições de loja a fim de maximizar o desempenho do site.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# Prática recomendada para configurar sites, lojas e visualizações de loja

Para o Adobe Commerce em infraestrutura em nuvem, as práticas recomendadas se aplicam especificamente ao ambiente de produção (e possivelmente à arquitetura Staging on Pro, sujeita a restrições de recursos) que teria mais recursos do que os ambientes de integração e desenvolvimento.

## Produtos e versões afetados

[Todas as versões &#x200B;](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Estratégias para melhorar o desempenho

Se o projeto exigir muitos sites, lojas ou visualizações de loja, você poderá usar as seguintes estratégias para melhorar o desempenho:

- Reestruturar o catálogo mudando a lógica para categorias
- Separe as listas de preços dos dados do catálogo usando o preço externo e um Sistema de Gerenciamento de Preços (PMS).
- Usar um armazenamento de dados noSQL alternativo como o Elasticsearch

## Possíveis impactos no desempenho

Sites e lojas são multiplicadores para dados de catálogo, portanto, ter muitos sites e lojas pode afetar negativamente o desempenho do site das seguintes maneiras:

- Tabelas de índice maiores aumentam o tempo necessário para concluir as operações de indexação [Índice de preços].
- O aumento do tempo para recuperar a configuração do aplicativo degrada o tempo de resposta da loja para páginas de catálogo não armazenadas em cache.
- Aumentos significativos no tempo necessário para concluir as operações de salvamento no Administrador, pois os dados são salvos separadamente para cada site.


## Informações adicionais

- [Noções básicas sobre sites, lojas e visualizações de loja](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure-store/best-practices)
- [Configurar vários sites ou lojas](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)
