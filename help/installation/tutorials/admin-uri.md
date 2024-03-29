---
title: Exibir ou alterar o URI do administrador
description: Siga estas etapas para exibir e modificar o URI do aplicativo Adobe Commerce ou Magento Open Source Admin.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Exibir ou alterar o URI do administrador

Antes de executar este comando, você deve [Criar ou atualizar a configuração de implantação](deployment.md).

## Exibir o URI do administrador

Esta seção discute como usar a linha de comando para exibir o Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opções de comando:

```bash
bin/magento info:adminuri
```

Um exemplo de resultado é o seguinte:

```terminal
Admin Panel URI: /admin_1wgrah
```

Você também pode exibir o URI do administrador no `<magento_root>/app/etc/env.php`. Segue um trecho:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Alterar o URL do administrador

Para alterar o URI do administrador, use o [`magento setup:config:set`](deployment.md) comando.
