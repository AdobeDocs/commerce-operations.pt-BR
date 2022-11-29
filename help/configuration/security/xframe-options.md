---
title: Cabeçalho X-Frame-Options
description: Use X-Frame-Options para controlar as renderizações de página.
source-git-commit: db696b8ca501d128db655c5ebb161c654c6378a7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Cabeçalho X-Frame-Options

Ajudar a evitar [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) exploits, adicionamos uma opção para usar a variável [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Cabeçalho da solicitação HTTP em solicitações para a loja.

O `X-Frame-Options` permite especificar se um navegador deve ter permissão para renderizar uma página em um `<frame>`, `<iframe>`ou `<object>` como se segue:

- `DENY`: A página não pode ser exibida em um quadro.
- `SAMEORIGIN`: (padrão) A página pode ser exibida somente em um quadro na mesma origem da própria página.

>[!WARNING]
>
>O `ALLOW-FROM <uri>` A opção foi substituída porque os navegadores compatíveis com o Commerce não são mais compatíveis com ela. Consulte [Compatibilidade do navegador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de segurança, o Adobe recomenda não executar a loja do Commerce em um quadro.

## Implementar `X-Frame-Options`

Defina um valor para `X-Frame-Options` em `<project-root>/app/etc/env.php`. O valor padrão é definido da seguinte maneira:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Reimplante para qualquer alteração no `env.php` para entrar em vigor.

>[!TIP]
>
>É mais seguro editar a variável `env.php` do que definir um valor em Admin.

## Verifique sua configuração para `X-Frame-Options`

Para verificar sua configuração, visualize os cabeçalhos HTTP em qualquer página de loja. Há várias maneiras de fazer isso, incluindo o uso de um inspetor de navegador da Web.

O exemplo a seguir usa o curl, que pode ser executado de qualquer máquina que possa se conectar ao seu servidor do Commerce pelo protocolo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Procure o `X-Frame-Options` nos cabeçalhos.
