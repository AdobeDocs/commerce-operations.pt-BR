---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---
# Visão geral

Este projeto usa tarefas do Rake para automatizar partes do fluxo de trabalho de documentação. A maioria das tarefas é compartilhada entre repositórios de documentos ExL Commerce e vem da gem [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks). Algumas tarefas abaixo são específicas para esse repositório.

**Para tarefas comuns (renderização de modelos, gerenciamento de inclusões, otimização/auditoria de imagens, geração do resumo Novidades), consulte o [ADME de tarefas do adobe-comdox-exl-rake](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md).**

> Todos os comandos `bundle exec rake` abaixo devem ser executados de dentro do diretório `_jekyll/`, já que é onde o Gemfile e o Rakefile vivem.

## Tarefas do Rake específicas do repositório

### `whatsnew_bp`

Gera dados para um resumo de notícias em Práticas recomendadas. O período padrão é desde a última atualização. Você pode especificar um ponto diferente usando o argumento `since`.

**Uso:**

```sh
bundle exec rake whatsnew_bp
```

**Com argumento `since`:**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `get_released_versions`

Obtém as 10 últimas versões lançadas do repositório `magento/magento2`. Exige que a [CLI do GitHub](https://cli.github.com/) seja instalada e autenticada.

**Uso:**

```sh
bundle exec rake get_released_versions
```

**Saída:** gera `tmp/core-release.txt` com nomes e datas de marcas de versão.

### `first_merge_date`

Obtém a data da primeira mesclagem em uma ramificação especificada. Exige que a [CLI do GitHub](https://cli.github.com/) seja instalada e autenticada.

**Uso:**

```sh
bundle exec rake first_merge_date base=develop
```

**Argumentos:**

- `base` (obrigatório): o nome da ramificação de destino para verificar mesclagens.

## Listando tarefas disponíveis

Para ver todas as tarefas do rake disponíveis com suas descrições, use:

```sh
bundle exec rake --tasks
```

Para obter informações mais detalhadas sobre uma tarefa específica, use:

```sh
bundle exec rake -T [task_name]
```

## Incluir formato de arquivo de relacionamentos

O arquivo `include-relationships.yml` rastreia as relações entre os arquivos de conteúdo principal e seus arquivos incluídos. Este arquivo é mantido automaticamente pela tarefa `includes:maintain_relationships` (consulte o [LEIAME de tarefas do adobe-comdox-exl-rake](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) para uso de tarefas), que descobre relações lendo arquivos de inclusão existentes e localizando arquivos principais que fazem referência a eles.

**Estrutura de arquivo:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Campos:**
- `metadata.last_updated`: carimbo de data/hora da última atualização
- `metadata.total_relationships`: Número total de arquivos principais com inclusões
- `metadata.auto_discovered`: indica que o arquivo foi gerado automaticamente
- `metadata.discovery_date`: Data em que as relações foram descobertas pela primeira vez
- `relationships`: Mapeamento de arquivos principais para seus arquivos incluídos

**Incluir formato de instrução:**
Os arquivos de conteúdo principal usam a seguinte sintaxe para incluir outros arquivos:

```markdown
{{$include /help/_includes/filename.md}}
```

## Pré-requisitos

- Ruby e Bundler instalados.
- Gems necessárias especificadas no Gemfile (tarefas comuns são fornecidas por `adobe-comdox-exl-rake-tasks`; a tarefa `whatsnew` requer adicionalmente `whatsup_github`).
- [CLI do GitHub](https://cli.github.com/) para as tarefas `get_released_versions` e `first_merge_date`.

## Configuração

Instale os gems necessários:

```sh
bundle install
```
