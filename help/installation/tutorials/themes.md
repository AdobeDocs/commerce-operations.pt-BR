---
title: Desinstalar temas
description: Siga estas etapas para desinstalar um tema do Adobe Commerce.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Desinstalar temas

Antes de usar esse comando, você deve saber o caminho relativo para o tema. Os temas estão localizados em um subdiretório de `<magento_root>/app/design/<area name>`. Você deve especificar o caminho para o tema que começa com a área, ou seja `frontend` (para temas de vitrine) ou `adminhtml` (para temas de Administrador).

Por exemplo, o caminho para o tema Luma fornecido com o Adobe Commerce é `frontend/Magento/luma`.

Para obter mais informações sobre temas, consulte [estrutura de tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Visão geral da desinstalação de temas

Esta seção discute como desinstalar um ou mais temas, incluindo, opcionalmente, o código do tema do sistema de arquivos. Você pode criar backups primeiro para poder restaurar os dados posteriormente.

Este comando desinstala o *somente* temas especificados em `composer.json`; em outras palavras, temas que são fornecidos como pacotes do Composer. Se o tema não for um pacote do Composer, você deverá desinstalá-lo manualmente ao:

* Atualização do `parent` informações do nó em `theme.xml` para remover referências ao tema.
* Removendo código de tema do sistema de arquivos.

  [Mais informações sobre herança de tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Desinstalar temas

Uso do comando:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Onde

* `{theme path}` é o caminho relativo para o tema, começando com o nome da área. Por exemplo, o caminho para o tema em branco fornecido com o Adobe Commerce é `frontend/Magento/blank`.
* `--backup-code` O faz backup da base de código conforme discutido nos parágrafos seguintes.
* `--clear-static-content` limpa geradas [arquivos de visualização estáticos](../../configuration/cli/static-view-file-deployment.md), que é necessário para fazer com que os arquivos de exibição estáticos sejam exibidos corretamente.

O comando executa as seguintes tarefas:

1. Verifica se os caminhos de tema especificados existem; caso contrário, o comando será encerrado.
1. Verifica se o tema é um pacote do Composer; caso contrário, o comando será encerrado.
1. Verifica dependências e encerra o comando se houver dependências não atendidas.

   Para contornar isso, você pode desinstalar todos os temas ao mesmo tempo ou desinstalar o dependendo do tema primeiro.

1. Verifica se o tema não está sendo usado; se estiver sendo usado, o comando será encerrado.
1. Verifica se o tema não é a base do tema virtual; se for a base de um tema virtual, o comando é finalizado.
1. Coloca o armazenamento no modo de manutenção.
1. Se `--backup-code` for especificado, fazer backup da base de código, excluindo a `pub/static`, `pub/media`, e `var` diretórios.

   O nome do arquivo de backup é `var/backups/<timestamp>_filesystem.tgz`

   É possível restaurar backups a qualquer momento usando o [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

1. Remove temas da lista `theme` tabela de banco de dados.
1. Remover temas da base de código usando `composer remove`.
1. Limpa o cache.
1. Limpa classes geradas
1. Se `--clear-static-content` for especificado, limpa [arquivos de visualização estáticos gerados](../../configuration/cli/static-view-file-deployment.md).

Por exemplo, se você tentar desinstalar um tema do qual outro tema depende, a seguinte mensagem será exibida:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Uma alternativa é desinstalar ambos os temas ao mesmo tempo, como segue, fazendo backup da base de código:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Mensagens semelhantes a esta são exibidas:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Para desinstalar um tema Admin, você também deve removê-lo da configuração de injeção de dependência do seu componente, `<component root directory>/etc/di.xml`.
