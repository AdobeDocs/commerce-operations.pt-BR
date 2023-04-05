---
title: Exibir ou alterar o URI do administrador
description: Siga estas etapas para visualizar e modificar o URI do seu aplicativo Adobe Commerce ou Magento Open Source Admin.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Exibir ou alterar o URI do administrador

Antes de executar este comando, é necessário [Criar ou atualizar a configuração de implantação](deployment.md).

## Exibir o URI do administrador

Esta seção discute como usar a linha de comando para exibir o Identificador de Recurso Uniforme de Administrador ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opções de comando:

```bash
bin/magento info:adminuri
```

Um exemplo de resultado é o seguinte:

```terminal
Admin Panel URI: /admin_1wgrah
```

Você também pode visualizar o URI do administrador em `<magento_root>/app/etc/env.php`. Um trecho segue:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Alterar o URL de administrador

Para alterar o URI do administrador, use o [`magento setup:config:set`](deployment.md) comando.
