---
title: Opções de back-end de cache e referência de armazenamento
description: Saiba mais sobre as opções de back-end do cache no Adobe Commerce, incluindo sistema de arquivos, Redis, Valkey e armazenamento de banco de dados. Descubra abordagens herdadas e modernas.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 3d64249bf778a5aa73db22a532a454bb37d6dd37
workflow-type: tm+mt
source-wordcount: 309
ht-degree: 0%

---

# Opções de back-end de cache e referência de armazenamento

{{cloud-cache-config}}

O aplicativo Commerce usa um front-end e back-end de cache de baixo nível para fornecer acesso ao armazenamento em cache. O Commerce oferece suporte a vários back-end e estratégias de armazenamento em cache, cada um adequado a casos de uso diferentes. Esta página descreve as infraestruturas disponíveis e a sua diferença.

>[!NOTE]
>
>[Verniz](config-varnish.md) lida com o armazenamento em cache de página inteira no nível HTTP e não usa o back-end de cache de nível baixo.

## Opções de cache de back-end

A tabela a seguir resume os caches de backend disponíveis:

| Infraestrutura | Descrição | Guia de configuração |
| ------- | ----------- | ------------------- |
| Sistema de arquivos | Padrão. Armazena dados do cache em arquivos em `var/cache/`. Nenhuma configuração é necessária. | N/D |
| [Redis](config-redis.md) | Armazenamento de dados na memória para cache de alto desempenho. | [Usar Redis para cache padrão](redis-pg-cache.md) |
| [Chave de valor](config-valkey.md) | Alternativa de código aberto e compatível com Redis. | [Usar Valkey para cache padrão](valkey-pg-cache.md) |
| [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Armazenamento em cache com base em banco de dados | [Criar mecanismos de cache personalizados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentação do desenvolvedor do Adobe) |

>[!IMPORTANT]
>
>{{redis-cache-support}}

## Abordagens de implementação

O Commerce oferece suporte a duas abordagens de implementação de back-end. A abordagem escolhida depende da versão do Commerce:

>[!BEGINTABS]

>[!TAB Cache herdado baseado no Zend (2.4.8 e anterior)]

Usa nomes completos de classe para a configuração de backend:

| Infraestrutura | Nome da classe |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

Eles são compatíveis com a interface `Zend_Cache_Backend`.

**Exemplo de configuração:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB Cache do Modern Symfony (2.4.9 e posterior, recomendado)]

>[!TIP]
>
>A implementação moderna do Symfony Cache oferece melhor desempenho através da conformidade com PSR-6, serialização Igbinary, compactação gzip, scripts Lua e conexões persistentes.

Usa nomes de tipo de back-end simplificados:

| Infraestrutura | Digitar nome |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| Sistema de arquivos | `file` |

**Exemplo de configuração:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Para obter opções completas de configuração, consulte:

- [Usar Redis para cache padrão](redis-pg-cache.md)
- [Usar Valkey para cache padrão](valkey-pg-cache.md)
- [Configuração do cache L2](level-two-cache.md)

Consulte a [documentação do Laminas](https://docs.laminas.dev/) para ver as opções herdadas baseadas no Zend.
