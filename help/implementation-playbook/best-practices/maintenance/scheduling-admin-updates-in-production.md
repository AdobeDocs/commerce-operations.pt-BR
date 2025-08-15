---
title: Agendando atualizações de administrador em sites de produção
description: Conheça as práticas recomendadas para agendar atualizações críticas para o Adobe Commerce a fim de evitar desempenho lento e interrupções.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Práticas recomendadas para agendar atualizações de Administrador em sites de produção

Agende atualizações e operações críticas nos sites da Adobe Commerce fora do horário de pico para evitar desempenho lento e paralisações nos sites de produção.

Exemplos de ações críticas:

- Alterações na configuração do administrador, por exemplo, atualizar um atributo de produto ou mover uma subcategoria de produto para outra categoria
- Operações de importação ou exportação de dados

As ações críticas resultam em operações de invalidação e reindexação de cache, o que aumenta significativamente o tempo de resposta que pode causar paralisações do site.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Informações adicionais

- [Práticas recomendadas para armazenamento em cache](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Conteúdo privado: Invalidar conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recomendações de hardware: caches](../../../performance/hardware.md#caches)
- [Configuração avançada: Configurar Redis](../../../performance/advanced-setup.md#set-up-redis)
