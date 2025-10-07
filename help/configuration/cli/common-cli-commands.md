---
title: Comandos comuns
description: Saiba mais sobre comandos comuns da CLI do Adobe Commerce e seus exemplos de uso. Descubra as ferramentas essenciais de linha de comando para desenvolvimento e administração.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Comandos comuns

Veja a seguir um resumo de alguns dos comandos disponíveis.

**Para exibir uma lista completa de comandos**:

```bash
bin/magento list
```

Exemplo de comando de ajuda:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Os comandos são exibidos somente na forma de resumo; para obter mais informações sobre um comando, clique no link na coluna Comando.

| Comando | Descrição |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gerencia o cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gerencia os indexadores |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Executa trabalhos cron do Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compila todos os proxies e fábricas não existentes e pré-compila definições de classe, informações de herança e definições de plug-in para uma loja e um site. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dependências de módulo, dependências circulares e dependências de estrutura do Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Cria um dicionário de tradução ou um pacote de tradução |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Implanta arquivos de visualização estáticos |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Cria CSS a partir de MENOS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Executa testes automáticos |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Atualize seus arquivos XML de layout para corresponder à nova folha de estilos XSLT (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Gerar dados para usar em testes de desempenho. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Instala dados de amostra opcionais após a instalação do aplicativo Commerce.<br><br>Para obter mais detalhes sobre dados de exemplo, consulte [Dados de exemplo opcionais](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gerencia configurações de backend |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Cria/edita/desbloqueia usuários administradores. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Habilita/desabilita as dicas do modelo de desenvolvedor. |

## Argumentos comuns

Os argumentos a seguir são comuns a [todos os comandos](/help/tools/reference/commerce-on-premises.md). Esses comandos podem ser executados antes ou depois que o software Commerce é instalado:

| Versão longa | Versão curta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtenha ajuda para qualquer comando. Por exemplo, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sem saída. |
| `--no-interaction` | `-n` | Sem perguntas interativas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nível de detalhamento. Por exemplo, `--verbose=3` ou `-vvv` exibe o detalhamento de depuração, que é a saída mais detalhada. O padrão é `--verbose=1` ou `-v`. |
| `--version` | `-V` | Exibir esta versão do aplicativo |
| `--ansi` | n/d | Forçar saída ANSI |
| `--no-ansi` | n/d | Desabilitar saída ANSI |
