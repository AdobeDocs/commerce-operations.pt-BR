---
title: Configurar front-ends e tipos de cache
description: Saiba como definir front-ends de cache e associá-los a tipos de cache no Adobe Commerce. Descubra a sintaxe de configuração para env.php.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%
---
# Configurar front-ends e tipos de cache

Um front-end do cache conecta os tipos de cache do Commerce ao armazenamento em cache. Você pode definir vários front-ends e atribuir tipos específicos de cache a cada front-end.

>[!BEGINSHADEBOX]

Use a seguinte relação para determinar onde um tipo de cache armazena seus dados:

tipo de cache → front-end do cache → back-end do cache

>[!ENDSHADEBOX]

Para obter uma visão geral da arquitetura de cache do Commerce, consulte [Visão geral e opções de configuração de cache](caching-overview.md).

>[!NOTE]
>
>Para o Adobe Commerce na infraestrutura em nuvem, use a [Configuração de implantação da nuvem](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) descrita no guia de nuvem. Não edite `app/etc/env.php` diretamente. As ferramentas de implantação geram esse arquivo e podem substituir alterações manuais.

## Usar o front-end padrão

O Commerce fornece um front-end padrão que pode ser usado por todos os tipos de cache.

Na maioria dos casos, não é necessário definir um front-end personalizado. Se todos os tipos de cache puderem usar as mesmas opções de back-end e back-end, use o front-end padrão e configure seu back-end. Consulte [Opções de back-end do cache](cache-options.md) para obter a configuração específica de back-end.

Para versões do Adobe Commerce anteriores a 2.4.9, o front-end padrão usa a implementação de cache herdada baseada no Zend. O front-end `Magento\Framework\Cache\Core` estende `Zend_Cache_Core`. Adobe Commerce 2.4.9 e posteriores usam a implementação moderna do Symfony. Consulte [Opções de back-end do cache](cache-options.md) para obter orientações específicas da versão.

## Definir um front-end personalizado

Use um front-end de cache personalizado quando um ou mais tipos de cache precisarem de configurações de back-end diferentes das do front-end padrão.

Para implantações locais, defina o front-end em `app/etc/env.php`. Em seguida, atribua um ou mais tipos de cache a ele:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

Onde:

- `<frontend-id>` é o identificador exclusivo do front-end, como `default` ou `page_cache`.
- `<backend-type>` identifica a infraestrutura usada pelo front-end. O valor compatível depende da versão do Adobe Commerce e do back-end selecionado.
- `backend_options` contém opções para o back-end selecionado.
- `<cache-type-id>` é um tipo de cache do Commerce, como `config`, `layout`, `block_html` ou `full_page`.


Para obter exemplos de tipos de back-end, opções com suporte e configurações específicas de versão, consulte [Opções de back-end de cache](cache-options.md).

## Atribuir um tipo de cache a um front-end

A configuração `type` mapeia um tipo de cache para um front-end:

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

Onde:

- `<frontend_type>` — O tipo de cache de front-end de baixo nível. Especifique um nome de classe compatível com `Zend_Cache_Core`.
Se omitido, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) será usado.

- `<frontend_option>`, `<frontend_option_value>` — O nome e o valor das opções que a estrutura Commerce transmite como uma matriz associativa para o cache de front-end na criação.

- `<backend_type>` — O tipo de cache de back-end de baixo nível. Você pode especificar:
  - **Symfony Cache (2.4.9+, recomendado)**: nomes simplificados como `valkey` ou `file`
  - **Baseado em Zend**: nome de classe completo compatível com `Zend_Cache_Backend` que implementa `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>` — O nome e o valor das opções que a estrutura Commerce passa como uma matriz associativa para o cache de back-end na criação.

>[!NOTE]
>
>Para formatos de valor de back-end, como nomes de classe baseados em Zend versus nomes simplificados do Symfony Cache, como `valkey` ou `file`, consulte [Opções de back-end do cache](cache-options.md).

>[!MORELIKETHIS]
>
>- [Configuração de cache L2 para otimização de desempenho](level-two-cache.md)
>- [Gerenciar o cache](../cli/manage-cache.md)
