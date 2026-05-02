---
title: Gerenciar módulos e extensões (desenvolvedor)
description: Gerencie módulos e extensões do Adobe Commerce usando a interface de linha de comando e o gerenciador de pacotes do Composer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
