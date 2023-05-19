---
title: Tipos de cache
description: Associar front-ends do cache com tipos de cache.
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Tipos de cache

As etapas a seguir percorrem para associar um front-end de cache a um tipo de cache.

## Etapa 1: definir um front-end de cache

O aplicativo Commerce tem um `default` front-end do cache que pode ser usado para qualquer [tipo de cache](../cli/manage-cache.md#clean-and-flush-cache-types). Esta seção discute como definir opcionalmente um front-end do cache com um nome diferente, o que é preferível se você espera personalizar seu front-end.

>[!INFO]
>
>Para usar o `default` tipo de cache, não é necessário modificar `env.php` de forma alguma; você modifica a configuração global do Commerce `di.xml`. Consulte [Opções de cache de baixo nível](cache-options.md).

Você deve especificar um front-end de cache personalizado `app/etc/env.php` ou global do Commerce `app/etc/di.xml`.

O exemplo a seguir mostra como defini-la na variável `env.php` arquivo, que substitui o `di.xml` arquivo:

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

Onde `<unique frontend id>` é um nome exclusivo para identificar seu front-end e `<cache options>` são opções discutidas nos tópicos específicos para cada tipo de cache (banco de dados, Redis e assim por diante).

## Etapa 2: configurar o cache

Você pode especificar opções de configuração de cache de front-end e back-end no `env.php` ou `di.xml`. Esta tarefa é opcional.

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
Se você omitir `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) é usada.

- `<frontend_option>`, `<frontend_option_value>` são o nome e o valor das opções que a estrutura do Commerce transmite como uma matriz associativa para o cache de front-end após a criação.
- `<backend_type>` é o tipo de cache de back-end de baixo nível. Especifique o nome de uma classe compatível com `Zend_Cache_Backend` e que implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` e `<backend_option_value>` são o nome e o valor das opções que a estrutura do Commerce transmite como uma matriz associativa para o cache de back-end após a criação.

Consulte a [Documentação do Laminas](https://docs.laminas.dev/) para obter as informações mais recentes do Zend.
