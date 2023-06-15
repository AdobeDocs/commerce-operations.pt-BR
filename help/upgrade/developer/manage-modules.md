---
title: Gerenciar módulos e extensões (desenvolvedor)
description: Gerencie módulos e extensões Adobe Commerce e Magento Open Source usando a interface de linha de comando e o gerenciador de pacotes do Composer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# Gerenciar módulos e extensões

Os desenvolvedores colaboradores atualizam módulos e extensões especificando suas versões no Adobe Commerce ou no Magento Open Source `composer.json` arquivo. Se você não for um desenvolvedor do contributing, consulte [Executar uma atualização](../implementation/perform-upgrade.md).

Você pode adicionar um `require` para a `composer.json` ou você pode usar o `composer require` comando da seguinte maneira:

{{$include /help/_includes/server-login.md}}

Você tem as seguintes opções:

## Obter versões de módulo disponíveis

Uso do comando:

```bash
composer show --all <vendor>/<name>
```

Por exemplo:

```bash
composer show --all example/module
```

## Use o `composer require` comando

Uso do comando:

```bash
composer require <vendor>/<name>:<version>
```

Por exemplo:

```bash
composer require example/module:1.0.0
```

Aguarde enquanto o Composer atualiza as dependências e instala o módulo.

## Adicionar um `require` seção para o arquivo composer.json

1. Abra o `composer.json` em um editor de texto.

1. Adicionar um `require` seção.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salve as alterações no `composer.json` e saia do editor de texto.

1. Resolva as dependências e grave versões exatas no `composer.lock` arquivo.

   ```bash
   composer update
   ```
