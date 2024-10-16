---
source-git-commit: a8f4df78dfec2a1e94d650cac03c7fba21f398e8
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Versão**: 3.0.19

Esta referência contém 9 comandos disponíveis através da ferramenta de linha de comando `bin/uct`.
A lista inicial é gerada automaticamente usando o comando `bin/uct list` na Adobe Commerce.

## Geral

Saiba mais sobre a ferramenta em [Visão geral](/help/upgrade/upgrade-compatibility-tool/overview.md).

Esta documentação de referência é gerada a partir do código-fonte do aplicativo. Para alterar a documentação, você deve abrir uma solicitação de pull para o comando correspondente no repositório [codebase](https://github.com/magento) relevante. Consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) para obter mais informações.

### Opções globais

#### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para o comando de lista

- Padrão: `false`
- Não aceita um valor

#### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

#### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

#### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

#### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

#### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

#### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

Comando interno para fornecer sugestões de conclusão de shell

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--shell`, `-s`

O tipo de shell (&quot;bash&quot;)

- Requer um valor

#### `--input`, `-i`

Uma matriz de tokens de entrada (por exemplo, COMP_WORDS ou argv)

- Padrão: `[]`
- Requer um valor

#### `--current`, `-c`

O índice da matriz &quot;input&quot; na qual o cursor está (por exemplo, COMP_CWORD)

- Requer um valor

#### `--symfony`, `-S`

A versão do script de conclusão

- Requer um valor


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Despejar o script de conclusão do shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```

### Argumentos

#### `shell`

O tipo de shell (por exemplo, &quot;bash&quot;), o valor do var env &quot;$SHELL&quot; será usado se isso não for fornecido

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--debug`

Analisar o log de depuração da conclusão

- Padrão: `false`
- Não aceita um valor


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Exibir a ajuda de um comando

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumentos

#### `command_name`

O nome do comando

- Padrão: `help`

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--format`

O formato de saída (txt, xml, json ou md)

- Padrão: `txt`
- Requer um valor

#### `--raw`

Para gerar a ajuda do comando raw

- Padrão: `false`
- Não aceita um valor


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Listar comandos

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Argumentos

#### `namespace`

O nome do namespace

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--raw`

Para gerar a lista de comandos raw

- Padrão: `false`
- Não aceita um valor

#### `--format`

O formato de saída (txt, xml, json ou md)

- Padrão: `txt`
- Requer um valor

#### `--short`

Para ignorar a descrição dos argumentos dos comandos

- Padrão: `false`
- Não aceita um valor


## `refactor`

```bash
bin/uct refactor <path>
```

Resolve os problemas que podem ser corrigidos automaticamente. O código no caminho fornecido será atualizado.

### Argumentos

#### `path`

Caminho para resolver problemas no.

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

A Ferramenta de compatibilidade de atualização é uma ferramenta de linha de comando que verifica uma instância do Adobe Commerce em relação a uma versão específica analisando todos os módulos que não são da Adobe Commerce instalados nela. Retorna uma lista de erros e avisos que você deve corrigir antes de atualizar para uma nova versão do código Adobe Commerce.

### Argumentos

#### `dir`

diretório de instalação do Adobe Commerce.

- Obrigatório


#### `vanilla-dir`

diretório de instalação do Adobe Commerce vanilla.

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Caminho do arquivo onde a saída será exportada (Formato Json)

- Aceita um valor


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Permite listar as diferenças de esquema do Adobe Commerce DB entre duas versões selecionadas. Versões disponíveis: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1

### Argumentos

#### `current-version`

versão atual (por exemplo, 2.3.2).

- Obrigatório


#### `target-version`

versão de destino (por exemplo, 2.4.5).

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Verificação de compatibilidade de esquema do GraphQL

### Argumentos

#### `schema1`

URL do ponto de extremidade apontando para o primeiro esquema do GraphQL.

- Obrigatório


#### `schema2`

URL do ponto de extremidade apontando para o segundo esquema do GraphQL.

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Caminho do arquivo onde a saída será exportada (formato JSON)

- Aceita um valor


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

A Ferramenta de compatibilidade de atualização é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos instalados nela. Retorna uma lista de erros e avisos que devem ser resolvidos antes de atualizar para a versão mais recente do Adobe Commerce.

### Argumentos

#### `dir`

diretório de instalação do Adobe Commerce.

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--current-version`, `-a`

A versão atual do Adobe Commerce e a versão da instalação do Adobe Commerce serão usadas, se omitida.

- Aceita um valor

#### `--coming-version`, `-c`

Versão do Adobe Commerce de destino. A versão estável mais recente lançada do Adobe Commerce será usada se omitida. Versões disponíveis do Adobe Commerce: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 2.3.4 \| 2.3.4-p1 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 2.3.7 \| 2.3.7-p1 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 2.4.0-p1 2.4.1 2.4.1-p1 2.4.2 \| 2.4.2-p1 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 2.4.4-p11 2.4.5 \| 2.4.5-p1 \| 2,4,5-p2 \| 2,4,5-p3 \| 2.4.5-p4 \| 2,4,5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2,4,5 - p10 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2,4,6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.8-beta1

- Aceita um valor

#### `--json-output-path`

Caminho do arquivo onde a saída será exportada no formato json

- Aceita um valor

#### `--html-output-path`

Caminho do arquivo onde a saída será exportada no formato HTML

- Aceita um valor

#### `--min-issue-level`

Nível mínimo de problema que você deseja ver no relatório (aviso, erro ou crítico).

- Padrão: `warning`
- Aceita um valor

#### `--ignore-current-version-compatibility-issues`, `-i`

Ignorar problemas comuns da versão atual e futura

- Padrão: `false`
- Não aceita um valor

#### `--context`

Contexto de execução. Essa opção é para fins de integração e não afeta o resultado da execução.

- Requer um valor

