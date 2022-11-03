---
title: Agendamento de atualizações do Administrador em sites de produção
description: Conheça as práticas recomendadas para agendar atualizações críticas para o Adobe Commerce, a fim de evitar o desempenho lento e as interrupções.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Práticas recomendadas para agendar atualizações de administradores em sites de produção

Agende atualizações e operações críticas nos sites da Adobe Commerce fora do horário de pico para evitar desempenho lento e interrupções nos sites de produção.

Exemplos de ações críticas:

- Alterações na configuração do administrador, por exemplo, atualização de um atributo de produto ou transferência de uma subcategoria de produto para outra categoria
- Operações de importação ou exportação de dados

Ações críticas levam a operações de invalidação e reindexação de cache, o que aumenta significativamente o tempo de resposta, o que pode causar paralisações no site.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Informações adicionais

- [Práticas recomendadas para armazenamento em cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Conteúdo privado: Invalidar conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recomendações de hardware: Caches](../../../performance/hardware.md#caches)
- [Configuração avançada: Configurar Redis](../../../performance/advanced-setup.md#set-up-redis)

