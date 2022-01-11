---
title: Gerenciar módulos e extensões
description: Gerencie módulos e extensões Adobe Commerce e Magento Open Source usando a interface de linha de comando e o gerenciador de pacotes do Composer.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Gerenciar módulos e extensões

Contribuição de desenvolvedores para atualizar módulos e extensões especificando suas versões no Adobe Commerce ou no Magento Open Source `composer.json` arquivo. Se você não for um desenvolvedor contribuidor, consulte [Executar uma atualização](../implementation/perform-upgrade.md).

Você pode adicionar uma `require` para `composer.json` ou você pode usar o `composer require` comando como segue:

1. Faça logon no servidor.
1. Alterne para [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Altere para o diretório onde você clonou o aplicativo. Por exemplo,

   ```bash
   cd /var/www/magento2
   ```

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

## Adicione um `require` seção para o arquivo composer.json

1. Abra o `composer.json` em um editor de texto.

1. Adicione um `require` seção.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salve as alterações no `composer.json` e saia do editor de texto.

1. Resolva as dependências e grave as versões exatas no `composer.lock` arquivo.

   ```bash
   composer update
   ```
