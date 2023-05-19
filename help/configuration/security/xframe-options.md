---
title: Cabeçalho X-Frame-Options
description: Use X-Frame-Options para controlar a renderização da página.
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Cabeçalho X-Frame-Options

Para ajudar a evitar [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) explorações, adicionamos uma opção para usar o [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Cabeçalho de solicitação HTTP em solicitações para a loja.

A variável `X-Frame-Options` cabeçalho permite especificar se um navegador deve ter permissão para renderizar uma página em um `<frame>`, `<iframe>`ou `<object>` do seguinte modo:

- `DENY`: a página não pode ser exibida em um quadro.
- `SAMEORIGIN`: (padrão) a página pode ser exibida somente em um quadro na mesma origem da própria página.

>[!WARNING]
>
>A variável `ALLOW-FROM <uri>` A opção foi descontinuada porque os navegadores compatíveis com o Commerce não oferecem mais suporte para ela. Consulte [Compatibilidade do navegador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de segurança, a Adobe recomenda não executar a loja de Commerce em um quadro.

## Implementar `X-Frame-Options`

Definir um valor para `X-Frame-Options` in `<project-root>/app/etc/env.php`. O valor padrão é definido da seguinte maneira:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Reimplante para qualquer alteração no `env.php` que entrará em vigor.

>[!TIP]
>
>É mais seguro editar as `env.php` que é para definir um valor no Administrador.

## Verifique sua configuração para `X-Frame-Options`

Para verificar sua configuração, visualize os cabeçalhos HTTP em qualquer página de vitrine. Há várias maneiras de fazer isso, incluindo o uso de um inspetor de navegador da Web.

O exemplo a seguir usa curl, que pode ser executado em qualquer máquina que possa se conectar ao servidor do Commerce por meio do protocolo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Procure o `X-Frame-Options` nos cabeçalhos.
