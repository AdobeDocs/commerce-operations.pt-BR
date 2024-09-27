---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Visão geral

Este projeto inclui várias tarefas do Rake para automatizar vários aspectos do fluxo de trabalho, como gerar dados para resumo de notícias, renderizar arquivos de modelo, otimizar imagens e gerar mapas. Abaixo estão as descrições e diretrizes de uso para cada tarefa do Rake definida no Rakefile.

## Tarefas do Rake

### `render`

Renderiza os arquivos de modelo no diretório `_jekyll/templates` com dados de `_jekyll/_data/`. O resultado será encontrado no diretório `help/includes/templated`.

**Uso:**

```sh
rake render
```

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

## Pré-requisitos

- Ruby e Bundler instalados.
- Gems necessárias especificadas no arquivo Gem.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html), e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) para a tarefa `azure_regions`.

## Configuração

1. Instale os gems necessários:

   ```sh
   bundle install
   ```

2. Verifique se o Python, PyGMT e pdf2svg estão instalados para a tarefa `azure_regions`. Para obter mais detalhes sobre a instalação, consulte a documentação nos comentários em [_scripts/azure_regions.py](_scripts/azure_regions.py).
