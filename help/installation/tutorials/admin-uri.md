---
title: Exibir ou alterar o URI do administrador
description: Siga estas etapas para exibir e modificar o URI do seu aplicativo de Administração do Adobe Commerce.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%
---
# Exibir ou alterar o URI do administrador

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Exibir o URI do administrador

Esta seção discute como usar a linha de comando para exibir o Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) do Administrador.

Opções de comando:

```shell
bin/magento info:adminuri
```

Um exemplo de resultado é o seguinte:

```text
Admin Panel URI: /admin_1wgrah
```

Você também pode exibir o URI do Administrador em `<magento_root>/app/etc/env.php`. Segue um trecho:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Alterar o URL do administrador

Para alterar o URI do Administrador, use o comando [`magento setup:config:set`](deployment.md).
