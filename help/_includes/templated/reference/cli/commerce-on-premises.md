---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '8253'
ht-degree: 1%

---
# bin/magento (Adobe Systems Comércio no local)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Versão**: 2.4.8

Esta referência contém 145 comandos disponíveis através da ferramenta de linha de comando `bin/magento`.
A lista inicial é gerada automaticamente usando o comando `bin/magento list` na Adobe Commerce.

## Geral

Use o guia [&quot;Adicionar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) para adicionar um comando CLI personalizado.

Você pode chamar comandos CLI do `bin/magento` usando atalhos em vez do nome completo do comando. Por exemplo, você pode chamar `bin/magento setup:upgrade` usando `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxe de atalho](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para entender como usar atalhos com qualquer comando CLI.

Esta documentação de referência é gerada a partir do código-fonte do aplicativo. Para alterar a documentação, você deve abrir uma solicitação de pull para o comando correspondente no repositório [codebase](https://github.com/magento) relevante. Consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) para obter mais informações.

### Opções globais

#### `--help`, `-h`

Exibir ajuda para o comando determinado. Quando nenhum comando recebe ajuda de exibição para o comando lista

- Padrão: `false`
- Não aceita um valor

#### `--quiet`, `-q`

Não enviar nenhuma mensagem

- Inadimplência: `false`
- Não aceita um valor

#### `--verbose`, `-v|-vv|-vvv`

Aumentar a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

#### `--version`, `-V`

Exibir esta versão do aplicativo

- Inadimplência: `false`
- Não aceita um valor

#### `--ansi`

Forçar (ou desativar --no-ansi) a saída ANSI

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
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Comando interno para fornecer sugestões de conclusão de shell

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--shell`, `-s`

