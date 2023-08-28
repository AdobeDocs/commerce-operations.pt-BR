---
title: Desenvolvimento do compositor
description: Saiba mais sobre como desenvolver módulos do Composer no local, no diretório "vendor/".
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Desenvolvimento do compositor

Este tópico descreve a abordagem recomendada para desenvolver módulos do Composer no local (como repositórios Git na `vendor/` diretório) e adicionando esses módulos ao seu projeto Git principal.

>[!NOTE]
>
>As presentes orientações aplicam-se [arquitetura de referência global (GRA)](../overview.md) projetos.

## Preparar uma ramificação de desenvolvimento

1. Crie ou confira a ramificação de desenvolvimento no repositório Git principal.
1. Exigir versões de desenvolvimento para cada módulo que você mantém.

   Neste exemplo, cada ramificação no repositório Git principal representa uma versão do pacote do Composer. A convenção de nomenclatura recomendada para versões do Composer neste cenário é `dev-` seguido pelo nome da filial. Por exemplo:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Se outro pacote do Composer exigir uma versão específica de um módulo (por exemplo, `client/module-example 1.0.12`), instale-o com um alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Para o `qa` ramificação, substituir `dev-develop` com `dev-qa`.

## Converter pacotes em repositórios Git

Por padrão, os pacotes não contêm um `.git/` diretório. O Composer pode retirar pacotes do Git em vez de usar os pacotes do Composer pré-criados. A vantagem dessa abordagem é que você pode modificar facilmente os pacotes durante o desenvolvimento.

1. Remova o módulo do `vendor/` diretório.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Reinstale o módulo usando o [fonte Git especificada](#prepare-a-development-branch).

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

Atualize seu repositório Git principal modificando o `composer.lock` arquivo. Se o módulo for novo, ative-o.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
