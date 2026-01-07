---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# Visão geral

Este projeto inclui várias tarefas do Rake para automatizar vários aspectos do fluxo de trabalho, como gerar dados para resumo de notícias, renderizar arquivos de modelo, otimizar imagens e gerar mapas. Abaixo estão as descrições e diretrizes de uso para cada tarefa do Rake definida no Rakefile.

## Tarefas do Rake

### `render`

Renderiza os arquivos de modelo no diretório `_jekyll/templates` com dados de `_jekyll/_data/`. O resultado será encontrado no diretório `help/includes/templated`. Essa tarefa mantém automaticamente relações de inclusão e carimbos de data e hora após a renderização.

**Uso:**

```sh
rake render
```

**O que ele faz:**
- Executa o script de renderização para gerar arquivos de modelo
- Executa `includes:maintain_all` para atualizar relações de inclusão e carimbos de data/hora
- Garante que todos os metadados de inclusão estejam atualizados após a renderização

### `image_optim`

Otimiza imagens em arquivos não confirmados modificados. Para outras imagens, use o argumento `path` para especificar o diretório ou arquivo.

**Uso:**

```sh
rake image_optim
```

**Com argumento `path`:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Gera dados para um resumo de notícias. O período padrão é desde a última atualização. Você pode especificar um ponto diferente usando o argumento `since`.

**Uso:**

```sh
rake whatsnew
```

**Com argumento `since`:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Gera dados para um resumo de notícias em Práticas recomendadas. O período padrão é desde a última atualização. Você pode especificar um ponto diferente usando o argumento `since`.

**Uso:**

```sh
rake whatsnew_bp
```

**Com argumento `since`:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Gera um mapa de regiões do Azure. O arquivo de dados de entrada deve ser colocado em `_jekyll/tmp/azure-regions.json`. O resultado será encontrado em `_jekyll/tmp/azure-regions.svg`. Observe que você precisa do Python, [PyGMT](https://www.pygmt.org/latest/install.html) e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) instalados.

**Uso:**

```sh
rake azure_regions
```

### `get_released_versions`

Obtém as 10 últimas versões lançadas do repositório `magento/magento2`. Exige que a [CLI do GitHub](https://cli.github.com/) seja instalada e autenticada.

**Uso:**

```sh
rake get_released_versions
```

**Saída:** gera `tmp/core-release.txt` com nomes e datas de marcas de versão.

### `first_merge_date`

Obtém a data da primeira mesclagem em uma ramificação especificada. Exige que a [CLI do GitHub](https://cli.github.com/) seja instalada e autenticada.

**Uso:**

```sh
rake first_merge_date base=develop
```

**Argumentos:**

- `base` (obrigatório): o nome da ramificação de destino para verificar mesclagens.

### `includes:maintain_relationships`

Descobre e atualiza o arquivo `include-relationships.yml` examinando todos os arquivos de marcação no diretório `help` para instruções de inclusão usando o padrão `{{$include /help/_includes/filename.md}}`. Essa tarefa mantém automaticamente as relações entre os arquivos de conteúdo principal e seus arquivos incluídos.

**Uso:**

```sh
rake includes:maintain_relationships
```

**O que ele faz:**
- Lê a lista de arquivos de inclusão existentes no diretório `help/_includes`
- Pesquisa em todos os arquivos de marcação principais para encontrar quais fazem referência a cada um deles
- Usa o padrão `{{$include /help/_includes/filename.md}}` para identificar referências
- Atualiza o arquivo `include-relationships.yml` com relações descobertas
- Fornece um resumo das alterações feitas e identifica inclusões sem referência

### `includes:maintain_timestamps`

Mantém os carimbos de data e hora de inclusão, adicionando os carimbos de data e hora de alteração de arquivo de inclusão mais recentes aos arquivos principais. Esta tarefa lê o arquivo `include-relationships.yml`, verifica o histórico do Git para cada arquivo de inclusão e adiciona ou atualiza carimbos de data/hora ao final dos arquivos principais.

**Uso:**

```sh
rake includes:maintain_timestamps
```

**O que ele faz:**
- As cargas incluem relações de `include-relationships.yml`
- Para cada arquivo principal, o encontra a data de confirmação do Git mais recente entre os arquivos de inclusão
- Adiciona ou atualiza comentários do HTML com carimbos de data e hora no final dos arquivos principais
- Usa o formato: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Fornece saída detalhada mostrando quais arquivos de inclusão foram verificados e seus carimbos de data e hora

**Exemplo de saída:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Uma tarefa de conveniência que executa `includes:maintain_relationships` e `includes:maintain_timestamps` em sequência. Essa é a maneira recomendada de manter relações de inclusão e carimbos de data e hora.

**Uso:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Localiza arquivos de inclusão no diretório `help/_includes` que não são referenciados por nenhum arquivo de marcação. Isso ajuda a identificar arquivos de inclusão órfãos que podem ser removidos com segurança.

**Uso:**

```sh
rake unused_includes
```

## Listando tarefas disponíveis

Para ver todas as tarefas do rake disponíveis com suas descrições, use:

```sh
rake --tasks
```

Para obter informações mais detalhadas sobre uma tarefa específica, use:

```sh
rake -T [task_name]
```

## Incluir tarefas de gerenciamento

Todas as tarefas relacionadas à inclusão são organizadas no namespace `includes` para melhor organização:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Incluir formato de arquivo de relacionamentos

O arquivo `include-relationships.yml` rastreia as relações entre os arquivos de conteúdo principal e seus arquivos incluídos. Este arquivo é mantido automaticamente pela tarefa do rake `maintain_include_relationships`, que descobre relações lendo arquivos de inclusão existentes e localizando arquivos principais que fazem referência a eles.

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

**Incluir formato da instrução:**
Os arquivos de conteúdo principal usam a seguinte sintaxe para incluir outros arquivos:

```markdown
{{$include /help/_includes/filename.md}}
```

## Pré-requisitos

- Ruby e Bundler instalados.
- Gems necessárias especificadas no Gemfile (as dependências principais são fornecidas por `adobe-comdox-exl-rake-tasks`).
- [CLI do GitHub](https://cli.github.com/) para as tarefas `get_released_versions` e `first_merge_date`.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html), e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) para a tarefa `azure_regions`.

## Configuração

1. Instale os gems necessários:

   ```sh
   bundle install
   ```

2. Verifique se o Python, PyGMT e pdf2svg estão instalados para a tarefa `azure_regions`. Para obter mais detalhes sobre a instalação, consulte a documentação nos comentários em [_scripts/azure_regions.py](_scripts/azure_regions.py).
