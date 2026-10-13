---
title: Agendando atualizações de administrador em sites de produção
description: Conheça as práticas recomendadas para agendar atualizações críticas para o Adobe Commerce a fim de evitar desempenho lento e interrupções.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%
---
# Práticas recomendadas para agendar atualizações de Administrador em sites de produção

Agende atualizações e operações críticas nos sites da Adobe Commerce fora do horário de pico para evitar desempenho lento e paralisações nos sites de produção.

Exemplos de ações críticas:

- Alterações na configuração do administrador, por exemplo, atualizar um atributo de produto ou mover uma subcategoria de produto para outra categoria
- Operações de importação ou exportação de dados

As ações críticas resultam em operações de invalidação e reindexação de cache, o que aumenta significativamente o tempo de resposta que pode causar paralisações do site.

## Produtos e versões afetados

[Todas as versões &#x200B;](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Informações adicionais

- [Práticas recomendadas para armazenamento em cache](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Conteúdo privado: invalidar conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [Recomendações de hardware: caches](../../../performance/hardware.md#caches)
- [Configuração avançada: Configurar Redis](../../../performance/advanced-setup.md#set-up-redis)
