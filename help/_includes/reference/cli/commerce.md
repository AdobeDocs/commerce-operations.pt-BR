---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce na infraestrutura de nuvem)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versão**: 1.38.1 <!-- app.version -->

Esta referência contém 127 comandos disponíveis através do `magento-cloud` ferramenta de linha de comando.
A lista inicial é gerada automaticamente usando o `magento-cloud list` na edição.

>[!NOTE]
>
>Essa referência é gerada a partir da base de código do aplicativo. Para alterar o conteúdo, você pode atualizar o código-fonte para a implementação do comando correspondente no [base de código](https://github.com/magento) e envie suas alterações para análise. Outra maneira de _Fornecer feedback_ (localize o link no canto superior direito). Para obter as diretrizes de contribuição, consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

Gancho de conclusão da BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



Gere o código BASH que configura a conclusão deste aplicativo.
- Padrão: `false`
- Não aceita um valor



### `--program`, `-p`



Nome do programa que deve acionar a conclusão &lt;comment>(o padrão é o caminho absoluto do aplicativo)&lt;/comment>.
- Requer um valor



### `--multiple`, `-m`



O gancho gerado pode ser usado para vários aplicativos.
- Padrão: `false`
- Não aceita um valor


### `--shell-type`

Defina o tipo de shell (zsh ou bash). Caso contrário, isso será determinado automaticamente.
- Aceita um valor <!-- options --> <!-- options.size -->

## `bot`

O bot Magento Cloud

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- Padrão: `false`
- Não aceita um valor


### `--parrot`


- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `clear-cache`

Limpar o cache da CLI

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `decode`

Decodificar uma string codificada, como MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

O valor da variável a ser decodificado
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade a ser exibida na variável
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `docs`

Abra a documentação online

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

Pesquisar termo(s)

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

O navegador a ser usado para abrir o URL. Defina 0 como nenhum.
- Requer um valor


### `--pipe`

Coloque o URL como stdout.
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `help`

Exibe a ajuda de um comando

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

O nome do comando
- Padrão: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

O formato de saída (txt, xml, json ou md)
- Padrão: `txt`
- Requer um valor


### `--raw`

Para gerar a ajuda do comando bruto
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `legacy-migrate`

Migrar da estrutura de arquivos herdada

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

Não crie um backup do projeto.
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `list`

Comandos Lists

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

O nome do namespace
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Para exibir a lista de comandos brutos
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (txt, xml, json ou md)
- Padrão: `txt`
- Requer um valor <!-- options --> <!-- options.size -->

## `multi`

Executar um comando em vários projetos

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

O comando a ser executado
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



Uma lista de IDs de projeto, separadas por vírgulas e/ou espaço em branco
- Requer um valor


### `--continue`

Continue executando comandos mesmo se uma exceção for encontrada
- Padrão: `false`
- Não aceita um valor


### `--sort`

Uma propriedade pela qual classificar a lista de opções do projeto
- Padrão: `title`
- Requer um valor


### `--reverse`

Inverter a ordem das opções do projeto
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `web`

Abra a interface do usuário da Web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

O navegador a ser usado para abrir o URL. Defina 0 como nenhum.
- Requer um valor


### `--pipe`

Coloque o URL como stdout.
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `welcome`

Bem-vindo à Magento Cloud

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `activity:cancel`

Cancelar uma atividade

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID da atividade. O padrão é a atividade cancelável mais recente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrar por tipo (ao selecionar uma atividade padrão)
- Requer um valor



### `--all`, `-a`



Verificar atividades recentes em todos os ambientes (ao selecionar uma atividade padrão)
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `activity:get`

Exibir informações detalhadas sobre uma única atividade

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID da atividade. O padrão é a atividade mais recente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade a ser exibida
- Requer um valor


### `--type`

Filtrar por tipo (ao selecionar uma atividade padrão)
- Requer um valor


### `--state`

Filtrar por estado (ao selecionar uma atividade padrão): in_progress, pendente, concluído ou cancelado
- Padrão: `[]`
- Requer um valor


### `--result`

Filtrar por resultado (ao selecionar uma atividade padrão): sucesso ou falha
- Requer um valor



### `--incomplete`, `-i`



Inclua apenas atividades incompletas (ao selecionar uma atividade padrão). Este é um encurtador para &lt;info>—state=in_progress,pending&lt;/info>
- Padrão: `false`
- Não aceita um valor



### `--all`, `-a`



Verificar atividades recentes em todos os ambientes (ao selecionar uma atividade padrão)
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `activity:list`

Obter uma lista de atividades para um ambiente ou projeto

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Filtrar atividades por tipo
- Requer um valor


### `--limit`

Limite o número de resultados exibidos
- Padrão: `10`
- Requer um valor


### `--start`

Somente as atividades criadas antes dessa data serão listadas
- Requer um valor


### `--state`

Filtrar atividades por estado: in_progress, pendente, concluído ou cancelado
- Padrão: `[]`
- Requer um valor


### `--result`

Filtrar atividades por resultado: sucesso ou falha
- Requer um valor



### `--incomplete`, `-i`



Listar apenas atividades incompletas
- Padrão: `false`
- Não aceita um valor



### `--all`, `-a`



Listar atividades em todos os ambientes
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `activity:log`

Exibir o log de uma atividade

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID da atividade. O padrão é a atividade mais recente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Intervalo de atualização da atividade (segundos). Defina como 0 para desativar a atualização.
- Padrão: `3`
- Requer um valor



### `--timestamps`, `-t`



Exibir um carimbo de data e hora ao lado de cada mensagem
- Padrão: `false`
- Não aceita um valor


### `--type`

Filtrar por tipo (ao selecionar uma atividade padrão)
- Requer um valor


### `--state`

Filtrar por estado (ao selecionar uma atividade padrão): in_progress, pendente, concluído ou cancelado
- Padrão: `[]`
- Requer um valor


### `--result`

Filtrar por resultado (ao selecionar uma atividade padrão): sucesso ou falha
- Requer um valor



### `--incomplete`, `-i`



Inclua apenas atividades incompletas (ao selecionar uma atividade padrão). Este é um encurtador para &lt;info>—state=in_progress,pending&lt;/info>
- Padrão: `false`
- Não aceita um valor



### `--all`, `-a`



Verificar atividades recentes em todos os ambientes (ao selecionar uma atividade padrão)
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `api:curl`

Execute uma solicitação de cURL autenticada na API da Magento Cloud

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

O caminho da API
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



O método de solicitação a ser usado
- Requer um valor



### `--data`, `-d`



Dados para enviar
- Requer um valor



### `--include`, `-i`



Incluir cabeçalhos na saída
- Padrão: `false`
- Não aceita um valor



### `--head`, `-I`



Buscar somente cabeçalhos
- Padrão: `false`
- Não aceita um valor


### `--disable-compression`

Não use o curl - sinalizador compactado
- Padrão: `false`
- Não aceita um valor


### `--enable-glob`

Ativar a globalização do curl (remover o sinalizador —globoff)
- Padrão: `false`
- Não aceita um valor



### `--header`, `-H`



Cabeçalho(s) extra
- Padrão: `[]`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `app:config-get`

Exibir a configuração de um aplicativo

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de configuração a ser exibida
- Requer um valor


### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--identity-file`, `-i`



[Opção obsoleta, não é mais usada]
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `app:list`

Listar aplicativos no projeto

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:api-token-login`

Faça logon no Magento Cloud usando um token de API

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:browser-login`

Faça logon no Magento Cloud por meio de um navegador

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Faça logon novamente, mesmo que já tenha feito logon
- Padrão: `false`
- Não aceita um valor


### `--browser`

O navegador a ser usado para abrir o URL. Defina 0 como nenhum.
- Requer um valor


### `--pipe`

Coloque o URL como stdout.
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:info`

Exibir suas informações de conta

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

A propriedade da conta a ser exibida
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade da conta a ser exibida (sintaxe alternativa)
- Requer um valor


### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:logout`

Saia do Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Fazer logoff de todas as sessões locais
- Padrão: `false`
- Não aceita um valor


### `--other`

Fazer logoff de outras sessões locais
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Faça logon no Magento Cloud usando um nome de usuário e senha

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `auth:token`

Obter um token de acesso OAuth 2 para solicitações de APIs da Magento Cloud

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `blackfire:setup`

Configurar a integração do Blackfire.io para o projeto

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

A ID do servidor
- Requer um valor


### `--server_token`

O token do servidor
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `certificate:add`

Adicionar um certificado SSL ao projeto

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

O caminho para o arquivo de certificado
- Requer um valor


### `--key`

O caminho para o arquivo de chave privada do certificado
- Requer um valor


### `--chain`

O caminho para o arquivo da cadeia de certificados
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `certificate:delete`

Excluir um certificado do projeto

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID do certificado (ou o seu início)
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `certificate:get`

Exibir um certificado

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID do certificado (ou o seu início)
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de certificado a ser exibida
- Requer um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `certificate:list`

Listar certificados de projeto

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

Filtrar por nome de domínio (pesquisa não diferencia maiúsculas de minúsculas)
- Requer um valor


### `--exclude-domain`

Excluir certificados, correspondendo por nome de domínio (pesquisa que não diferencia maiúsculas de minúsculas)
- Requer um valor


### `--issuer`

Filtrar por emissor
- Requer um valor


### `--only-auto`

Mostrar somente certificados provisionados automaticamente
- Padrão: `false`
- Não aceita um valor


### `--no-auto`

Mostrar apenas certificados adicionados manualmente
- Padrão: `false`
- Não aceita um valor


### `--ignore-expiry`

Mostrar certificados expirados e não expirados
- Padrão: `false`
- Não aceita um valor


### `--only-expired`

Mostrar apenas certificados expirados
- Padrão: `false`
- Não aceita um valor


### `--no-expired`

Mostrar somente certificados não expirados (padrão)
- Padrão: `false`
- Não aceita um valor


### `--pipe-domains`

Retornar apenas uma lista de nomes de domínio cobertos pelos certificados
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `commit:get`

Mostrar detalhes da confirmação

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

O SHA de confirmação. Isso também pode aceitar os sufixos &quot;HEAD&quot; e sinal de interpolação (^) ou til (~) para confirmações principais.
- Padrão: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de confirmação a ser exibida.
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor


### `--format`

OBSOLETO
- Requer um valor


### `--columns`

OBSOLETO
- Padrão: `[]`
- Requer um valor


### `--no-header`

OBSOLETO
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `commit:list`

Comentários da lista

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

O Git inicial confirma SHA. Isso também pode aceitar os sufixos &quot;HEAD&quot; e sinal de interpolação (^) ou til (~) para confirmações principais.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

O número de confirmações a serem exibidas.
- Padrão: `10`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `db:dump`

Criar um despejo local do banco de dados remoto

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

O esquema a ser despejado. Omitir para usar o schema padrão (geralmente &quot;principal&quot;).
- Requer um valor



### `--file`, `-f`



Um nome de arquivo personalizado para o despejo
- Requer um valor



### `--directory`, `-d`



Um diretório personalizado para o despejo
- Requer um valor



### `--gzip`, `-z`



Compacte o despejo usando gzip
- Padrão: `false`
- Não aceita um valor



### `--timestamp`, `-t`



Adicionar um carimbo de data e hora ao nome do arquivo de despejo
- Padrão: `false`
- Não aceita um valor



### `--stdout`, `-o`



Saída para STDOUT em vez de um arquivo
- Padrão: `false`
- Não aceita um valor


### `--table`

Tabela(s) a incluir
- Padrão: `[]`
- Requer um valor


### `--exclude-table`

Tabela(s) a excluir
- Padrão: `[]`
- Requer um valor


### `--schema-only`

Despejar apenas esquemas, sem dados
- Padrão: `false`
- Não aceita um valor


### `--charset`

A codificação do conjunto de caracteres para o despejo
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `db:size`

Estimativa do uso de disco de um banco de dados

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Mostrar tamanhos em bytes.
- Padrão: `false`
- Não aceita um valor



### `--cleanup`, `-C`



Verifique se as tabelas podem ser removidas e me mostrar recomendações (somente InnoDb).
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `db:sql`

Executar SQL no banco de dados remoto

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

Uma instrução SQL a ser executada
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Produzir saída bruta e não tabular
- Padrão: `false`
- Não aceita um valor


### `--schema`

O schema a ser usado. Omitir para usar o schema padrão (geralmente &quot;principal&quot;). Passe uma string vazia para não usar nenhum schema.
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `domain:add`

Adicionar um novo domínio ao projeto

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome do domínio
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

O caminho para o arquivo de certificado para este domínio
- Requer um valor


### `--key`

O caminho para o arquivo de chave privada do certificado fornecido.
- Requer um valor


### `--chain`

O caminho para o arquivo ou arquivos da cadeia de certificados para o certificado fornecido
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `domain:delete`

Excluir um domínio do projeto

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome do domínio
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `domain:get`

Mostrar informações detalhadas de um domínio

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome do domínio
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de domínio a ser exibida
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `domain:list`

Obter uma lista de todos os domínios

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `domain:update`

Atualizar um domínio

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome do domínio
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

O caminho para o arquivo de certificado para este domínio
- Requer um valor


### `--key`

O caminho para o arquivo de chave privada do certificado fornecido.
- Requer um valor


### `--chain`

O caminho para o arquivo ou arquivos da cadeia de certificados para o certificado fornecido
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:activate`

Ativar um ambiente

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Os ambientes a serem ativados

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

Definir um novo pai de ambiente antes de ativar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:branch`

Ramificação de um ambiente

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID (nome da ramificação) do novo ambiente
<!-- argument -->

### `parent`

O pai do novo ambiente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

O título do novo ambiente
- Requer um valor


### `--force`

Criar o novo ambiente mesmo que a ramificação não possa ser dada por check-out localmente
- Padrão: `false`
- Não aceita um valor


### `--no-clone-parent`

Não clonar os dados da ramificação principal
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:checkout`

Verificar um ambiente

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID do ambiente para check-out. Por exemplo: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:delete`

Excluir um ambiente

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

O(s) ambiente(s) a ser(em) excluído(s)

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

Exclua as ramificações Git remotas também
- Padrão: `false`
- Não aceita um valor


### `--no-delete-branch`

Não exclua ramificações Git remotas
- Padrão: `false`
- Não aceita um valor


### `--inactive`

Excluir todos os ambientes inativos
- Padrão: `false`
- Não aceita um valor


### `--merged`

Excluir todos os ambientes mesclados
- Padrão: `false`
- Não aceita um valor


### `--exclude`

Ambientes para não excluir
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:http-access`

Atualizar configurações de acesso HTTP para um ambiente

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

Restrição de acesso no formato &quot;permissão:endereço&quot;. Use 0 para limpar todos os endereços.
- Padrão: `[]`
- Requer um valor


### `--auth`

Credenciais de autenticação do HTTP Basic no formato &quot;nome de usuário:senha&quot;. Use 0 para limpar todas as credenciais.
- Padrão: `[]`
- Requer um valor


### `--enabled`

Se o controle de acesso deve ser ativado: 1 para ativar, 0 para desativar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:info`

Ler ou definir propriedades para um ambiente

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

O nome da propriedade
<!-- argument -->

### `value`

Definir um novo valor para a propriedade
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:init`

Inicializar um ambiente de um repositório Git público

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Um URL para um repositório Git
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

O nome do perfil
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:list`

Obter uma lista de ambientes

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



Não mostrar ambientes inativos
- Padrão: `false`
- Não aceita um valor


### `--pipe`

Coloque uma lista simples de IDs de ambiente.
- Padrão: `false`
- Não aceita um valor


### `--refresh`

Se a lista deve ser atualizada.
- Padrão: `1`
- Requer um valor


### `--sort`

Uma propriedade para classificar por
- Padrão: `title`
- Requer um valor


### `--reverse`

Classificar em ordem inversa (decrescente)
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:logs`

Ler os registros de um ambiente

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

O tipo de log, por exemplo &quot;access&quot; ou &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

O número de linhas a serem mostradas
- Padrão: `100`
- Requer um valor


### `--tail`

Continuamente rastrear o log
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:merge`

Mesclar um ambiente

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

O ambiente a ser mesclado
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:push`

Enviar código para um ambiente

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

A referência de origem: um nome de ramificação ou hash de confirmação
- Padrão: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

O nome da ramificação de destino
- Requer um valor



### `--force`, `-f`



Permitir atualizações não rápidas
- Padrão: `false`
- Não aceita um valor


### `--force-with-lease`

Permitir atualizações não rápidas, se a ramificação de rastreamento remoto estiver atualizada
- Padrão: `false`
- Não aceita um valor



### `--set-upstream`, `-u`



Definir o ambiente de destino como o upstream para a ramificação de origem
- Padrão: `false`
- Não aceita um valor


### `--activate`

Ative o ambiente antes de enviar
- Padrão: `false`
- Não aceita um valor


### `--branch`

OBSOLETO: alias de —ativate
- Padrão: `false`
- Não aceita um valor


### `--parent`

Definir um novo pai de ambiente (usado somente com —ativate ou —branch)
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:redeploy`

Reimplantar um ambiente

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:relationships`

Mostrar as relações de um ambiente

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

O ambiente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de relacionamento a ser exibida
- Requer um valor


### `--refresh`

Se os relacionamentos devem ser atualizados
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:scp`

Copiar arquivos de e para o ambiente atual usando o scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

Arquivos a serem copiados. Use o controle remoto: para definir locais remotos.

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



Copiar recursivamente todos os diretórios
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:set-remote`

Definir o ambiente remoto para mapear para uma ramificação

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

O nome da máquina do ambiente. Defina como 0 para remover o mapeamento de uma ramificação
- Obrigatório

   <!-- argument -->

### `branch`

A ramificação Git a ser mapeada (o padrão é a ramificação atual)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH para o ambiente atual

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Um comando para executar no ambiente.

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Coloque o URL do SSH somente.
- Padrão: `false`
- Não aceita um valor


### `--all`

Coloque todos os URLs SSH (para cada aplicativo).
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:synchronize`

Sincronizar o código e/ou os dados de um ambiente do pai

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

O que sincronizar: &quot;code&quot;, &quot;data&quot; ou ambos

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

Sincronize o código rebaseando em vez de mesclar
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:url`

Obter os URLs públicos de um ambiente

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



Retorna somente o URL da rota primária
- Padrão: `false`
- Não aceita um valor


### `--browser`

O navegador a ser usado para abrir o URL. Defina 0 como nenhum.
- Requer um valor


### `--pipe`

Coloque o URL como stdout.
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `environment:xdebug`

Abra um túnel para Xdebug no ambiente

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

A porta local
- Padrão: `9000`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:activity:get`

Exibir informações detalhadas sobre uma única atividade de integração

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Uma ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument -->

### `activity`

A ID da atividade. O padrão é a atividade de integração mais recente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade a ser exibida
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



[Opção obsoleta, não usada]
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:activity:list`

Obter uma lista de atividades para uma integração

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

Uma ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrar atividades por tipo
- Requer um valor


### `--limit`

Limite o número de resultados exibidos
- Padrão: `10`
- Requer um valor


### `--start`

Somente as atividades criadas antes dessa data serão listadas
- Requer um valor


### `--state`

Filtrar atividades por estado
- Padrão: `[]`
- Requer um valor


### `--result`

Filtrar atividades por resultado
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



[Opção obsoleta, não usada]
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:activity:log`

Exibir o log de uma atividade de integração

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Uma ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument -->

### `activity`

A ID da atividade. O padrão é a atividade de integração mais recente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



Exibir um carimbo de data e hora ao lado de cada mensagem
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



[Opção obsoleta, não usada]
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:add`

Adicionar uma integração ao projeto

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

O tipo de integração (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- Requer um valor


### `--base-url`

O URL básico da instalação do servidor
- Requer um valor


### `--username`

O nome de usuário do servidor de bucket
- Requer um valor


### `--token`

Um token de acesso para a integração
- Requer um valor


### `--key`

Uma chave de consumidor Bitbucket OAuth
- Requer um valor


### `--secret`

Um segredo do consumidor Bitbucket OAuth
- Requer um valor


### `--server-project`

O projeto (por exemplo, &#39;namespace/repo&#39;)
- Requer um valor


### `--repository`

O repositório a ser rastreado (por exemplo, &#39;owner/repository&#39;)
- Requer um valor


### `--build-merge-requests`

GitLab: criar solicitações de mesclagem como ambientes
- Padrão: `true`
- Requer um valor


### `--build-pull-requests`

Criar cada solicitação de pull como um ambiente
- Padrão: `true`
- Requer um valor


### `--build-draft-pull-requests`

Criar solicitações de pull de rascunho
- Padrão: `true`
- Requer um valor


### `--build-pull-requests-post-merge`

Criar solicitações de pull com base em seu estado pós-mesclagem
- Padrão: `false`
- Requer um valor


### `--build-wip-merge-requests`

GitLab: criar solicitações de mesclagem WIP
- Padrão: `true`
- Requer um valor


### `--merge-requests-clone-parent-data`

GitLab: clonar dados para solicitações de mesclagem
- Padrão: `true`
- Requer um valor


### `--pull-requests-clone-parent-data`

Clonar os dados do ambiente pai para solicitações de pull
- Padrão: `true`
- Requer um valor


### `--resync-pull-requests`

Sincronizar novamente os dados do ambiente de solicitação de pull em cada build
- Padrão: `false`
- Requer um valor


### `--fetch-branches`

Buscar todas as ramificações do remoto (como ambientes inativos)
- Padrão: `true`
- Requer um valor


### `--prune-branches`

Exclua ramificações que não existem no remoto
- Padrão: `true`
- Requer um valor


### `--room`

ID da sala HipChat
- Requer um valor


### `--url`

Webhook: um URL para receber dados JSON
- Requer um valor


### `--shared-key`

Webhook: a chave secreta compartilhada JWS
- Requer um valor


### `--file`

O nome de um arquivo local que contém o script a ser carregado
- Requer um valor


### `--events`

Uma lista de eventos para agir, por exemplo, environment.push
- Padrão: `*`
- Requer um valor


### `--states`

Uma lista de estados para agir, por exemplo, pendente, em_andamento, concluído
- Padrão: `complete`
- Requer um valor


### `--environments`

As IDs de ambiente a serem incluídas
- Padrão: `*`
- Requer um valor


### `--excluded-environments`

As IDs de ambiente a serem excluídas
- Padrão: `[]`
- Requer um valor


### `--from-address`

[Opcional] Personalizar endereço De para emails de alerta
- Requer um valor


### `--recipients`

O(s) endereço(s) de email do recipient
- Padrão: `[]`
- Requer um valor


### `--channel`

O canal Slack
- Requer um valor


### `--routing-key`

A chave de roteamento Pagerduty
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:delete`

Excluir uma integração de um projeto

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:get`

Exibir detalhes de uma integração

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Uma ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de integração a ser exibida
- Aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:list`

Exibir uma lista de integração(ões) de projeto

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:update`

Atualizar uma integração

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID da integração a ser atualizada
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

O tipo de integração (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)
- Requer um valor


### `--base-url`

O URL básico da instalação do servidor
- Requer um valor


### `--username`

O nome de usuário do servidor de bucket
- Requer um valor


### `--token`

Um token de acesso para a integração
- Requer um valor


### `--key`

Uma chave de consumidor Bitbucket OAuth
- Requer um valor


### `--secret`

Um segredo do consumidor Bitbucket OAuth
- Requer um valor


### `--server-project`

O projeto (por exemplo, &#39;namespace/repo&#39;)
- Requer um valor


### `--repository`

O repositório a ser rastreado (por exemplo, &#39;owner/repository&#39;)
- Requer um valor


### `--build-merge-requests`

GitLab: criar solicitações de mesclagem como ambientes
- Padrão: `true`
- Requer um valor


### `--build-pull-requests`

Criar cada solicitação de pull como um ambiente
- Padrão: `true`
- Requer um valor


### `--build-draft-pull-requests`

Criar solicitações de pull de rascunho
- Padrão: `true`
- Requer um valor


### `--build-pull-requests-post-merge`

Criar solicitações de pull com base em seu estado pós-mesclagem
- Padrão: `false`
- Requer um valor


### `--build-wip-merge-requests`

GitLab: criar solicitações de mesclagem WIP
- Padrão: `true`
- Requer um valor


### `--merge-requests-clone-parent-data`

GitLab: clonar dados para solicitações de mesclagem
- Padrão: `true`
- Requer um valor


### `--pull-requests-clone-parent-data`

Clonar os dados do ambiente pai para solicitações de pull
- Padrão: `true`
- Requer um valor


### `--resync-pull-requests`

Sincronizar novamente os dados do ambiente de solicitação de pull em cada build
- Padrão: `false`
- Requer um valor


### `--fetch-branches`

Buscar todas as ramificações do remoto (como ambientes inativos)
- Padrão: `true`
- Requer um valor


### `--prune-branches`

Exclua ramificações que não existem no remoto
- Padrão: `true`
- Requer um valor


### `--room`

ID da sala HipChat
- Requer um valor


### `--url`

Webhook: um URL para receber dados JSON
- Requer um valor


### `--shared-key`

Webhook: a chave secreta compartilhada JWS
- Requer um valor


### `--file`

O nome de um arquivo local que contém o script a ser carregado
- Requer um valor


### `--events`

Uma lista de eventos para agir, por exemplo, environment.push
- Padrão: `*`
- Requer um valor


### `--states`

Uma lista de estados para agir, por exemplo, pendente, em_andamento, concluído
- Padrão: `complete`
- Requer um valor


### `--environments`

As IDs de ambiente a serem incluídas
- Padrão: `*`
- Requer um valor


### `--excluded-environments`

As IDs de ambiente a serem excluídas
- Padrão: `[]`
- Requer um valor


### `--from-address`

[Opcional] Personalizar endereço De para emails de alerta
- Requer um valor


### `--recipients`

O(s) endereço(s) de email do recipient
- Padrão: `[]`
- Requer um valor


### `--channel`

O canal Slack
- Requer um valor


### `--routing-key`

A chave de roteamento Pagerduty
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `integration:validate`

Validar uma integração existente

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Uma ID de integração. Deixe em branco para escolher de uma lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `local:build`

Criar o projeto atual localmente

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

Especificar aplicativos para criar

- Padrão: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



Usar links absolutos
- Padrão: `false`
- Não aceita um valor



### `--source`, `-s`



O diretório de origem. O padrão é a raiz do projeto atual.
- Requer um valor



### `--destination`, `-d`



O destino, ao qual a raiz da Web de cada aplicativo será vinculada simbolicamente. Padrão: _www
- Requer um valor



### `--copy`, `-c`



Copiar para um diretório de compilação, em vez de vincular simbólico a partir da origem
- Padrão: `false`
- Não aceita um valor


### `--clone`

Use o Git para clonar o HEAD atual para o diretório de compilação
- Padrão: `false`
- Não aceita um valor


### `--run-deploy-hooks`

Executar ganchos de implantação e/ou pós-implantação
- Padrão: `false`
- Não aceita um valor


### `--no-clean`

Não remover criações antigas
- Padrão: `false`
- Não aceita um valor


### `--no-archive`

Não criar ou usar um arquivo de build
- Padrão: `false`
- Não aceita um valor


### `--no-backup`

Não fazer backup da build anterior
- Padrão: `false`
- Não aceita um valor


### `--no-cache`

Desativar armazenamento em cache
- Padrão: `false`
- Não aceita um valor


### `--no-build-hooks`

Não executar ganchos pós-compilação
- Padrão: `false`
- Não aceita um valor


### `--no-deps`

Não instale as dependências de build localmente
- Padrão: `false`
- Não aceita um valor


### `--working-copy`

Empurrar: use o git para clonar um repositório de cada módulo Drupal em vez de simplesmente baixar uma versão
- Padrão: `false`
- Não aceita um valor


### `--concurrency`

Empurrar: definir o número de projetos simultâneos que serão processados ao mesmo tempo
- Padrão: `4`
- Requer um valor


### `--lock`

Empurrar: criar ou atualizar um arquivo de bloqueio (disponível somente com o Drush versão 7+)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `local:clean`

Remover criações de projeto antigas

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

O número máximo de builds a serem mantidas
- Padrão: `5`
- Requer um valor


### `--max-age`

A idade máxima das criações, em segundos. Ignorado se não estiver definido.
- Requer um valor


### `--include-active`

Excluir as criações ativas também
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `local:dir`

Localizar a raiz do projeto local

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

O subdiretório a ser encontrado (&#39;local&#39;, &#39;web&#39; ou &#39;shared&#39;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `mount:download`

Baixar arquivos de uma montagem usando o rsync

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Baixar de todas as montagens
- Padrão: `false`
- Não aceita um valor



### `--mount`, `-m`



A montagem (como um caminho relativo ao aplicativo)
- Requer um valor


### `--target`

O diretório no qual os arquivos serão baixados. Se —all for usado, o caminho de montagem será anexado
- Requer um valor


### `--source-path`

Use o caminho de origem da montagem (em vez do caminho de montagem) como um subdiretório do destino, quando —all for usado
- Padrão: `false`
- Não aceita um valor


### `--delete`

Se deseja excluir arquivos irrelevantes no diretório de destino
- Padrão: `false`
- Não aceita um valor


### `--exclude`

Arquivos a serem excluídos do download (padrão)
- Padrão: `[]`
- Requer um valor


### `--include`

Arquivos a serem incluídos no download (padrão)
- Padrão: `[]`
- Requer um valor


### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `mount:list`

Obter uma lista de montagens

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

Saia apenas dos caminhos de montagem (um por linha)
- Padrão: `false`
- Não aceita um valor


### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `mount:size`

Verifique o uso de montagens no disco

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Mostrar tamanhos em bytes
- Padrão: `false`
- Não aceita um valor


### `--refresh`

Atualizar o cache
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `mount:upload`

Fazer upload de arquivos para uma montagem usando rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

Um diretório contendo arquivos para fazer upload
- Requer um valor



### `--mount`, `-m`



A montagem (como um caminho relativo ao aplicativo)
- Requer um valor


### `--delete`

Se deseja excluir arquivos irrelevantes na montagem
- Padrão: `false`
- Não aceita um valor


### `--exclude`

Arquivos a serem excluídos do upload (padrão)
- Padrão: `[]`
- Requer um valor


### `--include`

Arquivos a serem incluídos no upload (padrão)
- Padrão: `[]`
- Requer um valor


### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--worker`

Um nome de trabalhador
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

Limpar o cache de build de um projeto

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:curl`

Executar uma solicitação de cURL autenticada na API de um projeto

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

O caminho da API
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



O método de solicitação a ser usado
- Requer um valor



### `--data`, `-d`



Dados para enviar
- Requer um valor



### `--include`, `-i`



Incluir cabeçalhos na saída
- Padrão: `false`
- Não aceita um valor



### `--head`, `-I`



Buscar somente cabeçalhos
- Padrão: `false`
- Não aceita um valor


### `--disable-compression`

Não use o curl - sinalizador compactado
- Padrão: `false`
- Não aceita um valor


### `--enable-glob`

Ativar a globalização do curl (remover o sinalizador —globoff)
- Padrão: `false`
- Não aceita um valor



### `--header`, `-H`



Cabeçalho(s) extra
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:get`

Clonar um projeto localmente

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

A ID do projeto
<!-- argument -->

### `directory`

O diretório para o qual clonar. Padrões para o título do projeto
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



A ID do ambiente para clonar. O padrão do projeto é ou o primeiro ambiente disponível
- Requer um valor


### `--depth`

Criar um clone superficial: limitar o número de commits no histórico
- Requer um valor


### `--build`

Criar o projeto após a clonagem
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:info`

Ler ou definir propriedades para um projeto

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

O nome da propriedade
<!-- argument -->

### `value`

Definir um novo valor para a propriedade
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:list`

Obter uma lista de todos os projetos ativos

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

Coloque uma lista simples de IDs de projeto
- Padrão: `false`
- Não aceita um valor


### `--host`

Filtrar por nome de host da região (correspondência exata)
- Requer um valor


### `--title`

Filtrar por título (pesquisa não diferencia maiúsculas de minúsculas)
- Requer um valor


### `--my`

Exibir somente os projetos que você possui
- Padrão: `false`
- Não aceita um valor


### `--refresh`

Se a lista deve ser atualizada
- Padrão: `1`
- Requer um valor


### `--sort`

Uma propriedade para classificar por
- Padrão: `title`
- Requer um valor


### `--reverse`

Classificar em ordem inversa (decrescente)
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:set-remote`

Definir o projeto remoto para o repositório Git atual

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

A ID do projeto
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Excluir uma variável de um projeto

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Exibir variáveis de um projeto

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Coloque o valor total da variável somente (um &quot;nome&quot; deve ser especificado)
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Definir uma variável para um projeto

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument -->

### `value`

O valor da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Marcar o valor como JSON
- Padrão: `false`
- Não aceita um valor


### `--no-visible-build`

Não exponha essa variável no momento da criação
- Padrão: `false`
- Não aceita um valor


### `--no-visible-runtime`

Não exponha essa variável no tempo de execução
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `repo:cat`

Ler um arquivo no repositório do projeto

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

O caminho para o arquivo
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



O SHA de confirmação. Isso também pode aceitar os sufixos &quot;HEAD&quot; e sinal de interpolação (^) ou til (~) para confirmações principais.
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `repo:ls`

Listar arquivos no repositório do projeto

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

O caminho para um subdiretório
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



Mostrar somente diretórios
- Padrão: `false`
- Não aceita um valor



### `--files`, `-f`



Mostrar somente arquivos
- Padrão: `false`
- Não aceita um valor


### `--git-style`

Saída de estilo semelhante a &quot;git ls-tree&quot;
- Padrão: `false`
- Não aceita um valor



### `--commit`, `-c`



O SHA de confirmação. Isso também pode aceitar os sufixos &quot;HEAD&quot; e sinal de interpolação (^) ou til (~) para confirmações principais.
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `route:get`

Exibir informações detalhadas sobre uma rota

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

O URL original da rota
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

Um ID de rota para selecionar
- Requer um valor



### `--primary`, `-1`



Selecione a rota primária
- Padrão: `false`
- Não aceita um valor



### `--property`, `-P`



A propriedade a ser exibida
- Requer um valor


### `--refresh`

Ignorar o cache de rotas
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



[Opção obsoleta, não é mais usada]
- Requer um valor



### `--identity-file`, `-i`



[Opção obsoleta, não é mais usada]
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `route:list`

Listar todas as rotas para um ambiente

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

A ID do ambiente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Ignorar o cache de rotas
- Padrão: `false`
- Não aceita um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `self:install`

Instalar ou atualizar arquivos de configuração da CLI

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

O tipo de shell para autopreenchimento (bash ou zsh)
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `self:stats`

Visualizar estatísticas nos downloads de pacotes do GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



Número da página
- Padrão: `1`
- Requer um valor



### `--count`, `-c`



Resultados por página (máx.: 100)
- Padrão: `20`
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `self:update`

Atualize a CLI para a versão mais recente

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

Atualizar apenas entre versões secundárias ou de patch
- Padrão: `false`
- Não aceita um valor


### `--unstable`

Atualizar para uma nova versão instável, se disponível
- Padrão: `false`
- Não aceita um valor


### `--manifest`

Substituir o local do arquivo de manifesto
- Requer um valor


### `--current-version`

Substituir a versão atual
- Requer um valor


### `--timeout`

Um tempo limite para a verificação da versão
- Padrão: `30`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:list`

Listar serviços no projeto

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:mongo:dump`

Crie um despejo de dados de arquivo binário do MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



A coleção a ser despejada
- Requer um valor



### `--gzip`, `-z`



Compacte o despejo usando gzip
- Padrão: `false`
- Não aceita um valor



### `--stdout`, `-o`



Saída para STDOUT em vez de um arquivo
- Padrão: `false`
- Não aceita um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:mongo:export`

Exportar dados do MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



A coleção a ser exportada
- Requer um valor


### `--jsonArray`

Exportar dados como uma única matriz JSON
- Padrão: `false`
- Não aceita um valor


### `--type`

O tipo de exportação, por exemplo &quot;csv&quot;
- Requer um valor



### `--fields`, `-f`



Os campos a serem exportados
- Padrão: `[]`
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:mongo:restore`

Restaurar um despejo de arquivo binário de dados no MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



A coleção a ser restaurada
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:mongo:shell`

Usar o shell do MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

Envio de um fragmento JavaScript para o shell
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `service:redis-cli`

Acesso à CLI de Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Argumentos para adicionar ao comando Redis
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Alternar entre sessões

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A nova ID de sessão
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `snapshot:create`

Criar um instantâneo de um ambiente

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

O ambiente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

Backup em tempo real: não pare o ambiente. Se definido, isso deixará o ambiente em execução e aberto às conexões durante o backup. Isso reduz o tempo de inatividade, correndo o risco de fazer backup de dados em um estado inconsistente.
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `snapshot:list`

Listar instantâneos disponíveis de um ambiente

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

Limitar o número de instantâneos a listar
- Padrão: `10`
- Requer um valor


### `--start`

Somente os instantâneos criados antes dessa data serão listados
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `snapshot:restore`

Restaurar um instantâneo de ambiente

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

O nome do instantâneo. O padrão é o mais recente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

O ambiente para o qual restaurar. O padrão é o ambiente atual do instantâneo
- Requer um valor


### `--branch-from`

Se o —target ainda não existir, isso especifica o pai do novo ambiente
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Executar uma operação de origem

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

O nome da operação
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

Uma variável a ser definida durante a operação, no formato &lt;info>type:name=value&lt;/info>
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `ssh-cert:info`

Exibir informações sobre o certificado SSH atual

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

Não atualize o certificado se ele for inválido
- Padrão: `false`
- Não aceita um valor



### `--property`, `-P`



A propriedade certificate a ser exibida
- Requer um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `ssh-cert:load`

Gerar um certificado SSH

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

Atualize somente o certificado, se necessário (não gravar a configuração SSH)
- Padrão: `false`
- Não aceita um valor


### `--new`

Forçar a atualização do certificado
- Padrão: `false`
- Não aceita um valor


### `--new-key`

[Obsoleto] Use —new em vez disso
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `ssh-key:add`

Adicionar uma nova chave SSH

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

O caminho para uma chave pública SSH existente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

Um nome para identificar a chave
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `ssh-key:delete`

Excluir uma chave SSH

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

A ID da chave SSH a ser excluída
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `ssh-key:list`

Obter uma lista de chaves SSH em sua conta

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `subscription:info`

Ler ou modificar propriedades de assinatura

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

O nome da propriedade
<!-- argument -->

### `value`

Definir um novo valor para a propriedade
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



A ID da assinatura
- Requer um valor


### `--date-fmt`

O formato de data (como uma string de formato de data PHP)
- Padrão: `c`
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `tunnel:close`

Fechar túneis SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Fechar todos os túneis
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `tunnel:info`

Exibir informações de relacionamento para túneis SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



A propriedade de relacionamento a ser exibida
- Requer um valor



### `--encode`, `-c`



Saída como JSON codificado em base64
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `tunnel:list`

Listar túneis SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Ver todos os túneis
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `tunnel:open`

Abrir túneis SSH para as relações de um aplicativo

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



Permitir que hosts remotos se conectem a portas encaminhadas locais
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `tunnel:single`

Abra um único túnel SSH para um relacionamento de aplicativo

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

A porta local
- Requer um valor



### `--gateway-ports`, `-g`



Permitir que hosts remotos se conectem a portas encaminhadas locais
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--app`, `-A`



O nome do aplicativo remoto
- Requer um valor



### `--relationship`, `-r`



A relação de serviço a utilizar
- Requer um valor



### `--identity-file`, `-i`



Uma identidade SSH (chave privada) para usar
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `user:add`

Adicionar usuário ao projeto

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

O endereço de email do usuário
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



A função de projeto do usuário (&#39;admin&#39; ou &#39;viewer&#39;) ou a função específica do ambiente (por exemplo, &#39;principal:contributor&#39; ou &#39;stage:viewer&#39;). O caractere % pode ser usado como curinga na ID do ambiente, por exemplo &#39;%:viewer&#39;. A função pode ser abreviada, por exemplo &quot;principal:c&quot;.
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `user:delete`

Excluir um usuário do projeto

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

O endereço de email do usuário
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `user:get`

Exibir as funções de um usuário

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

O endereço de email do usuário
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



O nível da função (&#39;projeto&#39; ou &#39;ambiente&#39;)
- Requer um valor


### `--pipe`

Coloque a função em stdout (após fazer qualquer alteração)
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--role`, `-r`



[Obsoleto: usar user:atualizar para alterar as funções de um usuário]
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `user:list`

Listar usuários do projeto

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `user:update`

Atualizar funções de usuário em um projeto

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

O endereço de email do usuário
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



A função de projeto do usuário (&#39;admin&#39; ou &#39;viewer&#39;) ou a função específica do ambiente (por exemplo, &#39;principal:contributor&#39; ou &#39;stage:viewer&#39;). O caractere % pode ser usado como curinga na ID do ambiente, por exemplo &#39;%:viewer&#39;. A função pode ser abreviada, por exemplo &quot;principal:c&quot;.
- Padrão: `[]`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:create`

Criar uma variável

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



O nível no qual definir a variável (&#39;projeto&#39; ou &#39;ambiente&#39;)
- Requer um valor


### `--name`

O nome da variável
- Requer um valor


### `--value`

O valor da variável
- Requer um valor


### `--json`

Se a variável está formatada com JSON
- Padrão: `false`
- Requer um valor


### `--sensitive`

Se a variável é sensível
- Padrão: `false`
- Requer um valor


### `--prefix`

O prefixo do nome da variável (por exemplo, &#39;none&#39; ou &#39;env:&#39;)
- Padrão: `none`
- Requer um valor


### `--enabled`

Se a variável deve ser ativada
- Padrão: `true`
- Requer um valor


### `--inheritable`

Se a variável é herdada por ambientes filhos
- Padrão: `true`
- Requer um valor


### `--visible-build`

Se a variável deve estar visível no momento da criação
- Padrão: `true`
- Requer um valor


### `--visible-runtime`

Se a variável deve estar visível no tempo de execução
- Padrão: `true`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:delete`

Excluir uma variável

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



O nível da variável (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; ou &#39;e&#39;)
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Desativar uma variável de nível de ambiente ativada

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Ativar uma variável de nível de ambiente desativada

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:get`

Exibir uma variável

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Exibir uma única propriedade de variável
- Requer um valor



### `--level`, `-l`



O nível da variável (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; ou &#39;e&#39;)
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--pipe`

[Opção obsoleta] Coloque o valor da variável somente
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:list`

Variáveis da lista

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



O nível da variável (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; ou &#39;e&#39;)
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Definir uma variável para um ambiente

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument -->

### `value`

O valor da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Marcar o valor como JSON
- Padrão: `false`
- Não aceita um valor


### `--disabled`

Marque a variável como desabilitada
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `variable:update`

Atualizar uma variável

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

O nome da variável
- Obrigatório

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



O nível da variável (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; ou &#39;e&#39;)
- Requer um valor


### `--value`

O valor da variável
- Requer um valor


### `--json`

Se a variável está formatada com JSON
- Padrão: `false`
- Requer um valor


### `--sensitive`

Se a variável é sensível
- Padrão: `false`
- Requer um valor


### `--enabled`

Se a variável deve ser ativada
- Padrão: `true`
- Requer um valor


### `--inheritable`

Se a variável é herdada por ambientes filhos
- Padrão: `true`
- Requer um valor


### `--visible-build`

Se a variável deve estar visível no momento da criação
- Padrão: `true`
- Requer um valor


### `--visible-runtime`

Se a variável deve estar visível no tempo de execução
- Padrão: `true`
- Requer um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor



### `--no-wait`, `-W`



Não aguarde a conclusão da operação
- Padrão: `false`
- Não aceita um valor


### `--wait`

Aguarde a conclusão da operação (padrão)
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size -->

## `worker:list`

Obter uma lista de todos os trabalhadores implantados

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Se deseja atualizar o cache
- Padrão: `false`
- Não aceita um valor



### `--project`, `-p`



A ID ou URL do projeto
- Requer um valor


### `--host`

O nome do host da API do projeto
- Requer um valor



### `--environment`, `-e`



A ID do ambiente
- Requer um valor


### `--format`

O formato de saída (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)
- Padrão: `table`
- Requer um valor


### `--columns`

Colunas a serem exibidas (lista separada por vírgulas ou vários valores)
- Padrão: `[]`
- Requer um valor


### `--no-header`

Não produzir saída do cabeçalho da tabela
- Padrão: `false`
- Não aceita um valor



### `--help`, `-h`



Exibir esta mensagem de ajuda
- Padrão: `false`
- Não aceita um valor



### `--quiet`, `-q`



Não gerar nenhuma mensagem
- Padrão: `false`
- Não aceita um valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar a verbosidade das mensagens
- Padrão: `false`
- Não aceita um valor



### `--version`, `-V`



Exibir esta versão do aplicativo
- Padrão: `false`
- Não aceita um valor



### `--yes`, `-y`



Responder &quot;sim&quot; a qualquer pergunta sim/não; desativar interação
- Padrão: `false`
- Não aceita um valor



### `--no`, `-n`



Responder &quot;não&quot; a quaisquer perguntas &quot;sim/não&quot;; desativar interação
- Padrão: `false`
- Não aceita um valor <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->