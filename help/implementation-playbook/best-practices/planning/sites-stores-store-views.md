---
title: Práticas recomendadas para configurar sites, lojas e visualizações de loja
description: Conheça as práticas recomendadas para configurar sites, lojas e visualizações de loja a fim de maximizar o desempenho do site.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Prática recomendada para configurar sites, lojas e exibição de loja

Para obter o melhor desempenho do site, configure no máximo 50 sites, 50 lojas e 50 visualizações de loja para o Adobe Commerce em projetos de infraestrutura em nuvem.

>[!NOTE]
>
>Para o Adobe Commerce na infraestrutura de nuvem, as práticas recomendadas se aplicam especificamente ao ambiente de produção (e possivelmente ao ambiente de preparo no Pro, sujeito às restrições de recursos), que teria mais recursos do que os ambientes de integração e desenvolvimento. Para integração (Pro e Starter) e ambientes de preparo (Starter), reduza o número de visualizações da loja para menos de 5 ou 10 (sujeito a revisão técnica).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Estratégias para melhorar o desempenho

Se seu projeto exigir vários sites, lojas ou visualizações de loja, você pode usar as seguintes estratégias para melhorar o desempenho:

- Reestruturar catálogo alterando a lógica para categorias
- Separe as listas de preços dos dados do catálogo usando um preço externo e um Sistema de Gerenciamento de Preços (PMS).
- Use um armazenamento de dados alternativo noSQL como o Elasticsearch

## Potenciais impactos no desempenho

Os sites e lojas são multiplicadores para dados de catálogo, portanto, ter muitos sites e lojas pode afetar negativamente o desempenho do site das seguintes maneiras:

- Tabelas de índice maiores aumentam o tempo necessário para concluir operações de indexação [Índice de preços].
- Aumento do tempo para recuperar a configuração do aplicativo degrada o tempo de resposta da loja para páginas de catálogo não armazenadas em cache.
- Aumento significativo no tempo necessário para concluir as operações de Salvar no Administrador, pois os dados são salvos separadamente para cada site.


## Informações adicionais

- [Como entender sites, lojas e visualizações de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Configurar vários sites da Web ou lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

