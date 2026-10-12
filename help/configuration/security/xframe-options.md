---
title: Evitar explorações de clickjacking
description: Evite explorações de clickjacking usando o cabeçalho "X-Frame-Options" para controlar as renderizações da página.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
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
source-wordcount: '234'
ht-degree: 0%
---
# Evitar explorações de clickjacking

Evite explorações de [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) ao incluir o cabeçalho de solicitação HTTP [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) em solicitações para sua vitrine.

O cabeçalho `X-Frame-Options` permite especificar se um navegador tem permissão para renderizar uma página em um `<frame>`, `<iframe>` ou `<object>` da seguinte maneira:

- `DENY`: a página não pode ser exibida em um quadro.
- `SAMEORIGIN`: (padrão) a página pode ser exibida somente em um quadro na mesma origem da própria página.

>[!WARNING]
>
>A opção `ALLOW-FROM <uri>` foi descontinuada porque os navegadores com suporte para Commerce não oferecem mais suporte a ela. Consulte [Compatibilidade do navegador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de segurança, a Adobe recomenda não executar a loja da Commerce em um quadro.

## Implementar o `X-Frame-Options`

Defina um valor para `X-Frame-Options` em `<project-root>/app/etc/env.php`. O valor padrão é definido da seguinte maneira:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Reimplante para que qualquer alteração no arquivo `env.php` entre em vigor.

>[!TIP]
>
>Editar o arquivo `env.php` é mais seguro do que definir um valor no Administrador.

## Verifique sua configuração para `X-Frame-Options`

Para verificar sua configuração, visualize os cabeçalhos HTTP em qualquer página de vitrine. Há várias maneiras de fazer isso, incluindo o uso de um inspetor de navegador da Web.

O exemplo a seguir usa curl, que pode ser executado de qualquer máquina que possa se conectar ao servidor do Commerce pelo protocolo HTTP.

```shell
curl -I -v --location-trusted '<storefront-URL>'
```

Procure o valor `X-Frame-Options` nos cabeçalhos.
