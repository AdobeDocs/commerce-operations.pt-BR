---
title: Exibir ou alterar o URI do administrador
description: Siga estas etapas para visualizar e modificar o URI do seu aplicativo Adobe Commerce ou Magento Open Source Admin.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Exibir ou alterar o URI do administrador

Antes de executar este comando, é necessário [Criar ou atualizar a configuração de implantação](deployment.md).

## Exibir o URI do administrador

Esta seção discute como usar a linha de comando para exibir a variável [Administrador](https://glossary.magento.com/admin) Identificador de recurso uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

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
