---
title: Comandos comuns
description: Visualize uma amostra de comandos e uso comuns da CLI do Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# Comandos comuns

O seguinte resume alguns dos comandos disponíveis.

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

Os comandos são mostrados apenas na forma de resumo; para obter mais informações sobre um comando, clique no link na coluna Comando .

| Comando | Descrição |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gerencia o cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gerencia os indexadores |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Executa trabalhos de cron do Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compila todos os proxies e fábricas inexistentes; O e pré-compila definições de classe, informações de herança e definições de plug-in para uma loja e site. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dependências do módulo, dependências circulares e dependências da estrutura do Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Cria um dicionário de tradução ou um pacote de tradução |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Implanta arquivos de visualização estáticos |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Cria CSS de MENOS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Executa testes automatizados |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Atualize seus arquivos XML de layout para corresponder à nova folha de estilos XSLT (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Gere dados para usar em testes de desempenho. |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | Instala os dados de amostra opcionais após a instalação do aplicativo Commerce.<br><br>Para obter mais detalhes sobre dados de amostra, consulte [Dados de amostra opcionais](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gerencia configurações de back-end |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | Cria/edita/desbloqueia usuários administradores. |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | Ativa/desativa as dicas do modelo do desenvolvedor. |

## Argumentos comuns

Os argumentos a seguir são comuns a todos os comandos. Esses comandos podem ser executados antes ou depois da instalação do software Commerce:

| Versão longa | Versão curta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtenha ajuda para qualquer comando. Por exemplo, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sem saída. |
| `--no-interaction` | `-n` | Sem perguntas interativas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nível de verbosidade. Por exemplo, `--verbose=3` ou `-vvv` exibe a verbosidade de depuração, que é a saída mais detalhada. O padrão é `--verbose=1` ou `-v`. |
| `--version` | `-V` | Exibir esta versão do aplicativo |
| `--ansi` | n/d | Forçar saída ANSI |
| `--no-ansi` | n/d | Desativar saída ANSI |
