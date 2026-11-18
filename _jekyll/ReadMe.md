---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
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

### `whatsnew_consolidated`

Consolida tabelas de Novidades publicadas dos projetos configurados da documentação do Commerce em `help/_includes/automated/whatsnew/consolidated.md`.

```sh
bundle exec rake whatsnew_consolidated
```

Configurar projetos em `whatsnew_consolidated.projects` em [`_config.yml`](_config.yml). Cada entrada requer um nome de repositório, um título de projeto e um URL absoluto do site HTTP(S):

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/en/docs/commerce
```

Mova as entradas para alterar a ordem das seções. É possível intercalar projetos livremente de ambas as plataformas. Nomes de repositório terminando com `.en` usam o caminho de origem ExL, `help/_includes/templated/whats-new.md`. Todos os outros repositórios usam o caminho de origem DevSite, `src/pages/_includes/templated/whats-new.md`.

A tarefa busca arquivos públicos `main` da organização GitHub `AdobeDocs`. Ele exibe cada título de projeto como um cabeçalho de texto sem formatação e introduz cada tabela com uma frase vinculando o título do projeto à página inicial da documentação configurada em `website` como a fonte das atualizações de Novidades. Ele usa cabeçalhos de tabela `Description | Type | Date/source` em todo o. Somente para projetos DevSite, tags `\<br/\>` de escape tornam-se `<br/>`. Caso contrário, as linhas de corpo, duplicatas, links e a ordem das linhas de origem permanecerão inalteradas. Cada origem define seu próprio período de tempo.

Projetos com uma mensagem de não atualização reconhecida são omitidos. Se cada projeto não tiver entradas, a inclusão conterá uma mensagem geral de não atualização. Falhas de configuração, busca, análise ou gravação causam falha na tarefa sem substituir uma inclusão existente.

A tarefa não agenda a geração ou atualização de páginas de consumo.

O conjunto de testes focalizado inclui testes de ponto de entrada Rake que carregam o Rakefile `_jekyll` e são executados pelo Bundler. Primeiro instale o pacote e o `_jekyll`:

```sh
cd _jekyll && bundle install
```

Em seguida, execute os testes a partir da raiz do repositório:

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

Cria `help/_includes/automated/whatsnew/consolidated-feedback.md` filtrando a inclusão local `help/_includes/automated/whatsnew/consolidated.md` existente.

```sh
bundle exec rake whatsnew_feedback
```

A tarefa corresponde a `Feedback` como um valor Type completo, separado por vírgulas, ignorando maiúsculas e minúsculas e envolvendo espaços em branco. Tipos combinados como `Feedback, technical` são incluídos. As menções em descrições, links de origem ou nomes de tipos parciais não são qualificadas.

As linhas, duplicatas, cabeçalhos de projeto de texto sem formatação, frases de origem quando presentes e a ordem do projeto e da linha correspondentes permanecem inalteradas. Projetos sem entradas correspondentes são omitidos. Se nada corresponder, a saída conterá uma mensagem geral sem feedback.

A entrada já deve existir. Execute `bundle exec rake whatsnew_consolidated` separadamente quando quiser atualizá-lo. A tarefa de feedback não busca conteúdo remoto, lê configuração de projeto ou regenera sua entrada.

Entrada ausente ou malformada falha na tarefa sem substituir uma inclusão filtrada existente. O arquivo de entrada nunca é modificado e a saída filtrada é publicada com precisão.

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
