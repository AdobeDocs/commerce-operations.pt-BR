---
title: Desenvolvimento do compositor
description: Saiba mais sobre como desenvolver módulos do Composer no local, no diretório "vendor/".
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Desenvolvimento do compositor

Este tópico descreve a abordagem recomendada para desenvolver módulos do Composer no local (como repositórios Git no diretório `vendor/`) e adicionar esses módulos ao projeto Git principal.

>[!NOTE]
>
>Estas diretrizes aplicam-se principalmente aos projetos da [arquitetura de referência global (GRA)](../overview.md).

## Preparar uma ramificação de desenvolvimento

1. Crie ou confira a ramificação de desenvolvimento no repositório Git principal.
1. Exigir versões de desenvolvimento para cada módulo que você mantém.

   Neste exemplo, cada ramificação no repositório Git principal representa uma versão do pacote do Composer. A convenção de nomenclatura recomendada para versões do Composer neste cenário é `dev-` seguida do nome da ramificação. Por exemplo:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Se outro pacote do Composer exigir uma versão específica de um módulo (por exemplo, `client/module-example 1.0.12`), instale-o com um alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Para a ramificação `qa`, substitua `dev-develop` por `dev-qa`.

## Converter pacotes em repositórios Git

Por padrão, os pacotes não contêm um diretório `.git/`. O Composer pode retirar pacotes do Git em vez de usar os pacotes do Composer pré-criados. A vantagem dessa abordagem é que você pode modificar facilmente os pacotes durante o desenvolvimento.

1. Remova o módulo do diretório `vendor/`.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Reinstale o módulo usando a [origem Git especificada](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Verifique se o pacote do Composer agora é um repositório Git:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Para converter em lote vários módulos em repositórios Git (por exemplo, módulos &quot;cliente&quot;):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Iniciar desenvolvimento

1. Criar ou fazer check-out de uma ramificação de recurso/trabalho. O exemplo a seguir mostra uma ramificação com o mesmo nome de um tíquete Jira.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Depois de alterar ramificações em um módulo, consulte as alterações liberando o cache do Adobe Commerce e o conteúdo estático.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Atualize o projeto principal com seu desenvolvimento

Atualize seu repositório Git principal modificando o arquivo `composer.lock`. Se o módulo for novo, ative-o.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
