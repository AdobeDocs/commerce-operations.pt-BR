---
title: Tipos de cache
description: Associar frontends de cache a tipos de cache.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Tipos de cache

As etapas a seguir abordam a associação do front-end do cache com um tipo de cache.

## Etapa 1: Definir um front-end de cache

O aplicativo Commerce tem um `default` interface de cache que você pode usar para qualquer [tipo de cache](../cli/manage-cache.md#clean-and-flush-cache-types). Esta seção discute como, opcionalmente, definir um front-end de cache com um nome diferente, o que é preferível se você espera personalizar o front-end.

>[!INFO]
>
>Para usar o `default` tipo de cache, não é necessário modificar `env.php` de todo; você modifica o global do Commerce `di.xml`. Consulte [Opções de cache de baixo nível](cache-options.md).

Você deve especificar um front-end de cache personalizado `app/etc/env.php` ou global do Commerce `app/etc/di.xml`.

O exemplo a seguir mostra como defini-lo no `env.php` , que substitui `di.xml` arquivo:

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Onde `<unique frontend id>` é um nome exclusivo para identificar o front-end e `<cache options>` são opções discutidas nos tópicos específicos de cada tipo de armazenamento em cache (banco de dados, Redis etc.).

## Etapa 2: Configurar o cache

Você pode especificar as opções de configuração de cache de front-end e back-end em `env.php` ou `di.xml`. Essa tarefa é opcional.

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

em que

- `<frontend_type>` é o tipo de cache de front-end de baixo nível. Especifique o nome de uma classe compatível com `Zend\Cache\Core`.
Se você omitir `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) é usada.

- `<frontend_option>`, `<frontend_option_value>` são o nome e o valor das opções que a estrutura do Commerce transmite como uma matriz associativa ao cache de primeiro plano após sua criação.
- `<backend_type>` é o tipo de cache de back-end de baixo nível. Especifique o nome de uma classe compatível com `Zend_Cache_Backend` e que implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` e `<backend_option_value>` são o nome e o valor das opções que a estrutura do Commerce passa como uma matriz associativa para o cache de back-end após sua criação.

Consulte a [Documentação do Laminas](https://docs.laminas.dev/) para obter as informações mais recentes do Zend.
