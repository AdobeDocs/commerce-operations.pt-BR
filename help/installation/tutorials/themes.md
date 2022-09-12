---
title: Desinstalar temas
description: Siga estas etapas para desinstalar um tema Adobe Commerce ou Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Desinstalar temas

Antes de usar este comando, você deve saber o caminho relativo para seu tema. Os temas estão localizados em um subdiretório de `<magento_root>/app/design/<area name>`. Você deve especificar o caminho para o tema começando pela área, que é `frontend` (para temas de vitrine) ou `adminhtml` para [Administrador](https://glossary.magento.com/magento-admin) temas).

Por exemplo, o caminho para o Luma [tema](https://glossary.magento.com/theme) fornecido com Adobe Commerce e Magento Open Source `frontend/Magento/luma`.

Para obter mais informações sobre temas, consulte [estrutura de temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Visão geral da desinstalação de temas

Esta seção discute como desinstalar um ou mais temas, incluindo o código de temas do sistema de arquivos. Você pode criar backups primeiro para restaurar os dados posteriormente.

Este comando desinstala *only* temas especificados em `composer.json`; em outras palavras, temas fornecidos como [Composer](https://glossary.magento.com/composer) pacotes. Se o tema não for um pacote Composer, é necessário desinstalá-lo manualmente:

* Atualização do `parent` informações do nó no `theme.xml` para remover referências ao tema.
* Removendo o código do tema do sistema de arquivos.

   [Mais informações sobre herança de tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Desinstalar temas

Uso do comando:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Onde

* `{theme path}` é o caminho relativo para o tema, começando com o nome da área. Por exemplo, o caminho para o tema em branco fornecido com Adobe Commerce e Magento Open Source é `frontend/Magento/blank`.
* `--backup-code` faz o backup da base de código, conforme discutido nos parágrafos a seguir.
* `--clear-static-content` cleans gerados [arquivos de visualização estática](../../configuration/cli/static-view-file-deployment.md), que é necessário para fazer com que os arquivos de visualização estáticos sejam exibidos corretamente.

O comando executa as seguintes tarefas:

1. Verifica se os caminhos de temas especificados existem; caso contrário, o comando será encerrado.
1. Verifica se o tema é um pacote Composer; caso contrário, o comando será encerrado.
1. Verifica as dependências e encerra o comando se houver dependências não atendidas.

   Para contornar isso, é possível desinstalar todos os temas ao mesmo tempo ou desinstalar a dependendo do tema primeiro.

1. Verifica se o tema não está a ser utilizado; se estiver sendo usado, o comando será encerrado.
1. Verifica se o tema não é a base do tema virtual; se for a base de um tema virtual, o comando será encerrado.
1. Coloca a loja no modo de manutenção.
1. If `--backup-code` for especificado, faça backup da base de código, excluindo o `pub/static`, `pub/media`e `var` diretórios.

   O nome do arquivo de backup é `var/backups/<timestamp>_filesystem.tgz`

   Você pode restaurar os backups a qualquer momento usando o [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

1. Remove temas da `theme` tabela de banco de dados.
1. Remover temas da base de código usando `composer remove`.
1. Limpa o [cache](https://glossary.magento.com/cache).
1. Limpa classes geradas
1. If `--clear-static-content` é especificado, limpa [arquivos de visualização estática gerados](../../configuration/cli/static-view-file-deployment.md).

Por exemplo, se você tentar desinstalar um tema do qual outro tema dependerá, a seguinte mensagem será exibida:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Uma alternativa é desinstalar ambos os temas ao mesmo tempo, da seguinte maneira, fazendo o backup da base de código:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Mensagens semelhantes à seguinte exibição:

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
>Para desinstalar um [Administrador](https://glossary.magento.com/admin) tema, você também deve removê-lo do [injeção de dependência](https://glossary.magento.com/dependency-injection) configuração, `<component root directory>/etc/di.xml`.
