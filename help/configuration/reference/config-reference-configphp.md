---
title: referência config.php
description: Veja uma lista de valores no arquivo config.php.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---

# referência config.php

O arquivo `config.php` contém as seguintes seções:

| Nome | Descrição |
| --------- | -------------------|
| `i18n` | Todos os dados de tradução em linha. A leitura desta seção não é suportada. |
| `modules` | A lista de módulos habilitados e desabilitados. |
| `scopes` | A lista de lojas, grupos de lojas e sites com informações relacionadas. |
| `system` | As configurações do sistema necessárias para a implantação de conteúdo estático. |
| `themes` | A configuração dos temas instalados. |

## módulos

Contém uma matriz de módulos e seus estados. Se o módulo estiver ativado, o valor será 1. Caso contrário, o valor será 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Saiba mais sobre [Módulos].

## escopos

Contém uma matriz de valores de configuração de escopo. Ele tem os seguintes subnós:

| Nome | Descrição |
| ---------- | -----------------------------------|
| `websites` | Configuração do site |
| `groups` | Armazena a configuração |
| `stores` | Configuração de exibições de loja |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Saiba mais sobre [Escopos do Commerce][scopes].

## sistema

Contém uma matriz de valores de configuração de campo do sistema.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Saiba mais sobre [Configurações específicas do sistema](config-reference-sens.md).

## temas

Contém uma matriz de valores para a configuração do tema.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Saiba mais sobre [Temas].

<!-- link definitions -->

[Módulos]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=pt-BR
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=pt-BR#scope-settings
[Temas]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