O tipo de shell (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Exige um valor

#### `--input`, `-i`

Uma matriz de tokens de entrada (por exemplo, COMP_WORDS ou argv)

- Inadimplência: `[]`
- Exige um valor

#### `--current`, `-c`

O índice da matriz de &quot;entrada&quot; em que o cursor está (por exemplo, COMP_CWORD)

- Exige um valor

#### `--api-version`, `-a`

A versão da API do script de conclusão

- Exige um valor

#### `--symfony`, `-S`

deprecado

- Exige um valor


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Despeje o script de conclusão do shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Exibir a ajuda de um comando

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumentos

#### `command_name`

O nome do comando

- Inadimplência: `help`

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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Listar comandos

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
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

- Inadimplência: `txt`
- Requer um valor

#### `--short`

Para ignorar a descrição dos argumentos dos comandos

- Padrão: `false`
- Não aceita um valor


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Desabilitar o módulo Adobe IMS

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Ativar o módulo Adobe IMS.

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--organization-id`, `-o`

Defina o ID da organização para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

#### `--client-id`, `-c`

Defina a ID do cliente para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

#### `--client-secret`, `-s`

Defina o segredo do cliente para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

#### `--2fa`, `-t`

Verifique se 2FA está ativado para Organização na Adobe Admin Console. Obrigatório ao habilitar o módulo

- Aceita um valor


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Informações de configuração do módulo Adobe IMS

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Status do módulo IMS da Adobe

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Cria um administrador

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--admin-user`

(Obrigatório) usuário do administrador

- Exige um valor

#### `--admin-password`

(Obrigatório) senha do administrador

- Requer um valor

#### `--admin-email`

(Obrigatório) Email do administrador

- Requer um valor

#### `--admin-firstname`

(Obrigatório) Nome do administrador

- Requer um valor

#### `--admin-lastname`

(Obrigatório) Sobrenome do administrador

- Requer um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar Magento parâmetros de inicialização Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Desbloquear Conta de Administrador

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### Argumentos

#### `username`

O nome de usuário do administrador a ser desbloqueado

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Criar despejo de aplicativo

### Argumentos

#### `config-types`

Lista separada por espaços de tipos de configuração ou omissão para despejar todos os [escopos, temas, sistema, i18n]

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Importar dados de arquivos de configuração compartilhados para o armazenamento de dados apropriado

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Verifica se a propagação de configuração requer atualização

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrar cartões armazenados de um banco de dados do Magento 1

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--host`

Nome do host/IP. A porta é opcional

- Exige um valor

#### `--dbname`

Nome do banco de dados

- Requer um valor

#### `--username`

Usuário do banco de dados. Deve ter acesso de leitura

- Requer um valor

#### `--password`

Senha

- Requer um valor


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Limpa os tipos de cache

### Argumentos

#### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

- Requer um valor


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Limpar cache de escopos de Comerciante de Serviços de Pagamento

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Desabilita os tipos de cache

### Argumentos

#### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

- Exige um valor


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Habilita o(s) tipo(s) de cache

### Argumentos

#### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

- Requer um valor


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Libera o armazenamento em cache usado pelo(s) tipo(s) de cache

### Argumentos

#### `types`

lista de tipos de cache separados por espaços ou omitir para aplicar a todos os tipos de cache.

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

- Requer um valor


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Verifica o status do cache

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

- Requer um valor


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Cria imagens de produtos redimensionadas

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--async`, `-a`

Redimensionar imagem no modo assíncrono

- Padrão: `false`
- Não aceita um valor

#### `--skip_hidden_images`

Não processar imagens marcadas como ocultas da página do produto

- Padrão: `false`
- Não aceita um valor


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Remove atributos de produto não utilizados.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Defina se deseja impor a validação de conteúdo do HTML do usuário ou mostrar um aviso

### Argumentos

#### `restrict`

y\n

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Definir valores de configuração confidenciais

### Argumentos

#### `path`

Caminho de configuração para exemplo group/section/field_name


#### `value`

Valor de configuração

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--interactive`, `-i`

Ativar o modo interativo para definir todas as variáveis confidenciais

- Padrão: `false`
- Não aceita um valor

#### `--scope`

Escopo para configuração, se não for definido, usar &quot;padrão&quot;

- Padrão: `default`
- Aceita um valor

#### `--scope-code`

Código do escopo da configuração, string vazia por padrão

- Padrão: &quot;&quot;
- Aceita um valor


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Alterar configuração do sistema

### Argumentos

#### `path`

Caminho de configuração na seção de formato/grupo/field_name

- Obrigatório


#### `value`

Valor de configuração

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--scope`

Escopo de configuração (padrão, site ou loja)

- Padrão: `default`
- Exige um valor

#### `--scope-code`

Código do escopo (obrigatório somente se escopo não for &#39;padrão&#39;)

- Exige um valor

#### `--lock-env`, `-e`

Valor de bloqueio que impede a modificação no Administrador (será salvo em app/etc/env.php)

- Padrão: `false`
- Não aceita um valor

#### `--lock-config`, `-c`

Bloquear e compartilhar valor com outras instalações, impede a modificação no Administrador (será salvo em app/etc/config.php)

- Padrão: `false`
- Não aceita um valor

#### `--lock`, `-l`

Obsoleto, use a opção — lock- env.

- Padrão: `false`
- Não aceita um valor


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Mostra o valor de configuração para determinado caminho. Se o caminho não for especificado, todos os valores salvos serão mostrados

### Argumentos

#### `path`

Caminho de configuração, por exemplo section_id/grupo_id/field_id

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--scope`

Escopo para configuração; se não especificado, o escopo &quot;padrão&quot; será usado

- Padrão: `default`
- Aceita um valor

#### `--scope-code`

Código do escopo (necessário somente se o escopo não for `default`)

- Padrão: &quot;
- Aceita um valor


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Gera e instala o crontab para o usuário atual

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Forçar tarefas de instalação

- Padrão: `false`
- Não aceita um valor

#### `--non-optional`, `-d`

Instalar somente as tarefas não opcionais (padrão)

- Inadimplência: `false`
- Não aceita um valor


## `cron:remove`

```bash
bin/magento cron:remove
```

Remove tarefas do crontab

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Executa tarefas por agendamento

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--group`

Executar tarefas somente a partir de grupo especificados

- Exige um valor

#### `--exclude-group`

Excluir trabalhos do grupo especificado

- Padrão: `[]`
- Aceita vários valores

#### `--bootstrap`

Adicionar ou substituir parâmetros da inicialização

- Requer um valor


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Atualize o hash do cliente de acordo com o algoritmo mais recente

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Defina o modo do aplicativo.

### Argumentos

#### `mode`

O modo de aplicativo a ser definido. As opções disponíveis são &quot;desenvolvedor&quot; ou &quot;produção&quot;

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--skip-compilation`, `-s`

Ignora a limpeza e a regeneração de conteúdo estático (código gerado, CSS pré-processado e ativos no pub/static/)

- Padrão: `false`
- Não aceita um valor


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Exibe o modo de aplicação atual.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Fornece informações sobre a configuração de Injeção de Dependência para o Comando.

### Argumentos

#### `class`

Nome da classe

- Obrigatório


#### `area`

Código de área

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Verifica modelos de boletim informativo em busca de possíveis problemas de compatibilidade com o uso de variáveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Verifica substituições de modelo de email em possíveis problemas variável de compatibilidade de uso

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Desative o profiler.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Ative o profiler.

### Argumentos

#### `type`

Tipo de profiler

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Desabilitar log de consultas do BD

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Habilitar log de consultas do BD

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--include-all-queries`

Registra todas as consultas. [true\|false]

- Padrão: `true`
- Aceita um valor

#### `--query-time-threshold`

Limites de tempo de consulta.

- Padrão: `0.001`
- Aceita um valor

#### `--include-call-stack`

Incluir pilha de chamadas. [true\|false]

- Padrão: `true`
- Aceita um valor


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Coleta e publica arquivos de origem para o tema.

### Argumentos

#### `file`

Arquivos a serem pré-processados (o arquivo deve ser especificado sem a extensão)

- Padrão: `css/styles-mcss/styles-l`

- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--type`

Tipo de arquivos de origem: [less]

- Padrão: `less`
- Requer um valor

#### `--locale`

Localidade: [en_US]

- Inadimplência: `en_US`
- Exige um valor

#### `--area`

Área: [frontend\|adminhtml]

- Padrão: `frontend`
- Requer um valor

#### `--theme`

Tema: [Fornecedor/tema]

- Inadimplência: `Magento/luma`
- Exige um valor


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Desative as dicas de modelo do frontend. Uma liberação do cache pode ser necessária.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Ativar dicas de modelo de front-end. Uma liberação de cache pode ser necessária.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Mostrar status das dicas do modelo de front-end.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Executa testes

### Argumentos

#### `type`

Tipo de teste a ser executado. Tipos disponíveis: tudo, unidade, integração, integração-tudo, estático, estático-tudo, integridade, herdado, padrão

- Padrão: `default`

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--arguments`, `-c`

Argumentos adicionais para PHPUnit. Exemplo: &quot;-c&#39;--filter=MyTest&#39;&quot; (sem espaços)

- Padrão: &quot;&quot;
- Exige um valor


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Gera o catálogo de URNs para mapeamentos *.xsd para o IDE destacar xml.

### Argumentos

#### `path`

Caminho do arquivo para a saída do catálogo. Para o PhpStorm, use .idea/misc.xml

- Necessário

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--ide`

Formato no qual o catálogo será gerado. Com suporte: [phpstorm, vscode]

- Padrão: `phpstorm`
- Requer um valor


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Converte arquivo XML usando folhas de estilo XSL

### Argumentos

#### `xml-file`

Caminho para o arquivo XML que será transformado

- Necessário


#### `processor`

Caminho para a folha de estilos XSL que será aplicada ao arquivo XML

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--overwrite`, `-o`

Substituir arquivo XML

- Inadimplência: `false`
- Não aceita um valor


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Adicionar domínios à lista de permissões de domínios baixáveis

### Argumentos

#### `domains`

Nome dos domínios

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Remover domínios da lista de permissões de domínios baixáveis

### Argumentos

#### `domains`

Nomes de domínio

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Exibir lista de permissões de domínios baixáveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Mostra uma lista de criptografadores de dados novos disponíveis.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Criptografa novamente os dados criptografados usando a chave de criptografia atual.

### Argumentos

#### `encryptors`

Lista separada por espaços de re-criptografadores a serem usados.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Altere a chave de criptografia dentro do arquivo env.php.

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--key`, `-k`

A chave deve ter uma sequência de 32 caracteres. Se não for fornecida, uma chave aleatória será gerada.

- Aceita um valor


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Criptografa novamente os dados criptografados do cartão de crédito com a cifra de criptografia mais recente.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Crie um provedor de eventos personalizado no Adobe I/O Events para esta instância. Se você não especificar as opções de rótulo e descrição, elas deverão ser definidas no arquivo de sistema app/etc/event-types.json.

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--label`

Um rótulo para definir seu provedor personalizado.

- Aceita um valor

#### `--description`

Uma descrição do provedor.

- Aceita um valor


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Gerar módulo com base na lista de plug-ins

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Retorna a carga do evento especificado.

### Argumentos

#### `event-code`

Código do evento

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--depth`

O número de níveis na carga útil do evento a ser retornada

- Padrão: `2`
- Aceita um valor


## `events:list`

```bash
bin/magento events:list
```

Mostra a lista de eventos inscritos

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Retorna uma lista de eventos subscritáveis definidos na módulo especificada.

### Argumentos

#### `module_name`

Nome do módulo

- Necessário

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Cria metadados no Adobe Systems E/S a partir da lista de configuração (configurações XML e aplicativo)

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Retorna detalhes sobre o provedor de evento configurado

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Lista registros de eventos no seu projeto do App Builder

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Assina o evento

### Argumentos

#### `event-code`

Código do evento

- Necessário

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Força a inscrição do evento especificado, mesmo que ele não tenha sido definido localmente.

- Padrão: `false`
- Não aceita um valor

#### `--fields`

A lista de campos na carga de dados do evento.

- Padrão: `[]`
- Requer um valor

#### `--parent`

O código de evento pai de uma assinatura de evento com regras ou como um alias.

- Requer um valor

#### `--rules`

A lista de regras para a assinatura do evento, em que cada regra é formatada como &quot;campo\|operador\|valor&quot;. Para usar essa opção, você também deve especificar a opção &quot;pai&quot;.

- Inadimplência: `[]`
- Exige um valor

#### `--priority`, `-p`

Acelera a transmissão desse evento. Especifique essa opção para eventos que precisam ser entregues imediatamente. Por padrão, os eventos são enviados pelo cron uma vez por minuto.

- Padrão: `false`
- Não aceita um valor

#### `--destination`, `-d`

O destino deste evento. Especifique essa opção para os eventos que devem ser entregues ao destino personalizado.

- Padrão: `default`
- Requer um valor

#### `--hipaaAuditRequired`

Indica que o evento contém dados sujeitos à auditoria da HIPAA.

- Padrão: `false`
- Não aceita um valor


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Sincronizar metadados de evento para esta instância

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--delete`, `-d`

A exclusão de metadados de eventos não é mais necessária

- Padrão: `false`
- Não aceita um valor


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Remove a assinatura do evento fornecido

### Argumentos

#### `event-code`

Código de evento do qual cancelar inscrição

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Descobre frases na base de código

### Argumentos

#### `directory`

Caminho do diretório para análise. Não é necessário se o sinalizador — magento estiver ativo

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Caminho (incluindo o nome do arquivo) para um arquivo de saída. Sem nenhum arquivo especificado, o padrão é stdout.

- Requer um valor

#### `--magento`, `-m`

Use o parâmetro —magento para analisar a base de código atual do Magento. Omita o parâmetro se um diretório for especificado.

- Padrão: `false`
- Não aceita um valor


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Salva o pacote de idioma

### Argumentos

#### `source`

Caminho para o arquivo do dicionário de origem com traduções

- Obrigatório


#### `locale`

Local de destino do dicionário, por exemplo &quot;de_DE&quot;

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--mode`, `-m`

Modo de salvamento do dicionário - &quot;substituir&quot; - substituir o pacote de idiomas por um novo - &quot;mesclar&quot; - mesclar pacotes de idiomas, por padrão &quot;substituir&quot;

- Padrão: `replace`
- Requer um valor

#### `--allow-duplicates`, `-d`

Use o parâmetro —allow-duplicates para permitir o salvamento de duplicatas de translate. Caso contrário, omita o parâmetro.

- Padrão: `false`
- Não aceita um valor


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Desinstala pacotes de idiomas

### Argumentos

#### `package`

Nome do pacote de idioma

- Padrão: `[]`
- Obrigatório

- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--backup-code`, `-b`

Fazer backup de arquivos de código e configuração (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor


## `indexer:info`

```bash
bin/magento indexer:info
```

Mostra os Indexadores permitidos

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Reindexa dados

### Argumentos

#### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Redefine o status do indexador para inválido

### Argumentos

#### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Definir modo de dimensões do indexador

### Argumentos

#### `indexer`

Nome [do indexador catalog_product_price|catalogpermissions_categoria]


#### `mode`

Modos de dimensão do indexador catalog_product_price          nenhum,site,customer_group,website_and_customer_group catalogpermissions_category    nenhum,customer_group

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Define o tipo de modo de índice

### Argumentos

#### `mode`

Tipo de modo [de indexador em tempo real|programação]


#### `index`

lista de tipos de índice separados por espaços ou omitir para aplicar a todos os índices.

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Define o status do indexador especificado

### Argumentos

#### `status`

Tipo de status do indexador [inválido|suspenso|válido]

- Obrigatório


#### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Mostra O Modo Dimension Do Indexador

### Argumentos

#### `indexer`

lista de tipos de índice separados por espaços ou omitir para aplicar a todos os índices (catalog_product_price,catalogpermissions_categoria)

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Mostra o modo de índice

### Argumentos

#### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Mostra o status do Indexador

### Argumentos

#### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Exibe o URI do administrador do Magento

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Imprime a lista de arquivos de backup disponíveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Exibe a lista de moedas disponíveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Mostra o número de dependências na estrutura do Magento

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Nome do arquivo do relatório

- Padrão: `framework-dependencies.csv`
- Requer um valor


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Mostra o número de dependências entre módulos

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Nome do arquivo do relatório

- Padrão: `modules-dependencies.csv`
- Requer um valor


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Mostra o número de dependências circulares entre módulos

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--output`, `-o`

Nome do arquivo de relatório

- Inadimplência: `modules-circular-dependencies.csv`
- Requer um valor


## `info:language:list`

```bash
bin/magento info:language:list
```

Exibe a lista de localidades de idioma disponíveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Exibe a lista de fusos horários disponíveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Criar reservas por argumentos de remuneração fornecidos

### Argumentos

#### `compensations`

Lista de argumentos de compensação no formato &quot;::&quot;

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--raw`, `-r`

Saída bruta

- Padrão: `false`
- Não aceita um valor


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Exibir todos os pedidos e produtos com inconsistências saláveis quantidade

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--complete-orders`, `-c`

Mostrar apenas inconsistências para pedidos completos

- Padrão: `false`
- Não aceita um valor

#### `--incomplete-orders`, `-i`

Exibir somente inconsistências de pedidos incompletos

- Inadimplência: `false`
- Não aceita um valor

#### `--bunch-size`, `-b`

Define quantos pedidos serão carregados de uma vez

- Padrão: `50`
- Aceita um valor

#### `--raw`, `-r`

Saída bruta

- Inadimplência: `false`
- Não aceita um valor


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Baixe e importe nomes geográficos para o algoritmo de seleção de origem

### Argumentos

#### `countries`

Lista de códigos de país a serem importados

- Padrão: `[]`
- Obrigatório

- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Define o modo de manutenção de IPs isentos

### Argumentos

#### `ip`

Endereços IP permitidos

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--none`

Limpar endereços IP permitidos

- Inadimplência: `false`
- Não aceita um valor

#### `--add`

Adicionar o endereço IP à lista existente

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Desabilita o modo de manutenção

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--ip`

Endereços IP permitidos (use &quot;nenhum&quot; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Exige um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Ativa o modo de manutenção

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--ip`

Endereços IP permitidos (use &quot;nenhum&quot; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Requer um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Exibe o status do modo de manutenção

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Sincronizar conteúdo com o ativos

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Sincronizar mídia armazenamento e mídia ativos no banco de dados

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Verifica a configuração dos módulos no arquivo &quot;app/etc/config.php&quot; e informa se eles estão atualizados ou não

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Desativa módulos especificados

### Argumentos

#### `module`

Nome do módulo

- Inadimplência: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Ignorar verificação de dependências

- Padrão: `false`
- Não aceita um valor

#### `--all`

Desativar todos os módulos

- Padrão: `false`
- Não aceita um valor

#### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados. Necessário, se o(s) módulo(s) tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Habilita módulos especificados

### Argumentos

#### `module`

Nome do módulo

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Verificação de dependências de bypass

- Padrão: `false`
- Não aceita um valor

#### `--all`

Habilitar todos os módulos

- Padrão: `false`
- Não aceita um valor

#### `--clear-static-content`, `-c`

Limpe os arquivos de visualização estáticos gerados. Necessário, se as módulo tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar Magento parâmetros de inicialização Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Exige um valor


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Exibe o status dos módulos

### Argumentos

#### `module-names`

Nome do módulo opcional

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--enabled`

Impressão somente módulos habilitados

- Padrão: `false`
- Não aceita um valor

#### `--disabled`

Imprimir somente módulos desabilitados

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Desinstala módulos instalados pelo compositor

### Argumentos

#### `module`

Nome do módulo

- Inadimplência: `[]`
- Necessário

- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--remove-data`, `-r`

Remover dados instalados pelos módulos

- Padrão: `false`
- Não aceita um valor

#### `--backup-code`

Use arquivos de código e configuração backup (excluindo arquivos temporários)

- Inadimplência: `false`
- Não aceita um valor

#### `--backup-media`

Fazer backup de mídia

- Padrão: `false`
- Não aceita um valor

#### `--backup-db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

#### `--non-composer`

Todos os módulos, que serão passados aqui, serão não baseados em compositor

- Padrão: `false`
- Não aceita um valor

#### `--clear-static-content`, `-c`

Limpe os arquivos de visualização estáticos gerados. Necessário, se o(s) módulo(s) tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Verifique se há entradas na fila de implantação e crie um marcador de implantação apropriado.

### Argumentos

#### `message`

Implantar Enviar mensagem?

- Obrigatório


#### `change_log`

Registro de alterações?

- Obrigatório


#### `user`

Usuário de implantação


#### `revision`

Revisão

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lista de consumidores do MessageQueue

```
This command shows list of MessageQueue consumers.
```

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Reiniciar consumidores do MessageQueue

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Iniciar consumidor MessageQueue

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### Argumentos

#### `consumer`

O nome do consumidor a ser iniciado.

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--max-messages`

O número de mensagens a serem processadas pelo consumidor antes do término do processo. Se não for especificado - finalizar após o processamento de todas as mensagens em fila.

- Requer um valor

#### `--batch-size`

O número de mensagens por lote. Aplicável somente para o consumidor do lote.

- Requer um valor

#### `--area-code`

O padrão da área preferida (global, adminhtml, etc.) é global.

- Requer um valor

#### `--single-thread`

Essa opção impede a execução de várias cópias de um consumidor simultaneamente.

- Padrão: `false`
- Não aceita um valor

#### `--multi-process`

O número de processos por consumidor.

- Aceita um valor

#### `--pid-file-path`

O caminho do arquivo para salvar o PID (Esta opção está obsoleta, use — single- thread)

- Requer um valor


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Sincronizar arquivos de mídia com o armazenamento remoto.

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Sincroniza novamente os dados do feed com o serviço SaaS.

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--feed`

Nome do feed para ressincronização completa com o serviço SaaS. Feeds disponíveis: Payment Services Order Production, Payment Services Order Sandbox, Payment Services Order Status Production, Payment Services Order Status Sandbox, Payment Services Order Status Sandbox, Payment Services Store Production, Sandbox de armazenamento de serviços de pagamento

- Requer um valor

#### `--no-reindex`

Execute o reenvio de dados de feed somente para o serviço SaaS. Não reindexa. (Esta opção não se aplica aos produtos, substituições de produtos, feeds de preços)

- Padrão: `false`
- Não aceita um valor

#### `--cleanup-feed`

Força a limpeza da tabela indexadora de feed antes da sincronização.

- Padrão: `false`
- Não aceita um valor

#### `--dry-run`

Pista seca. Os dados não serão exportados. Para salvar a carga no arquivo de log var/log/saas-export.log, execute com a variável env EXPORTER_EXTENDED_LOG=1.

- Padrão: `false`
- Não aceita um valor

#### `--thread-count`

Definir contagem de threads de sincronização.

- Requer um valor

#### `--batch-size`

Definir o tamanho do lote de sincronização

- Exige um valor

#### `--continue-resync`

Continuar ressincronizar da última posição armazenada (esta opção é aplicável aos produtos, productoverrides, feeds de preços)

- Inadimplência: `false`
- Não aceita um valor

#### `--by-ids`

Sincronizar parcialmente por lista de identificadores fornecidos. (Esta opção é aplicável aos feeds de produtos, substituições e preços)

- Exige um valor

#### `--id-type`

Tipo de identificadores para ressíncrona parcial (por exemplo: sku, productId etc)

- Exige um valor


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Implantar módulos de dados de amostra para instalações de Magento baseadas em compositor

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--no-update`

Atualizar composer.json sem executar a atualização do composer

- Padrão: `false`
- Não aceita um valor


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Remover todos os pacotes de dados de amostra do composer.json

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--no-update`

Atualizar composer.json sem executar a atualização do composer

- Padrão: `false`
- Não aceita um valor


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Redefina todos os módulos de dados de amostra para reinstalação

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Desativar o reCAPTCHA para o formulário de senha esquecida do usuário administrador

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Desabilitar reCAPTCHA para o formulário de logon de usuário administrador

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Defina o segredo usado para a geração de OTP do Google.

### Argumentos

#### `user`

Nome de usuário

- Necessário


#### `secret`

Segredo

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Listar todos os provedores disponíveis

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Redefinir configuração de um usuário

### Argumentos

#### `user`

Nome de usuário

- Necessário


#### `provider`

Código do provedor

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Executar servidor de aplicativos

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--port`, `-p`

porta para atender

- Padrão: `9501`
- Aceita um valor

#### `--background`, `-b`

sinalizador de modo de plano de fundo

- Padrão: `0`
- Aceita um valor

#### `--workerNum`, `-wn`

número de processos de trabalho a serem iniciados

- Padrão: `4`
- Aceita um valor

#### `--dispatchMode`, `-dm`

modo de distribuição de conexões para os processos de trabalho

- Padrão: `3`
- Aceita um valor

#### `--maxRequests`, `-mr`

máximo de solicitações antes que o processo de trabalho fosse reiniciado

- Padrão: `10000`
- Aceita um valor

#### `--area`, `-a`

área do servidor de aplicativos

- Padrão: `graphql`
- Aceita um valor

#### `--magento-init-params`, `-mip`

parâmetros de inicialização do magento bootstrap

- Padrão: &quot;
- Aceita um valor

#### `--maxWaitTime`, `-mwt`

quanto tempo esperar pelos trabalhadores após recarregar (por exemplo, mudança de configuração) antes de matá-los

- Inadimplência: `3600`
- Aceita um valor

#### `--state-monitor`

Habilitar monitoramento de estado. Use isso somente para problemas de estado de depuração!

- Padrão: `false`
- Não aceita um valor


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Saída agregada do monitor de estado do ApplicationServer

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Obtém backup de Magento base de código do aplicativo, mídia e banco de dados

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--code`

Use arquivos de código e configuração backup (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

#### `--media`

Fazer backup de mídia

- Padrão: `false`
- Não aceita um valor

#### `--db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Cria ou modifica a configuração de implantação

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

#### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

#### `--remote-storage-endpoint`

Ponto de extremidade de armazenamento remoto

- Requer um valor

#### `--remote-storage-bucket`

Compartimento de armazenamento remoto

- Requer um valor

#### `--remote-storage-region`

Região de armazenamento remoto

- Exige um valor

#### `--remote-storage-key`

Chave de acesso armazenamento remota

- Padrão: &quot;&quot;
- Exige um valor

#### `--remote-storage-secret`

Chave secreta do armazenamento remoto

- Padrão: &quot;
- Requer um valor

#### `--remote-storage-path-style`

Estilo do caminho do armazenamento remoto

- Inadimplência: `0`
- Exige um valor

#### `--backend-frontname`

Nome do frontname do back-end (será gerado automaticamente se estiver faltando)

- Requer um valor

#### `--enable-debug-logging`

Habilitar log de depuração

- Requer um valor

#### `--enable-syslog-logging`

Habilitar registro do syslog

- Requer um valor

#### `--id_salt`

Sal GraphQl

- Requer um valor

#### `--checkout-async`

Habilitar processamento assíncrono de pedidos? 1 - Sim, 0 - Não

- Requer um valor

#### `--config-async`

Habilitar Salvar Configuração de Administração assíncrona? 1 - Sim, 0 - Não

- Requer um valor

#### `--amqp-host`

Host do servidor Amqp

- Padrão: &quot;
- Requer um valor

#### `--amqp-port`

Porta do servidor Amqp

- Padrão: `5672`
- Requer um valor

#### `--amqp-user`

Nome de usuário do servidor Amqp

- Padrão: &quot;
- Requer um valor

#### `--amqp-password`

Senha do servidor Amqp

- Padrão: &quot;
- Requer um valor

#### `--amqp-virtualhost`

Virtualhost Amqp

- Padrão: `/`
- Requer um valor

#### `--amqp-ssl`

Amqp SSL

- Padrão: &quot;
- Requer um valor

#### `--amqp-ssl-options`

Opções de SSL Amqp (JSON)

- Padrão: &quot;
- Requer um valor

#### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

#### `--queue-default-connection`

Conexão padrão de filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve estar instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

#### `--deferred-total-calculating`

Ativar cálculo de total adiado? 1 - Sim, 0 - Não

- Requer um valor

#### `--key`

Chave de criptografia

- Requer um valor

#### `--db-host`

Host do servidor de banco de dados

- Requer um valor

#### `--db-name`

Nome do banco de dados

- Requer um valor

#### `--db-user`

Usuário do servidor de banco de dados

- Requer um valor

#### `--db-engine`

Mecanismo do servidor de banco de dados

- Requer um valor

#### `--db-password`

Senha do servidor de banco de dados

- Requer um valor

#### `--db-prefix`

Prefixo da tabela do banco de dados

- Requer um valor

#### `--db-model`

Tipo de banco de dados

- Requer um valor

#### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Requer um valor

#### `--skip-db-validation`, `-s`

Se especificado, a validação da conexão com o banco de dados será ignorada

- Padrão: `false`
- Não aceita um valor

#### `--http-cache-hosts`

hosts de cache http

- Requer um valor

#### `--db-ssl-key`

Caminho completo do arquivo de chave do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

#### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

#### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

#### `--db-ssl-verify`

Verificar certificação do servidor

- Padrão: `false`
- Não aceita um valor

#### `--session-save`

Manipulador de salvamento de sessão

- Exige um valor

#### `--session-save-redis-host`

Nome de host totalmente qualificado, endereço IP ou caminho absoluto se estiver usando soquetes UNIX

- Requer um valor

#### `--session-save-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--session-save-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--session-save-redis-timeout`

Tempo limite da conexão, em segundos

- Exige um valor

#### `--session-save-redis-retries`

Redis conexão tentativas.

- Requer um valor

#### `--session-save-redis-persistent-id`

Sequência de caracteres exclusiva para habilitar conexões persistentes

- Requer um valor

#### `--session-save-redis-db`

Número do banco de dados Redis

- Requer um valor

#### `--session-save-redis-compression-threshold`

Limite de compactação Redis

- Requer um valor

#### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

#### `--session-save-redis-log-level`

Nível de log Redis. Valores: 0 (menos explícito) a 7 (mais explícito)

- Requer um valor

#### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar um bloqueio em uma sessão

- Exige um valor

#### `--session-save-redis-break-after-frontend`

Número de segundos a serem esperados antes de tentar quebrar um bloqueio para a sessão de frontend

- Exige um valor

#### `--session-save-redis-break-after-adminhtml`

Número de segundos a serem esperados antes de tentar interromper um bloqueio para a sessão administrativa

- Requer um valor

#### `--session-save-redis-first-lifetime`

Tempo de vida, em segundos, da sessão para não bots na primeira gravação (use 0 para desativar)

- Requer um valor

#### `--session-save-redis-bot-first-lifetime`

Tempo de vida, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

#### `--session-save-redis-bot-lifetime`

Duração da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

#### `--session-save-redis-disable-locking`

Redis desabilita o bloqueio. Valores: falso (padrão), verdadeiro

- Requer um valor

#### `--session-save-redis-min-lifetime`

Tempo de vida mínimo da sessão Redis, em segundos

- Exige um valor

#### `--session-save-redis-max-lifetime`

Tempo de vida máximo da sessão do Redis, em segundos

- Requer um valor

#### `--session-save-redis-sentinel-master`

Redis Sentinel mestre

- Requer um valor

#### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgula

- Requer um valor

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica o mestre. Valores: falso (padrão), verdadeiro

- Requer um valor

#### `--session-save-redis-sentinel-connect-retries`

Tentativas de conexão do Redis Sentinel.

- Requer um valor

#### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

#### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

#### `--cache-backend-redis-db`

Número do banco de dados do cache

- Requer um valor

#### `--cache-backend-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--cache-backend-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--cache-backend-redis-compress-data`

Defina como 0 para desativar a compactação (o padrão é 1, ativado)

- Requer um valor

#### `--cache-backend-redis-compression-lib`

Biblioteca de compactação para usar [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

#### `--cache-backend-redis-use-lua`

Defina como 1 para ativar lua (o padrão é 0, desativado)

- Requer um valor

#### `--cache-backend-redis-use-lua-on-gc`

Defina como 0 para desativar lua na coleção de lixo (o padrão é 1, ativado)

- Exige um valor

#### `--cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

#### `--allow-parallel-generation`

Permitir gerar cache de forma não bloqueada

- Padrão: `false`
- Não aceita um valor

#### `--page-cache`

Manipulador de cache padrão

- Requer um valor

#### `--page-cache-redis-server`

Servidor Redis

- Requer um valor

#### `--page-cache-redis-db`

Número do banco de dados do cache

- Requer um valor

#### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página inteira (use 0 para desativar)

- Requer um valor

#### `--page-cache-redis-compression-lib`

Biblioteca de compactação para usar [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

#### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

#### `--lock-provider`

Nome do provedor de bloqueio

- Requer um valor

#### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

#### `--lock-zookeeper-host`

Host e porta para conexão com o cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

#### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/locks

- Requer um valor

#### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Exige um valor

#### `--document-root-is-pub`

Sinalizador para mostrar é Pub está na raiz, pode ser verdadeiro ou falso apenas

- Exige um valor

#### `--backpressure-logger`

Manipulador do agente de log do backpressure

- Exige um valor

#### `--backpressure-logger-redis-server`

Servidor Redis

- Requer um valor

#### `--backpressure-logger-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--backpressure-logger-redis-timeout`

Tempo limite do servidor Redis

- Requer um valor

#### `--backpressure-logger-redis-persistent`

Redis persistente

- Requer um valor

#### `--backpressure-logger-redis-db`

Número do banco de dados Redis

- Requer um valor

#### `--backpressure-logger-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--backpressure-logger-redis-user`

Usuário do servidor Redis

- Requer um valor

#### `--backpressure-logger-id-prefix`

Prefixo de ID para chaves

- Requer um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala e atualiza dados no BD

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Gere o patch e coloque-o na pasta específica.

### Argumentos

#### `module`

Nome do módulo

- Obrigatório


#### `patch`

Nome do patch

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--revertable`

Verifique se o patch é reversível ou não.

- Padrão: `false`
- Aceita um valor

#### `--type`

Descubra que tipo de patch deve ser gerado. Valores disponíveis: `data`, `schema`.

- Inadimplência: `data`
- Aceita um valor


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Gerar lista de permissões de tabelas e colunas que podem ser editadas pelo instalador de declaração

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--module-name`

Nome do módulo onde a lista de permissões será gerada

- Padrão: `all`
- Aceita um valor


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mover tabelas relacionadas à cotação de check-out para um servidor de banco de dados separado

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--host`

Host do Servidor BD Escravo

- Padrão: `localhost`
- Requer um valor

#### `--dbname`

Nome do Banco de Dados Secundário

- Requer um valor

#### `--username`

Nome do usuário subordinado do DB

- Padrão: `root`
- Requer um valor

#### `--password`

Senha de usuário do BD subordinado

- Aceita um valor

#### `--connection`

Nome da conexão subordinada

- Inadimplência: `default`
- Aceita um valor

#### `--resource`

Nome do recurso subordinado

- Inadimplência: `default`
- Aceita um valor

#### `--maxAllowedLag`

Máximo de Conexões Lag Slave Permitidas (em segundos)

- Padrão: &quot;
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mover tabelas relacionadas à cotação de check-out para um servidor de banco de dados separado. Obsoleto desde a versão 2.4.2 e será removido

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--host`

Verificar host do Servidor de BD

- Exige um valor

#### `--dbname`

Nome do banco de dados de check-out

- Exige um valor

#### `--username`

Fazer check-out do nome de usuário do BD

- Requer um valor

#### `--password`

Fazer check-out da senha de usuário do BD

- Aceita um valor

#### `--connection`

Fazer check-out do nome da conexão

- Padrão: `checkout`
- Aceita um valor

#### `--resource`

Fazer check-out do nome do recurso

- Padrão: `checkout`
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mover tabelas relacionadas a vendas para um servidor do BD separado. Obsoleto desde a versão 2.4.2 e será removido

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--host`

Host do servidor do banco de dados de vendas

- Requer um valor

#### `--dbname`

Nome do Banco de Dados de Vendas

- Requer um valor

#### `--username`

Nome de usuário do BD de Vendas

- Requer um valor

#### `--password`

Senha do usuário do BD de Vendas

- Aceita um valor

#### `--connection`

Nome da conexão de vendas

- Padrão: `sales`
- Aceita um valor

#### `--resource`

Nome do recurso de vendas

- Padrão: `sales`
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala e atualiza o esquema do BD

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verifica se o esquema ou os dados do banco de dados exigem atualização

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--magento-init-params`

Adicione a qualquer comando para personalizar Magento parâmetros de inicialização Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Exige um valor


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Gera a configuração de DI e todas as classes ausentes que podem ser geradas automaticamente

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala o aplicativo do Magento

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

#### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

#### `--remote-storage-endpoint`

Ponto de extremidade de armazenamento remoto

- Requer um valor

#### `--remote-storage-bucket`

Compartimento de armazenamento remoto

- Exige um valor

#### `--remote-storage-region`

Região de armazenamento remoto

- Requer um valor

#### `--remote-storage-key`

Chave de acesso do armazenamento remoto

- Padrão: &quot;
- Requer um valor

#### `--remote-storage-secret`

Chave secreta do armazenamento remoto

- Padrão: &quot;
- Requer um valor

#### `--remote-storage-path-style`

Estilo do caminho de armazenamento remoto

- Padrão: `0`
- Requer um valor

#### `--backend-frontname`

Nome do frontname do back-end (será gerado automaticamente se estiver faltando)

- Requer um valor

#### `--enable-debug-logging`

Ativar fazendo logon de depurar

- Exige um valor

#### `--enable-syslog-logging`

Ativar fazendo logon de syslog

- Requer um valor

#### `--id_salt`

Sal GraphQl

- Requer um valor

#### `--checkout-async`

Habilitar processamento assíncrono de pedidos? 1 - Sim, 0 - Não

- Exige um valor

#### `--config-async`

Ativar Salvar de configuração de administrador assíncrona? 1 - Sim, 0 - Não

- Exige um valor

#### `--amqp-host`

host do servidor Amqp

- Padrão: &quot;&quot;
- Requer um valor

#### `--amqp-port`

Porta do servidor Amqp

- Padrão: `5672`
- Requer um valor

#### `--amqp-user`

Nome de usuário do servidor Amqp

- Padrão: &quot;&quot;
- Exige um valor

#### `--amqp-password`

senha do servidor Amqp

- Padrão: &quot;&quot;
- Exige um valor

#### `--amqp-virtualhost`

Virtualhost Amqp

- Inadimplência: `/`
- Exige um valor

#### `--amqp-ssl`

Amqp SSL

- Padrão: &quot;&quot;
- Exige um valor

#### `--amqp-ssl-options`

Opções de SSL Amqp (JSON)

- Padrão: &quot;
- Requer um valor

#### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

#### `--queue-default-connection`

Conexão padrão de filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve estar instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

#### `--deferred-total-calculating`

Ativar cálculo de total adiado? 1 - Sim, 0 - Não

- Requer um valor

#### `--key`

Chave de criptografia

- Requer um valor

#### `--db-host`

Host do servidor de banco de dados

- Requer um valor

#### `--db-name`

Nome do banco de dados

- Requer um valor

#### `--db-user`

Usuário do servidor de banco de dados

- Requer um valor

#### `--db-engine`

Mecanismo do servidor do banco de dados

- Exige um valor

#### `--db-password`

senha do servidor de banco de dados

- Exige um valor

#### `--db-prefix`

Prefixo da tabela do banco de dados

- Requer um valor

#### `--db-model`

Tipo de banco de dados

- Requer um valor

#### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Exige um valor

#### `--skip-db-validation`, `-s`

Se especificado, a validação de conexão db será ignorada

- Inadimplência: `false`
- Não aceita um valor

#### `--http-cache-hosts`

hosts http Cache

- Exige um valor

#### `--db-ssl-key`

Caminho completo do arquivo chave do cliente no solicitar para estabelecer a conexão db por meio de SSL

- Padrão: &quot;&quot;
- Exige um valor

#### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente no solicitar para estabelecer a conexão db por meio de SSL

- Padrão: &quot;
- Requer um valor

#### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

#### `--db-ssl-verify`

Verificar certificação do servidor

- Padrão: `false`
- Não aceita um valor

#### `--session-save`

Manipulador de salvamento de sessão

- Requer um valor

#### `--session-save-redis-host`

Nome de host totalmente qualificado, endereço IP ou caminho absoluto se estiver usando soquetes UNIX

- Requer um valor

#### `--session-save-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--session-save-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--session-save-redis-timeout`

Tempo limite da conexão, em segundos

- Requer um valor

#### `--session-save-redis-retries`

Redefine tentativas de conexão.

- Requer um valor

#### `--session-save-redis-persistent-id`

Sequência de caracteres exclusiva para habilitar conexões persistentes

- Exige um valor

#### `--session-save-redis-db`

Número do banco de dados redis

- Exige um valor

#### `--session-save-redis-compression-threshold`

Redisca o limite de compactação

- Requer um valor

#### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

#### `--session-save-redis-log-level`

Nível de log Redis. Valores: 0 (menos explícito) a 7 (mais explícito)

- Exige um valor

#### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar por um bloqueio em uma sessão

- Requer um valor

#### `--session-save-redis-break-after-frontend`

Número de segundos a aguardar antes de tentar interromper um bloqueio para uma sessão de front-end

- Requer um valor

#### `--session-save-redis-break-after-adminhtml`

Número de segundos a serem esperados antes de tentar interromper um bloqueio para a sessão administrativa

- Exige um valor

#### `--session-save-redis-first-lifetime`

Duração, em segundos, da sessão para não-bots na primeira gravação (use 0 para desativar)

- Exige um valor

#### `--session-save-redis-bot-first-lifetime`

Duração, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

#### `--session-save-redis-bot-lifetime`

Duração da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

#### `--session-save-redis-disable-locking`

Reativar o bloqueio. Valores: false (padrão), true

- Exige um valor

#### `--session-save-redis-min-lifetime`

Tempo de vida mínimo da sessão Redis, em segundos

- Requer um valor

#### `--session-save-redis-max-lifetime`

Tempo de vida máximo da sessão do Redis, em segundos

- Requer um valor

#### `--session-save-redis-sentinel-master`

Redis Sentinel mestre

- Requer um valor

#### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgula

- Requer um valor

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica o mestre. Valores: falso (padrão), verdadeiro

- Exige um valor

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conectou-se tentativas.

- Exige um valor

#### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

#### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

#### `--cache-backend-redis-db`

Número do banco de dados do cache

- Exige um valor

#### `--cache-backend-redis-port`

Porta de escuta do servidor Redis

- Exige um valor

#### `--cache-backend-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--cache-backend-redis-compress-data`

Defina como 0 para desativar a compactação (o padrão é 1, ativado)

- Requer um valor

#### `--cache-backend-redis-compression-lib`

Biblioteca de compactação para usar [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

#### `--cache-backend-redis-use-lua`

Defina como 1 para ativar lua (o padrão é 0, desativado)

- Requer um valor

#### `--cache-backend-redis-use-lua-on-gc`

Defina como 0 para desativar lua na coleta de lixo (o padrão é 1, ativado)

- Requer um valor

#### `--cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

#### `--allow-parallel-generation`

Permitir gerar cache de forma não bloqueada

- Padrão: `false`
- Não aceita um valor

#### `--page-cache`

Manipulador de cache padrão

- Requer um valor

#### `--page-cache-redis-server`

Servidor Redis

- Requer um valor

#### `--page-cache-redis-db`

Número do banco de dados do cache

- Requer um valor

#### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

#### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página inteira (use 0 para desativar)

- Requer um valor

#### `--page-cache-redis-compression-lib`

Biblioteca de compactação para usar [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

#### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

#### `--lock-provider`

Nome do provedor de bloqueio

- Requer um valor

#### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

#### `--lock-zookeeper-host`

Host e porta para conexão com o cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

#### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/locks

- Requer um valor

#### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Requer um valor

#### `--document-root-is-pub`

O sinalizador para mostrar se o Pub está na raiz e pode ser verdadeiro ou falso apenas

- Requer um valor

#### `--backpressure-logger`

Manipulador do agente de log do backpressure

- Exige um valor

#### `--backpressure-logger-redis-server`

Servidor Redis

- Exige um valor

#### `--backpressure-logger-redis-port`

O servidor Redis escuta o porta

- Exige um valor

#### `--backpressure-logger-redis-timeout`

Tempo limite do servidor redis

- Exige um valor

#### `--backpressure-logger-redis-persistent`

Redis persistente

- Exige um valor

#### `--backpressure-logger-redis-db`

Número do banco de dados Redis

- Requer um valor

#### `--backpressure-logger-redis-password`

Senha do servidor Redis

- Requer um valor

#### `--backpressure-logger-redis-user`

Usuário do servidor Redis

- Requer um valor

#### `--backpressure-logger-id-prefix`

Prefixo de ID para chaves

- Exige um valor

#### `--base-url`

URL em que o armazenamento deveria estar disponível. Obsoleto, use config:set com caminho web/unsecure/base_url

- Exige um valor

#### `--language`

Código de idioma padrão. Obsoleto, use config:set com path general/locale/code

- Requer um valor

#### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com o caminho general/locale/timezone

- Requer um valor

#### `--currency`

Código de moeda padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

#### `--use-rewrites`

Use reescritas. Obsoleto, use config:set com caminho web/seo/use_rewrites

- Requer um valor

#### `--use-secure`

Use URLs seguros. Habilite essa opção somente se o SSL estiver disponível. Obsoleto, use config:set com o caminho web/secure/use_in_frontend

- Requer um valor

#### `--base-url-secure`

URL de base para conexão SSL. Obsoleto, use config:set com caminho web/seguro/base_url

- Exige um valor

#### `--use-secure-admin`

Execute administrador interface com SSL. Obsoleto, use config:set com caminho web/seguro/use_in_adminhtml

- Exige um valor

#### `--admin-use-security-key`

Se um recurso de &quot;chave de segurança&quot; deve ser usado em URLs e formulários de administração do Magento. Obsoleto, use config:set com o caminho admin/security/use_form_key

- Requer um valor

#### `--admin-user`

Usuário administrador

- Aceita um valor

#### `--admin-password`

Senha do administrador

- Aceita um valor

#### `--admin-email`

Email do administrador

- Aceita um valor

#### `--admin-firstname`

Nome do administrador

- Aceita um valor

#### `--admin-lastname`

Sobrenome do administrador

- Aceita um valor

#### `--search-engine`

Mecanismo de pesquisa. Valores: elasticsearch8, opensearch

- Requer um valor

#### `--elasticsearch-host`

Host do servidor do Elasticsearch.

- Requer um valor

#### `--elasticsearch-port`

Porta do servidor do Elasticsearch.

- Requer um valor

#### `--elasticsearch-enable-auth`

Defina como 1 para ativar a autenticação. (o padrão é 0, desativado)

- Requer um valor

#### `--elasticsearch-username`

Nome de usuário do Elasticsearch. Aplicável somente se a autenticação HTTP estiver ativada

- Exige um valor

#### `--elasticsearch-password`

Elasticsearch senha. Aplicável somente se a autenticação HTTP estiver ativada

- Exige um valor

#### `--elasticsearch-index-prefix`

Prefixo do índice Elasticsearch.

- Requer um valor

#### `--elasticsearch-timeout`

Tempo limite do servidor do Elasticsearch.

- Requer um valor

#### `--opensearch-host`

Host do servidor OpenSearch.

- Requer um valor

#### `--opensearch-port`

Porta do servidor OpenSearch.

- Requer um valor

#### `--opensearch-enable-auth`

Defina como 1 para ativar a autenticação. (o padrão é 0, desativado)

- Requer um valor

#### `--opensearch-username`

Nome de usuário do OpenSearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

#### `--opensearch-password`

Senha do OpenSearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

#### `--opensearch-index-prefix`

Prefixo do índice OpenSearch.

- Requer um valor

#### `--opensearch-timeout`

Tempo limite do servidor OpenSearch.

- Requer um valor

#### `--cleanup-database`

Limpar o banco de dados antes da instalação

- Padrão: `false`
- Não aceita um valor

#### `--sales-order-increment-prefix`

Prefixo do número da ordem de venda

- Requer um valor

#### `--use-sample-data`

Usar dados de amostra

- Padrão: `false`
- Não aceita um valor

#### `--enable-modules`

Lista de nomes de módulo separados por vírgulas. Isso deve ser incluído durante a instalação. Parâmetro mágico disponível &quot;tudo&quot;.

- Aceita um valor

#### `--disable-modules`

Lista de nomes de módulo separados por vírgulas. Isso deve ser evitado durante a instalação. Parâmetro mágico disponível &quot;tudo&quot;.

- Aceita um valor

#### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

#### `--interactive`, `-i`

Instalação interativa do Magento

- Padrão: `false`
- Não aceita um valor

#### `--safe-mode`

Instalação segura do Magento com despejos em operações destrutivas, como remoção de coluna

- Aceita um valor

#### `--data-restore`

Restaurar dados removidos de despejos

- Aceita um valor

#### `--dry-run`

A instalação do Magento será executada no modo de simulação

- Padrão: `false`
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Gera luminárias

### Argumentos

#### `profile`

Caminho para o arquivo de configuração do perfil

- Necessário

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--skip-reindex`, `-s`

Ignorar reindexação

- Padrão: `false`
- Não aceita um valor


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Reverte a base de código, a mídia e o banco de dados do aplicativo Magento

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--code-file`, `-c`

Nome de base do arquivo de backup de código em var/backups

- Requer um valor

#### `--media-file`, `-m`

Nome de base do arquivo de backup de mídia em var/backups

- Requer um valor

#### `--db-file`, `-d`

Nome de base do arquivo de backup de banco de dados em var/backups

- Requer um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Implanta arquivos de visualização estáticos

### Argumentos

#### `languages`

Lista separada por espaços de códigos de linguagem ISO-639 para os quais serão gerados arquivos de visualização estáticos.

- Padrão: `[]`
- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Implante arquivos em qualquer modo.

- Padrão: `false`
- Não aceita um valor

#### `--strategy`, `-s`

Implante arquivos usando a estratégia especificada.

- Inadimplência: `quick`
- Aceita um valor

#### `--area`, `-a`

Gere arquivos somente para as áreas especificadas.

- Inadimplência: `all`
- Aceita vários valores

#### `--exclude-area`

Não gere arquivos para as áreas especificadas.

- Inadimplência: `none`
- Aceita vários valores

#### `--theme`, `-t`

Gera arquivos de visualização estáticos apenas para os temas especificados.

- Padrão: `all`
- Aceita vários valores

#### `--exclude-theme`

Não gerar arquivos para os temas especificados.

- Padrão: `none`
- Aceita vários valores

#### `--language`, `-l`

Gera arquivos somente para os idiomas especificados.

- Padrão: `all`
- Aceita vários valores

#### `--exclude-language`

Não gere arquivos para os idiomas especificados.

- Inadimplência: `none`
- Aceita vários valores

#### `--jobs`, `-j`

Habilite o processamento paralelo usando o número especificado de trabalhos.

- Padrão: `0`
- Aceita um valor

#### `--max-execution-time`

O tempo máximo de execução esperado do processo estático de implantação (em segundos).

- Padrão: `900`
- Aceita um valor

#### `--symlink-locale`

Crie symlinks para os arquivos dessas localidades, que são transmitidos para implantação, mas não têm personalizações.

- Padrão: `false`
- Não aceita um valor

#### `--content-version`

A versão personalizada do conteúdo estático pode ser usada se a implantação estiver em execução em vários nós para garantir que a versão do conteúdo estático seja idêntica e o armazenamento em cache funcione corretamente.

- Requer um valor

#### `--refresh-content-version-only`

Atualizar a versão somente do conteúdo estático pode ser usado para atualizar o conteúdo estático no cache do navegador e do CDN.

- Padrão: `false`
- Não aceita um valor

#### `--no-javascript`

Não implante arquivos do JavaScript.

- Padrão: `false`
- Não aceita um valor

#### `--no-js-bundle`

Não implante arquivos de pacote do JavaScript.

- Padrão: `false`
- Não aceita um valor

#### `--no-css`

Não implante arquivos CSS.

- Padrão: `false`
- Não aceita um valor

#### `--no-less`

Não implantar arquivos LESS.

- Padrão: `false`
- Não aceita um valor

#### `--no-images`

Não implantar imagens.

- Padrão: `false`
- Não aceita um valor

#### `--no-fonts`

Não implantar arquivos de fonte.

- Padrão: `false`
- Não aceita um valor

#### `--no-html`

Não implante arquivos do HTML.

- Padrão: `false`
- Não aceita um valor

#### `--no-misc`

Não implante arquivos de outros tipos (.md, .jbf, .csv etc.).

- Padrão: `false`
- Não aceita um valor

#### `--no-html-minify`

Não minifique arquivos HTML.

- Padrão: `false`
- Não aceita um valor

#### `--no-parent`

Não compile o temas pai. Suportado somente em estratégias rápidas e padrão.

- Inadimplência: `false`
- Não aceita um valor


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala a configuração de armazenamento. Obsoleto desde 2.2.0. Use config:set

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--base-url`

URL em que o armazenamento deveria estar disponível. Obsoleto, use config:set com o caminho web/unsecure/base_url

- Requer um valor

#### `--language`

Código de idioma padrão. Obsoleto, use config:set com o caminho general/locale/code

- Requer um valor

#### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com o caminho general/locale/timezone

- Requer um valor

#### `--currency`

Código de moeda padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

#### `--use-rewrites`

Use regravações. Obsoleto, use config:set com o caminho web/seo/use_rewrites

- Requer um valor

#### `--use-secure`

Use URLs seguros. Ative essa opção somente se o SSL estiver disponível. Obsoleto, use config:set com caminho web/seguro/use_in_frontend

- Exige um valor

#### `--base-url-secure`

URL base da conexão SSL. Obsoleto, use config:set com o caminho web/secure/base_url

- Requer um valor

#### `--use-secure-admin`

Execute a interface do administrador com SSL. Obsoleto, use config:set com o caminho web/secure/use_in_adminhtml

- Requer um valor

#### `--admin-use-security-key`

Se um recurso de &quot;chave de segurança&quot; deve ser usado em URLs e formulários de administração do Magento. Obsoleto, use config:set com o caminho admin/security/use_form_key

- Exige um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar Magento parâmetros de inicialização Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Desinstala o aplicativo do Magento

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização do Magento. Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requer um valor


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Atualiza o aplicativo Magento, os dados do banco de dados e o esquema

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--keep-generated`

Impede que os arquivos gerados sejam excluídos. Desencorajamos o uso dessa opção, exceto ao implantar na produção. Consulte o integrador de sistemas ou administrador para obter mais informações.

- Inadimplência: `false`
- Não aceita um valor

#### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

#### `--safe-mode`

Instalação segura do Magento com despejos em operações destrutivas, como remoção de coluna

- Aceita um valor

#### `--data-restore`

Restaurar dados removidos dos despejos

- Aceita um valor

#### `--dry-run`

Magento instalação será executada no modo de execução seca

- Inadimplência: `false`
- Aceita um valor

#### `--magento-init-params`

Adicione a qualquer comando para personalizar Magento parâmetros de inicialização Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Exige um valor


## `store:list`

```bash
bin/magento store:list
```

Exibe a lista de lojas

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `store:website:list`

```bash
bin/magento store:website:list
```

Exibe a lista de sites

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Criar backup de código

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--name`

Nome do despejo

- Aceita um valor

#### `--output`, `-o`

Caminho de saída

- Aceita um valor

#### `--logs`, `-l`

Incluir logs

- Padrão: `false`
- Não aceita um valor


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Criar backup de BD

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--name`

Nome do despejo

- Aceita um valor

#### `--output`, `-o`

Caminho de saída

- Aceita um valor

#### `--logs`, `-l`

Incluir logs

- Padrão: `false`
- Não aceita um valor

#### `--ignore-sanitize`, `-i`

Ignorar a sanitização

- Inadimplência: `false`
- Não aceita um valor


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Verifique os utilitários de backup necessários

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--hide-paths`

Verificar somente os utilitários de console necessários

- Inadimplência: `false`
- Não aceita um valor


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

caminhos de utilitários Criar lista

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--force`, `-f`

Forçar

- Padrão: `false`
- Não aceita um valor


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Desinstala o tema

### Argumentos

#### `theme`

Caminho do tema. O caminho do tema deve ser especificado como o caminho completo, que é área/fornecedor/nome. Por exemplo, front-end/Magento/em branco

- Padrão: `[]`
- Obrigatório

- Matriz

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--backup-code`

Fazer backup do código (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

#### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados.

- Padrão: `false`
- Não aceita um valor


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Gera VCL de verniz e o ecoa à linha de comando

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--access-list`

IPs acessam lista que podem limpar varnish

- Inadimplência: `localhost`
- Requer um valor

#### `--backend-host`

Host do back-end da Web

- Padrão: `localhost`
- Requer um valor

#### `--backend-port`

Porta do back-end da Web

- Padrão: `8080`
- Exige um valor

#### `--export-version`

A versão do arquivo verniz

- Padrão: `6`
- Requer um valor

#### `--grace-period`

Período de carência em segundos

- Padrão: `300`
- Requer um valor

#### `--input-file`

Arquivo de entrada do qual gerar vcl

- Requer um valor

#### `--output-file`

Caminho para o arquivo para gravar vcl

- Requer um valor


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Executa um webhook registrado para fins de desenvolvimento.

### Argumentos

#### `name`

Nome do Webhook

- Obrigatório


#### `payload`

A carga do webhook no formato JSON

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Gerar plug-ins com base em registros de webhook

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Retorna a carga do webhook especificado.

### Argumentos

#### `webhook-name`

Nome do método Webhook

- Necessário


#### `webhook-type`

Tipo de Webhook (antes, depois)

- Padrão: `before`

### Opções

Para opções globais, consulte [Opções globais](#global-options).

#### `--depth`

O número de níveis na carga de webhook para retornar

- Padrão: `3`
- Aceita um valor


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Mostra lista de webhooks assinados

### Opções

Para opções globais, consulte [Opções globais](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Retorna uma lista de nomes de método de webhook com suporte para o módulo especificado

### Argumentos

#### `module_name`

Nome do módulo

- Obrigatório

### Opções

Para opções globais, consulte [Opções globais](#global-options).
