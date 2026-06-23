---
title: Configurar front-end do cache
description: Saiba como definir front-ends de cache e associá-los a tipos de cache no Adobe Commerce. Descubra a sintaxe de configuração para env.php e di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ae31702797c8754a719e5a5eb39a3924e723c87a
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 0%

---

# Configurar front-ends do cache

Um front-end de cache é uma interface entre o Commerce e o back-end de armazenamento em cache. Você pode definir vários front-ends, cada um com configurações de back-end diferentes, e atribuir [tipos de cache](../cli/manage-cache.md#clean-and-flush-cache-types) específicos a cada front-end.

Isso é útil quando você deseja usar diferentes back-ends de cache ou configurações para diferentes tipos de dados em cache. Por exemplo, você pode querer o cache de `full_page` em um banco de dados Redis dedicado ao usar um banco de dados separado para o cache de `default`.

{{cloud-cache-config}}

## Usar o front-end padrão

O Commerce fornece um front-end de cache do `default` que funciona para todos os tipos de cache. Ele estende o [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando o cache de front-end [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

Na maioria dos casos, não é necessário personalizar o front-end. Você só precisa configurar o back-end. Consulte [Opções de back-end do cache](cache-options.md).

## Definir um front-end do cache personalizado

As etapas a seguir passam pela associação de um front-end de cache com um tipo de cache.

### Etapa 1: definir um front-end do cache e atribuir tipos de cache

Para definir um front-end de cache personalizado, adicione a configuração a `app/etc/env.php` (que substitui `di.xml`):

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Onde:

- `<unique frontend id>` — Um nome exclusivo para identificar o front-end (por exemplo, `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>` — Tipo de back-end e opções para este front-end (consulte [Opções de cache](cache-options.md))
- `<cache type>` — Um tipo de cache do Commerce a ser atribuído a este front-end (por exemplo, `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>**Implementação do Modern Symfony Cache (2.4.9+):** A partir do Commerce 2.4.9, você pode usar tipos de back-end simplificados como `redis`, `valkey` ou `file` com a implementação moderna do Symfony Cache. Consulte [Usar Redis para cache padrão](redis-pg-cache.md) e [Usar Valkey para cache padrão](valkey-pg-cache.md) para obter detalhes.

### Etapa 2: configurar opções de front-end e back-end

Você pode especificar opções de configuração de cache front-end e back-end em `env.php` ou `di.xml`. Esta tarefa é opcional. Se você não especificar opções, o Commerce usará as configurações padrão de front-end e back-end.

`env.php` exemplo:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

Onde:

- `<frontend_type>` — O tipo de cache de front-end de baixo nível. Especifique um nome de classe compatível com `Zend\Cache\Core`.
Se omitido, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) será usado.

- `<frontend_option>`, `<frontend_option_value>` — O nome e o valor das opções que a estrutura Commerce transmite como uma matriz associativa para o cache de front-end na criação.

- `<backend_type>` — O tipo de cache de back-end de baixo nível. Você pode especificar:
   - **Modern Symfony Cache (2.4.9+, recomendado)**: nomes simplificados como `redis`, `valkey` ou `file`
   - **Herdado (baseado em Zend)**: nome de classe completo compatível com `Zend_Cache_Backend` que implementa `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>` — O nome e o valor das opções que a estrutura Commerce passa como uma matriz associativa para o cache de back-end na criação.

>[!NOTE]
>
>**Implementação herdada vs. moderna:**
>
>- **Herdado (Zend-based)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Moderno (Symfony Cache)**: `'backend' => 'redis'` (recomendado para o Commerce 2.4.9+)
>
>A implementação moderna do Symfony Cache oferece melhor desempenho através da conformidade com PSR-6, serialização Igbinary, compactação gzip, scripts Lua e conexões persistentes.

Consulte a [documentação do Laminas](https://docs.laminas.dev/) para ver as opções baseadas em Zend. Para obter a configuração do Symfony Cache, consulte os artigos [Redis](redis-pg-cache.md) e [Valkey](valkey-pg-cache.md) nesta documentação.
