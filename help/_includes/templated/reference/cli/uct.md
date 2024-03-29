---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versão**: 3.0.3

Esta referência contém 9 comandos disponíveis através do `bin/uct` ferramenta de linha de comando.
A lista inicial é gerada automaticamente usando o `bin/uct list` comando no Adobe Commerce.

Saiba mais sobre a ferramenta em [Visão geral](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Essa referência é gerada a partir da base de código do aplicativo. Para alterar o conteúdo, você pode atualizar o código-fonte para a implementação do comando correspondente no [codebase](https://github.com/magento) repositório e enviar suas alterações para revisão. Outra maneira é _Envie seus comentários_ (localize o link no canto superior direito). Para obter diretrizes de contribuição, consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno para fornecer sugestões de conclusão de shell

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

O tipo de shell (&quot;bash&quot;)

- Requer um valor

### `--input`, `-i`

Uma matriz de tokens de entrada (por exemplo, COMP_WORDS ou argv)

- Padrão: `[]`
- Requer um valor

### `--current`, `-c`

O índice da matriz &quot;input&quot; na qual o cursor está (por exemplo, COMP_CWORD)

- Requer um valor

### `--symfony`, `-S`

A versão do script de conclusão

- Requer um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `completion`

Despejar o script de conclusão do shell

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

O tipo de shell (por exemplo, &quot;bash&quot;), o valor do var env &quot;$SHELL&quot; será usado se isso não for fornecido


### `--debug`

Analisar o log de depuração da conclusão

- Padrão: `false`
- Não aceita um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `help`

Exibir a ajuda de um comando

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

O nome do comando

- Padrão: `help`


### `--format`

O formato de saída (txt, xml, json ou md)

- Padrão: `txt`
- Requer um valor

### `--raw`

Para gerar a ajuda do comando raw

- Padrão: `false`
- Não aceita um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `list`

Listar comandos

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

O nome do namespace


### `--raw`

Para gerar a lista de comandos raw

- Padrão: `false`
- Não aceita um valor

### `--format`

O formato de saída (txt, xml, json ou md)

- Padrão: `txt`
- Requer um valor

### `--short`

Para ignorar a descrição dos argumentos dos comandos

- Padrão: `false`
- Não aceita um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `refactor`

Resolve os problemas que podem ser corrigidos automaticamente. O código no caminho fornecido será atualizado.

```bash
bin/uct refactor <path>
```


### `path`

Caminho para resolver problemas no.

- Obrigatório

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `core:code:changes`

A Ferramenta de compatibilidade de atualização é uma ferramenta de linha de comando que verifica uma instância do Adobe Commerce em relação a uma versão específica analisando todos os módulos que não são da Adobe Commerce instalados nela. Retorna uma lista de erros e avisos que você deve corrigir antes de atualizar para uma nova versão do código Adobe Commerce.

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

diretório de instalação do Adobe Commerce.

- Obrigatório

### `vanilla-dir`

diretório de instalação do Adobe Commerce vanilla.


### `--output`, `-o`

Caminho do arquivo onde a saída será exportada (Formato Json)

- Aceita um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dbschema:diff`

Permite listar as diferenças de esquema do Adobe Commerce DB entre duas versões selecionadas.
Versões disponíveis: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2,3,5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2,4,5-p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

versão atual (por exemplo, 2.3.2).

- Obrigatório

### `target-version`

versão de destino (por exemplo, 2.4.5).

- Obrigatório

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `graphql:compare`

Verificação de compatibilidade de esquema do GraphQL

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

URL do ponto de extremidade apontando para o primeiro esquema do GraphQL.

- Obrigatório

### `schema2`

URL do ponto de extremidade apontando para o segundo esquema do GraphQL.

- Obrigatório

### `--output`, `-o`

Caminho do arquivo onde a saída será exportada (formato JSON)

- Aceita um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `upgrade:check`

A Ferramenta de compatibilidade de atualização é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos instalados nela. Retorna uma lista de erros e avisos que devem ser resolvidos antes de atualizar para a versão mais recente do Adobe Commerce.

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

diretório de instalação do Adobe Commerce.

- Obrigatório

### `--current-version`, `-a`

A versão atual do Adobe Commerce e a versão da instalação do Adobe Commerce serão usadas, se omitida.

- Aceita um valor

### `--coming-version`, `-c`

A versão do Adobe Commerce de destino, a versão mais recente lançada do Adobe Commerce, será usada se omitida. Versões do Adobe Commerce disponíveis: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4 \| 2.4 -p1 \| 2.4.5 \| 2.4.4-p2 \| 2.4.5-p1 \| 2.4.4-p3 \| 2.4.5-p2 \| 2.4.6

- Aceita um valor

### `--json-output-path`

Caminho do arquivo onde a saída será exportada no formato json

- Aceita um valor

### `--html-output-path`

Caminho do arquivo onde a saída será exportada no formato HTML

- Aceita um valor

### `--min-issue-level`

Nível mínimo de problema que você deseja ver no relatório (aviso, erro ou crítico).

- Padrão: `warning`
- Aceita um valor

### `--ignore-current-version-compatibility-issues`, `-i`

Ignorar problemas comuns da versão atual e futura

- Padrão: `false`
- Não aceita um valor

### `--context`

Contexto de execução. Essa opção é para fins de integração e não afeta o resultado da execução.

- Requer um valor

### `--help`, `-h`

Exibe a ajuda para o comando fornecido. Quando nenhum comando é fornecido, exibir ajuda para \&lt;info>lista\&lt;/info> comando

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar (ou desativar — no- ansi) a saída ANSI

- Não aceita um valor

### `--no-ansi`

Negar a opção &quot;—ansi&quot;

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor

