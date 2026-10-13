---
title: Gerenciar módulos e extensões (desenvolvedor)
description: Gerencie módulos e extensões do Adobe Commerce usando a interface de linha de comando e o gerenciador de pacotes do Composer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%
---
# Gerenciar módulos e extensões

Os desenvolvedores colaboradores atualizam módulos e extensões especificando suas versões no arquivo `composer.json` do Adobe Commerce. Se você não for um desenvolvedor contribuinte, consulte [Fazer uma atualização](../implementation/perform-upgrade.md).

Você pode adicionar uma seção `require` ao arquivo `composer.json` ou usar o comando `composer require` da seguinte maneira:

{{$include /help/_includes/server-login.md}}

Você tem as seguintes opções:

## Obter versões de módulo disponíveis

Uso do comando:

```shell
composer show --all <vendor>/<name>
```

Por exemplo:

```shell
composer show --all example/module
```

## Usar o comando `composer require`

Uso do comando:

```shell
composer require <vendor>/<name>:<version>
```

Por exemplo:

```shell
composer require example/module:1.0.0
```

Aguarde enquanto o Composer atualiza as dependências e instala o módulo.

## Adicionar uma seção `require` ao arquivo composer.json

1. Abra o `composer.json` em um editor de texto.

1. Adicione uma seção `require`.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salve as alterações no arquivo `composer.json` e saia do editor de texto.

1. Resolva as dependências e grave versões exatas no arquivo `composer.lock`.

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
