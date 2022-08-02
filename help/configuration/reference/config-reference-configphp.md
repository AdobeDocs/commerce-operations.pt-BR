---
title: referência config.php
description: Consulte uma lista de valores no arquivo config.php.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# referência config.php

O `config.php` O arquivo contém as seguintes seções:

| Nome | Descrição |
| --------- | -------------------|
| `i18n` | Todos os dados de tradução em linha. A leitura desta seção não é suportada. |
| `modules` | A lista de módulos ativados e desativados. |
| `scopes` | A lista de lojas, grupos de lojas e sites com informações relacionadas. |
| `system` | As configurações do sistema necessárias para a implantação de conteúdo estático. |
| `themes` | A configuração de temas instalados. |

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
| `stores` | Configuração de visualizações de loja |

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

Saiba mais sobre [Escopos de Comércio][scopes].

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

Contém uma matriz de valores para configuração de tema.

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

[Módulos]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[Temas]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
