---
title: Tipos de cache
description: Saiba como associar front-ends de cache a tipos de cache no Adobe Commerce. Descubra as técnicas de configuração e gerenciamento de cache.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Tipos de cache

As etapas a seguir percorrem para associar um front-end de cache a um tipo de cache.

## Etapa 1: definir um front-end de cache

O aplicativo Commerce tem um front-end de cache `default` que pode ser usado para qualquer [tipo de cache](../cli/manage-cache.md#clean-and-flush-cache-types). Esta seção discute como definir opcionalmente um front-end do cache com um nome diferente, o que é preferível se você espera personalizar seu front-end.

>[!INFO]
>
>Para usar o tipo de cache `default`, não é necessário modificar `env.php`; você modifica o `di.xml` global da Commerce. Consulte [Opções de cache de baixo nível](cache-options.md).

Você deve especificar um front-end de cache personalizado `app/etc/env.php` ou o `app/etc/di.xml` global da Commerce.

O exemplo a seguir mostra como defini-lo no arquivo `env.php`, que substitui o arquivo `di.xml`:

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

Onde `<unique frontend id>` é um nome exclusivo para identificar seu front-end e `<cache options>` são opções discutidas nos tópicos específicos para cada tipo de armazenamento em cache (banco de dados, Redis, etc).

## Etapa 2: configurar o cache

Você pode especificar opções de configuração de cache front-end e back-end em `env.php` ou `di.xml`. Esta tarefa é opcional.

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

onde

- `<frontend_type>` é o tipo de cache de front-end de baixo nível. Especifique o nome de uma classe compatível com `Zend\Cache\Core`.
Se você omitir `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) será usado.

- `<frontend_option>`, `<frontend_option_value>` são o nome e o valor das opções que a estrutura do Commerce transmite como uma matriz associativa para o cache de front-end após sua criação.
- `<backend_type>` é o tipo de cache back-end de nível baixo. Especifique o nome de uma classe compatível com `Zend_Cache_Backend` e que implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` e `<backend_option_value>` são o nome e o valor das opções que a estrutura Commerce transmite como uma matriz associativa para o cache de back-end após sua criação.

Consulte a [documentação do Laminas](https://docs.laminas.dev/) para obter as informações mais recentes do Zend.
