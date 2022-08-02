---
title: Cabeçalho X-Frame-Options
description: Use X-Frame-Options para controlar as renderizações de página.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Cabeçalho X-Frame-Options

Ajudar a evitar [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) exploits, adicionamos uma opção para usar a variável [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Cabeçalho da solicitação HTTP em solicitações para a loja.

O `X-Frame-Options` permite especificar se um navegador deve ou não renderizar uma página em um `<frame>`, `<iframe>`ou `<object>` como se segue:

- `DENY`: A página não pode ser exibida em um quadro.
- `SAMEORIGIN`: (padrão) A página pode ser exibida somente em um quadro na mesma origem da própria página.

>[!WARNING]
>
>O `ALLOW-FROM <uri>` A opção foi substituída porque os navegadores compatíveis com o Commerce não são mais compatíveis com ela. Consulte [Compatibilidade do navegador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de segurança, o Adobe recomenda não executar a loja do Commerce em um quadro.

## Implementar `X-Frame-Options`

Defina um valor para `X-Frame-Options` em `<magento_root>/app/etc/env.php`. A seguir, o valor padrão:

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>É mais seguro editar a variável `env.php` do que definir um valor em Admin.

## Verifique sua configuração para `X-Frame-Options`

Para verificar sua configuração, visualize cabeçalhos HTTP em qualquer página de loja. Há várias maneiras de fazer isso, incluindo o uso de um inspetor de navegador da Web.

O exemplo a seguir usa o curl, que pode ser executado de qualquer máquina que possa se conectar ao seu servidor do Commerce pelo protocolo HTTP.

Use o seguinte comando:

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Procure o `X-Frame-Options` nos cabeçalhos.
