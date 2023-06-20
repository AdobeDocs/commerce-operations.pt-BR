---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '17529'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versão**: 2.4.7-beta1

Esta referência contém 115 comandos disponíveis através do `bin/magento` ferramenta de linha de comando.
A lista inicial é gerada automaticamente usando o `bin/magento list` comando no Magento Open Source.
Use o [&quot;Adicionar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) guia para adicionar um comando CLI personalizado.

>[!NOTE]
>
>Você pode chamar `bin/magento` Comandos CLI usando atalhos em vez do nome completo do comando. Por exemplo, você pode chamar `bin/magento setup:upgrade` usar `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxe de atalho](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para entender como usar atalhos com qualquer comando da CLI.

>[!NOTE]
>
>Essa referência é gerada a partir da base de código do aplicativo. Para alterar o conteúdo, você pode atualizar o código-fonte para a implementação do comando correspondente no [codebase](https://github.com/magento) repositório e enviar suas alterações para revisão. Outra maneira é _Envie seus comentários_ (localize o link no canto superior direito). Para obter diretrizes de contribuição, consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno para fornecer sugestões de conclusão de shell

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
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
bin/magento completion [--debug] [--] [<shell>]
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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


## `admin:adobe-ims:disable`

Desabilitar o módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

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


## `admin:adobe-ims:enable`

Ativar o módulo Adobe IMS.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Defina o ID da organização para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

### `--client-id`, `-c`

Defina a ID do cliente para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

### `--client-secret`, `-s`

Defina o segredo do cliente para a configuração do Adobe IMS. Obrigatório ao habilitar o módulo

- Aceita um valor

### `--2fa`, `-t`

Verifique se 2FA está ativado para Organização na Adobe Admin Console. Obrigatório ao habilitar o módulo

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


## `admin:adobe-ims:info`

Informações de configuração do módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:info
```

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


## `admin:adobe-ims:status`

Status do módulo IMS da Adobe

```bash
bin/magento admin:adobe-ims:status
```

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


## `admin:user:create`

Cria um administrador

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

(Obrigatório) Usuário administrador

- Requer um valor

### `--admin-password`

(Obrigatório) Senha do administrador

- Requer um valor

### `--admin-email`

(Obrigatório) Email do administrador

- Requer um valor

### `--admin-firstname`

(Obrigatório) Nome do administrador

- Requer um valor

### `--admin-lastname`

(Obrigatório) Sobrenome do administrador

- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `admin:user:unlock`

Desbloquear Conta de Administrador

```bash
bin/magento admin:user:unlock <username>
```


### `username`

O nome de usuário do administrador a ser desbloqueado

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


## `app:config:dump`

Criar despejo de aplicativo

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Lista separada por espaços de tipos de configuração ou omitir para despejar tudo [escopos, sistema, temas, i18n]

- Padrão: `[]`

- Matriz

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


## `app:config:import`

Importar dados de arquivos de configuração compartilhados para o armazenamento de dados apropriado

```bash
bin/magento app:config:import
```

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


## `app:config:status`

Verifica se a propagação de configuração requer atualização

```bash
bin/magento app:config:status
```

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


## `braintree:migrate`

Migrar cartões armazenados de um banco de dados Magento 1

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

Nome do host/IP. A porta é opcional

- Requer um valor

### `--dbname`

Nome do banco de dados

- Requer um valor

### `--username`

Usuário do banco de dados. Deve ter acesso de leitura

- Requer um valor

### `--password`

Senha

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


## `cache:clean`

Limpa os tipos de cache

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

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


## `cache:disable`

Desabilita os tipos de cache

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

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


## `cache:enable`

Habilita o(s) tipo(s) de cache

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

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


## `cache:flush`

Libera o armazenamento em cache usado pelo(s) tipo(s) de cache

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espaços de tipos de cache ou omitir para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

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


## `cache:status`

Verifica o status do cache

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

adicionar ou substituir parâmetros da inicialização

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


## `catalog:images:resize`

Cria imagens de produtos redimensionadas

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Redimensionar imagem no modo assíncrono

- Padrão: `false`
- Não aceita um valor

### `--skip_hidden_images`

Não processar imagens marcadas como ocultas da página do produto

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


## `catalog:product:attributes:cleanup`

Remove atributos de produto não utilizados.

```bash
bin/magento catalog:product:attributes:cleanup
```

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


## `cms:wysiwyg:restrict`

Defina se deseja impor a validação do conteúdo HTML do usuário ou mostrar um aviso

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

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


## `config:sensitive:set`

Definir valores de configuração confidenciais

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Caminho de configuração para exemplo group/section/field_name


### `value`

Valor de configuração


### `--interactive`, `-i`

Ativar o modo interativo para definir todas as variáveis confidenciais

- Padrão: `false`
- Não aceita um valor

### `--scope`

Escopo para configuração, se não for definido, usar &quot;padrão&quot;

- Padrão: `default`
- Aceita um valor

### `--scope-code`

Código de escopo para configuração, cadeia de caracteres vazia por padrão

- Padrão: &quot;
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


## `config:set`

Alterar configuração do sistema

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Caminho de configuração no formato seção/grupo/nome_do_campo

- Obrigatório

### `value`

Valor de configuração

- Obrigatório

### `--scope`

Escopo de configuração (padrão, site ou loja)

- Padrão: `default`
- Requer um valor

### `--scope-code`

Código do escopo (obrigatório somente se o escopo não for &#39;padrão&#39;)

- Requer um valor

### `--lock-env`, `-e`

Valor de bloqueio que impede a modificação no Administrador (será salvo em app/etc/env.php)

- Padrão: `false`
- Não aceita um valor

### `--lock-config`, `-c`

Bloquear e compartilhar valor com outras instalações, impede a modificação no Administrador (será salvo em app/etc/config.php)

- Padrão: `false`
- Não aceita um valor

### `--lock`, `-l`

Obsoleto, use a opção — lock- env.

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


## `config:show`

Mostra o valor de configuração para determinado caminho. Se o caminho não for especificado, todos os valores salvos serão mostrados

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Caminho de configuração, por exemplo section_id/group_id/field_id


### `--scope`

Escopo para configuração; se não especificado, o escopo &quot;padrão&quot; será usado

- Padrão: `default`
- Aceita um valor

### `--scope-code`

Código do escopo (necessário somente se o escopo não for `default`)

- Padrão: &quot;
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


## `cron:install`

Gera e instala o crontab para o usuário atual

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Forçar tarefas de instalação

- Padrão: `false`
- Não aceita um valor

### `--non-optional`, `-d`

Instalar somente as tarefas não opcionais (padrão)

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


## `cron:remove`

Remove tarefas do crontab

```bash
bin/magento cron:remove
```

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


## `cron:run`

Executa trabalhos por agendamento

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

Executar trabalhos somente do grupo especificado

- Requer um valor

### `--exclude-group`

Excluir trabalhos do grupo especificado

- Padrão: `[]`
- Aceita vários valores

### `--bootstrap`

Adicionar ou substituir parâmetros da inicialização

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


## `customer:hash:upgrade`

Atualize o hash do cliente de acordo com o algoritmo mais recente

```bash
bin/magento customer:hash:upgrade
```

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


## `deploy:mode:set`

Defina o modo do aplicativo.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

O modo de aplicativo a ser definido. As opções disponíveis são &quot;desenvolvedor&quot; ou &quot;produção&quot;

- Obrigatório

### `--skip-compilation`, `-s`

Ignora a limpeza e a regeneração de conteúdo estático (código gerado, CSS pré-processado e ativos no pub/static/)

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


## `deploy:mode:show`

Exibe o modo de aplicação atual.

```bash
bin/magento deploy:mode:show
```

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


## `dev:di:info`

Fornece informações sobre a configuração da Injeção de Dependência para o Comando.

```bash
bin/magento dev:di:info <class>
```


### `class`

Nome da classe

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


## `dev:email:newsletter-compatibility-check`

Verifica modelos de boletim informativo em busca de possíveis problemas de compatibilidade com o uso de variáveis

```bash
bin/magento dev:email:newsletter-compatibility-check
```

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


## `dev:email:override-compatibility-check`

Verifica substituições de modelos de e-mail em busca de possíveis problemas de compatibilidade com o uso de variáveis

```bash
bin/magento dev:email:override-compatibility-check
```

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


## `dev:profiler:disable`

Desative o profiler.

```bash
bin/magento dev:profiler:disable
```

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


## `dev:profiler:enable`

Ative o profiler.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Tipo de profiler


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


## `dev:query-log:disable`

Desabilitar log de consultas do BD

```bash
bin/magento dev:query-log:disable
```

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


## `dev:query-log:enable`

Habilitar log de consultas do BD

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Registra todas as consultas. [true\|false]

- Padrão: `true`
- Aceita um valor

### `--query-time-threshold`

Limites de tempo de consulta.

- Padrão: `0.001`
- Aceita um valor

### `--include-call-stack`

Incluir pilha de chamadas. [true\|false]

- Padrão: `true`
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


## `dev:source-theme:deploy`

Coleta e publica arquivos de origem para o tema.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Arquivos a serem pré-processados (o arquivo deve ser especificado sem a extensão)

- Padrão: `css/styles-mcss/styles-l`

- Matriz

### `--type`

Tipo de arquivos de origem: [menos]

- Padrão: `less`
- Requer um valor

### `--locale`

Localidade: [pt_BR]

- Padrão: `en_US`
- Requer um valor

### `--area`

Área: [front-end\|adminhtml]

- Padrão: `frontend`
- Requer um valor

### `--theme`

Tema: [Fornecedor/tema]

- Padrão: `Magento/luma`
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


## `dev:template-hints:disable`

Desative as dicas de modelo de front-end. Uma liberação de cache pode ser necessária.

```bash
bin/magento dev:template-hints:disable
```

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


## `dev:template-hints:enable`

Ativar dicas de modelo de front-end. Uma liberação de cache pode ser necessária.

```bash
bin/magento dev:template-hints:enable
```

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


## `dev:template-hints:status`

Mostrar status das dicas do modelo de front-end.

```bash
bin/magento dev:template-hints:status
```

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


## `dev:tests:run`

Executa testes

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Tipo de teste a ser executado. Tipos disponíveis: tudo, unidade, integração, integração-tudo, estático, estático-tudo, integridade, herdado, padrão

- Padrão: `default`


### `--arguments`, `-c`

Argumentos adicionais para PHPUnit. Exemplo: &quot;-c&#39;—filter=MeuTeste&#39;&quot; (sem espaços)

- Padrão: &quot;
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


## `dev:urn-catalog:generate`

Gera o catálogo de URNs para mapeamentos *.xsd para que o IDE destaque o xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Caminho para o arquivo de saída do catálogo. Para PhpStorm, use .idea/misc.xml

- Obrigatório

### `--ide`

Formato no qual o catálogo será gerado. Compatível: [phpstorm, vscode]

- Padrão: `phpstorm`
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


## `dev:xml:convert`

Converte arquivo XML usando folhas de estilos XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Caminho para o arquivo XML que será transformado

- Obrigatório

### `processor`

Caminho para a folha de estilos XSL que será aplicada ao arquivo XML

- Obrigatório

### `--overwrite`, `-o`

Substituir arquivo XML

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


## `downloadable:domains:add`

Adicionar domínios à lista de permissões de domínios baixáveis

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nome dos domínios

- Padrão: `[]`

- Matriz

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


## `downloadable:domains:remove`

Remover domínios da lista de permissões de domínios baixáveis

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Nomes de domínio

- Padrão: `[]`

- Matriz

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


## `downloadable:domains:show`

Exibir lista de permissões de domínios baixáveis

```bash
bin/magento downloadable:domains:show
```

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


## `encryption:payment-data:update`

Criptografa novamente os dados criptografados do cartão de crédito com a cifra de criptografia mais recente.

```bash
bin/magento encryption:payment-data:update
```

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


## `i18n:collect-phrases`

Descobre frases na base de código

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Caminho do diretório para análise. Não é necessário se o sinalizador — magento estiver ativo


### `--output`, `-o`

Caminho (incluindo o nome do arquivo) para um arquivo de saída. Sem nenhum arquivo especificado, o padrão é stdout.

- Requer um valor

### `--magento`, `-m`

Use o parâmetro —magento para analisar a base de código do Magento atual. Omita o parâmetro se um diretório for especificado.

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


## `i18n:pack`

Salva o pacote de idioma

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Caminho para o arquivo do dicionário de origem com traduções

- Obrigatório

### `locale`

Local de destino do dicionário, por exemplo &quot;de_DE&quot;

- Obrigatório

### `--mode`, `-m`

Modo de salvamento do dicionário - &quot;substituir&quot; - substituir o pacote de idiomas por um novo - &quot;mesclar&quot; - mesclar pacotes de idiomas, por padrão &quot;substituir&quot;

- Padrão: `replace`
- Requer um valor

### `--allow-duplicates`, `-d`

Use o parâmetro —allow-duplicates para permitir o salvamento de duplicatas de translate. Caso contrário, omita o parâmetro.

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


## `i18n:uninstall`

Desinstala pacotes de idiomas

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Nome do pacote de idioma

- Padrão: `[]`

- Obrigatório
- Matriz

### `--backup-code`, `-b`

Fazer backup de arquivos de código e configuração (excluindo arquivos temporários)

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


## `indexer:info`

Mostra os Indexadores permitidos

```bash
bin/magento indexer:info
```

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


## `indexer:reindex`

Reindexa dados

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

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


## `indexer:reset`

Redefine o status do indexador para inválido

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

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


## `indexer:set-dimensions-mode`

Definir modo de indexador Dimension

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nome do indexador [catalog_product_price]


### `mode`

Modos de dimensão do indexador catalog_product_price none,website,customer_group,website_and_customer_group


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


## `indexer:set-mode`

Define o tipo de modo de índice

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Tipo de modo do indexador [tempo real|cronograma]


### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

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


## `indexer:show-dimensions-mode`

Mostra o modo de Dimension do indexador

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices (catalog_product_price)

- Padrão: `[]`

- Matriz

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


## `indexer:show-mode`

Mostra o modo de índice

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

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


## `indexer:status`

Mostra o status do Indexador

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Lista separada por espaços de tipos de índice ou omissão para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

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


## `info:adminuri`

Exibe o URI do administrador de Magento

```bash
bin/magento info:adminuri
```

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


## `info:backups:list`

Imprime a lista de arquivos de backup disponíveis

```bash
bin/magento info:backups:list
```

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


## `info:currency:list`

Exibe a lista de moedas disponíveis

```bash
bin/magento info:currency:list
```

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


## `info:dependencies:show-framework`

Mostra o número de dependências na estrutura Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome do arquivo do relatório

- Padrão: `framework-dependencies.csv`
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


## `info:dependencies:show-modules`

Mostra o número de dependências entre módulos

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome do arquivo do relatório

- Padrão: `modules-dependencies.csv`
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


## `info:dependencies:show-modules-circular`

Mostra o número de dependências circulares entre módulos

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome do arquivo do relatório

- Padrão: `modules-circular-dependencies.csv`
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


## `info:language:list`

Exibe a lista de localidades de idioma disponíveis

```bash
bin/magento info:language:list
```

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


## `info:timezone:list`

Exibe a lista de fusos horários disponíveis

```bash
bin/magento info:timezone:list
```

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


## `inventory:reservation:create-compensations`

Criar reservas por argumentos de remuneração fornecidos

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Lista de argumentos de compensação no formato &quot;\&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>&quot;

- Padrão: `[]`

- Matriz

### `--raw`, `-r`

Saída bruta

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


## `inventory:reservation:list-inconsistencies`

Mostrar todos os pedidos e produtos com inconsistências de quantidade vendável

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Mostrar apenas inconsistências para pedidos completos

- Padrão: `false`
- Não aceita um valor

### `--incomplete-orders`, `-i`

Mostrar apenas inconsistências para pedidos incompletos

- Padrão: `false`
- Não aceita um valor

### `--bunch-size`, `-b`

Define quantos pedidos serão carregados de uma vez

- Padrão: `50`
- Aceita um valor

### `--raw`, `-r`

Saída bruta

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


## `inventory-geonames:import`

Baixar e importar nomes geográficos para o algoritmo de seleção de origem

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Lista de códigos de país a serem importados

- Padrão: `[]`

- Obrigatório
- Matriz

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


## `maintenance:allow-ips`

Define IPs isentos do modo de manutenção

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

Endereços IP permitidos

- Padrão: `[]`

- Matriz

### `--none`

Limpar endereços IP permitidos

- Padrão: `false`
- Não aceita um valor

### `--add`

Adicionar o endereço IP à lista existente

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:disable`

Desabilita o modo de manutenção

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Endereços IP permitidos (use &quot;nenhum&quot; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:enable`

Ativa o modo de manutenção

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Endereços IP permitidos (use &quot;nenhum&quot; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:status`

Exibe o status do modo de manutenção

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `media-content:sync`

Sincronizar conteúdo com ativos

```bash
bin/magento media-content:sync
```

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


## `media-gallery:sync`

Sincronizar armazenamento de mídia e ativos de mídia no banco de dados

```bash
bin/magento media-gallery:sync
```

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


## `module:config:status`

Verifica a configuração dos módulos no arquivo &#39;app/etc/config.php&#39; e relata se eles estão atualizados ou não

```bash
bin/magento module:config:status
```

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


## `module:disable`

Desativa módulos especificados

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nome do módulo

- Padrão: `[]`

- Matriz

### `--force`, `-f`

Ignorar verificação de dependências

- Padrão: `false`
- Não aceita um valor

### `--all`

Desativar todos os módulos

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados. Necessário, se o(s) módulo(s) tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:enable`

Habilita módulos especificados

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nome do módulo

- Padrão: `[]`

- Matriz

### `--force`, `-f`

Ignorar verificação de dependências

- Padrão: `false`
- Não aceita um valor

### `--all`

Habilitar todos os módulos

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados. Necessário, se o(s) módulo(s) tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:status`

Exibe o status dos módulos

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Nome opcional do módulo

- Padrão: `[]`

- Matriz

### `--enabled`

Imprimir somente os módulos habilitados

- Padrão: `false`
- Não aceita um valor

### `--disabled`

Imprimir somente módulos desabilitados

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:uninstall`

Desinstala módulos instalados pelo compositor

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

Nome do módulo

- Padrão: `[]`

- Obrigatório
- Matriz

### `--remove-data`, `-r`

Remover dados instalados pelos módulos

- Padrão: `false`
- Não aceita um valor

### `--backup-code`

Fazer backup de arquivos de código e configuração (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--backup-media`

Fazer backup de mídia

- Padrão: `false`
- Não aceita um valor

### `--backup-db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

### `--non-composer`

Todos os módulos, que serão passados aqui, serão não baseados em compositor

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados. Necessário, se o(s) módulo(s) tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `newrelic:create:deploy-marker`

Verifique se há entradas na fila de implantação e crie um marcador de implantação apropriado.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

Implantar mensagem?

- Obrigatório

### `change_log`

Registro de alterações?

- Obrigatório

### `user`

Usuário de implantação


### `revision`

Revisão


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


## `queue:consumers:list`

Lista de consumidores do MessageQueue

```bash
bin/magento queue:consumers:list
```

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


## `queue:consumers:restart`

Reiniciar consumidores do MessageQueue

```bash
bin/magento queue:consumers:restart
```

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


## `queue:consumers:start`

Iniciar consumidor MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

O nome do consumidor a ser iniciado.

- Obrigatório

### `--max-messages`

O número de mensagens a serem processadas pelo consumidor antes do término do processo. Se não for especificado - finalizar após o processamento de todas as mensagens em fila.

- Requer um valor

### `--batch-size`

O número de mensagens por lote. Aplicável somente para o consumidor do lote.

- Requer um valor

### `--area-code`

O padrão da área preferida (global, adminhtml, etc.) é global.

- Requer um valor

### `--single-thread`

Essa opção impede a execução de várias cópias de um consumidor simultaneamente.

- Padrão: `false`
- Não aceita um valor

### `--multi-process`

O número de processos por consumidor.

- Aceita um valor

### `--pid-file-path`

O caminho do arquivo para salvar o PID (Esta opção está obsoleta, use — single- thread)

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


## `remote-storage:sync`

Sincronizar arquivos de mídia com o armazenamento remoto.

```bash
bin/magento remote-storage:sync
```

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


## `saas:resync`

Sincroniza novamente os dados do feed com o serviço SaaS.

```bash
bin/magento saas:resync [--no-reindex] [--feed FEED] [--cleanup-feed]
```

### `--no-reindex`

Execute o reenvio de dados de feed somente para o serviço SaaS. Não reindexa.

- Padrão: `false`
- Não aceita um valor

### `--feed`

Nome do feed para ressincronização completa com o serviço SaaS. Feeds disponíveis:

- Requer um valor

### `--cleanup-feed`

Força a limpeza da tabela indexadora de feed antes da sincronização.

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


## `sampledata:deploy`

Implantar módulos de dados de amostra para instalações de Magento com base no compositor

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Atualizar composer.json sem executar a atualização do composer

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


## `sampledata:remove`

Remover todos os pacotes de dados de amostra do composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Atualizar composer.json sem executar a atualização do composer

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


## `sampledata:reset`

Redefina todos os módulos de dados de amostra para reinstalação

```bash
bin/magento sampledata:reset
```

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


## `security:recaptcha:disable-for-user-forgot-password`

Desativar o reCAPTCHA para o formulário de senha esquecida do usuário administrador

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

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


## `security:recaptcha:disable-for-user-login`

Desabilitar reCAPTCHA para o formulário de logon de usuário administrador

```bash
bin/magento security:recaptcha:disable-for-user-login
```

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


## `security:tfa:google:set-secret`

Defina o segredo usado para a geração de OTP do Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Nome de usuário

- Obrigatório

### `secret`

Segredo

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


## `security:tfa:providers`

Listar todos os provedores disponíveis

```bash
bin/magento security:tfa:providers
```

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


## `security:tfa:reset`

Redefinir configuração para um usuário

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Nome de usuário

- Obrigatório

### `provider`

Código do provedor

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


## `setup:backup`

Faz backup de Magento Base de código de aplicativo, mídia e banco de dados

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Fazer backup de arquivos de código e configuração (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--media`

Fazer backup de mídia

- Padrão: `false`
- Não aceita um valor

### `--db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:config:set`

Cria ou modifica a configuração de implantação

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome da frente de backend (será gerado automaticamente se estiver faltando)

- Requer um valor

### `--enable-debug-logging`

Habilitar log de depuração

- Requer um valor

### `--enable-syslog-logging`

Habilitar registro do syslog

- Requer um valor

### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-endpoint`

Ponto de extremidade de armazenamento remoto

- Requer um valor

### `--remote-storage-bucket`

Compartimento de armazenamento remoto

- Requer um valor

### `--remote-storage-region`

Região de armazenamento remoto

- Requer um valor

### `--remote-storage-key`

Chave de acesso do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-secret`

Chave secreta do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-path-style`

Estilo do caminho de armazenamento remoto

- Padrão: `0`
- Requer um valor

### `--id_salt`

Sal GraphQl

- Requer um valor

### `--amqp-host`

Host do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-port`

Porta do servidor Amqp

- Padrão: `5672`
- Requer um valor

### `--amqp-user`

Nome de usuário do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-password`

Senha do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-virtualhost`

Virtualhost Amqp

- Padrão: `/`
- Requer um valor

### `--amqp-ssl`

Amqp SSL

- Padrão: &quot;
- Requer um valor

### `--amqp-ssl-options`

Opções de SSL Amqp (JSON)

- Padrão: &quot;
- Requer um valor

### `--config-async`

Habilitar Salvar Configuração de Administração assíncrona? 1 - Sim, 0 - Não

- Requer um valor

### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

### `--queue-default-connection`

Conexão padrão de filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve estar instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

### `--key`

Chave de criptografia

- Requer um valor

### `--db-host`

Host do servidor de banco de dados

- Requer um valor

### `--db-name`

Nome do banco de dados

- Requer um valor

### `--db-user`

Usuário do servidor de banco de dados

- Requer um valor

### `--db-engine`

Mecanismo do servidor de banco de dados

- Requer um valor

### `--db-password`

Senha do servidor de banco de dados

- Requer um valor

### `--db-prefix`

Prefixo da tabela do banco de dados

- Requer um valor

### `--db-model`

Tipo de banco de dados

- Requer um valor

### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Requer um valor

### `--skip-db-validation`, `-s`

Se especificado, a validação da conexão com o banco de dados será ignorada

- Padrão: `false`
- Não aceita um valor

### `--http-cache-hosts`

hosts de cache http

- Requer um valor

### `--db-ssl-key`

Caminho completo do arquivo de chave do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-verify`

Verificar certificação do servidor

- Padrão: `false`
- Não aceita um valor

### `--session-save`

Manipulador de salvamento de sessão

- Requer um valor

### `--session-save-redis-host`

Nome de host totalmente qualificado, endereço IP ou caminho absoluto se estiver usando soquetes UNIX

- Requer um valor

### `--session-save-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--session-save-redis-password`

Senha do servidor Redis

- Requer um valor

### `--session-save-redis-timeout`

Tempo limite da conexão, em segundos

- Requer um valor

### `--session-save-redis-persistent-id`

Sequência de caracteres exclusiva para habilitar conexões persistentes

- Requer um valor

### `--session-save-redis-db`

Número do banco de dados Redis

- Requer um valor

### `--session-save-redis-compression-threshold`

Limite de compactação Redis

- Requer um valor

### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

### `--session-save-redis-log-level`

Nível de log Redis. Valores: 0 (menos explícito) a 7 (mais explícito)

- Requer um valor

### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar um bloqueio em uma sessão

- Requer um valor

### `--session-save-redis-break-after-frontend`

Número de segundos a aguardar antes de tentar interromper um bloqueio para uma sessão de front-end

- Requer um valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos a aguardar antes de tentar interromper um bloqueio para a sessão de administrador

- Requer um valor

### `--session-save-redis-first-lifetime`

Tempo de vida, em segundos, da sessão para não bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-first-lifetime`

Tempo de vida, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-lifetime`

Tempo de vida da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

### `--session-save-redis-disable-locking`

Redis desabilita o bloqueio. Valores: falso (padrão), verdadeiro

- Requer um valor

### `--session-save-redis-min-lifetime`

Tempo de vida mínimo da sessão Redis, em segundos

- Requer um valor

### `--session-save-redis-max-lifetime`

Tempo de vida máximo da sessão do Redis, em segundos

- Requer um valor

### `--session-save-redis-sentinel-master`

Redis Sentinel principal

- Requer um valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgula

- Requer um valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifique principal. Valores: falso (padrão), verdadeiro

- Requer um valor

### `--session-save-redis-sentinel-connect-retries`

Tentativas de conexão do Redis Sentinel.

- Requer um valor

### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

### `--cache-backend-redis-db`

Número do banco de dados do cache

- Requer um valor

### `--cache-backend-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--cache-backend-redis-password`

Senha do servidor Redis

- Requer um valor

### `--cache-backend-redis-compress-data`

Defina como 0 para desativar a compactação (o padrão é 1, ativado)

- Requer um valor

### `--cache-backend-redis-compression-lib`

Biblioteca de compactação a ser usada [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--allow-parallel-generation`

Permitir gerar cache de forma não bloqueada

- Padrão: `false`
- Não aceita um valor

### `--page-cache`

Manipulador de cache padrão

- Requer um valor

### `--page-cache-redis-server`

Servidor Redis

- Requer um valor

### `--page-cache-redis-db`

Número do banco de dados do cache

- Requer um valor

### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página inteira (use 0 para desativar)

- Requer um valor

### `--page-cache-redis-compression-lib`

Biblioteca de compactação a ser usada [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--lock-provider`

Nome do provedor de bloqueio

- Requer um valor

### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

### `--lock-zookeeper-host`

Host e porta para conexão com o cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/locks

- Requer um valor

### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Requer um valor

### `--document-root-is-pub`

O sinalizador para mostrar se o Pub está na raiz e pode ser verdadeiro ou falso apenas

- Requer um valor

### `--backpressure-logger`

Manipulador de registrador de pressão inversa

- Requer um valor

### `--backpressure-logger-redis-server`

Servidor Redis

- Requer um valor

### `--backpressure-logger-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-timeout`

Tempo limite do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-persistent`

Redis persistente

- Requer um valor

### `--backpressure-logger-redis-db`

Número do banco de dados Redis

- Requer um valor

### `--backpressure-logger-redis-password`

Senha do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-user`

Usuário do servidor Redis

- Requer um valor

### `--backpressure-logger-id-prefix`

Prefixo de ID para chaves

- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-data:upgrade`

Instala e atualiza dados no BD

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-declaration:generate-patch`

Gere o patch e coloque-o na pasta específica.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

Nome do módulo

- Obrigatório

### `patch`

Nome do patch

- Obrigatório

### `--revertable`

Verifique se o patch é reversível ou não.

- Padrão: `false`
- Aceita um valor

### `--type`

Descubra que tipo de patch deve ser gerado. Valores disponíveis: `data`, `schema`.

- Padrão: `data`
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


## `setup:db-declaration:generate-whitelist`

Gerar lista de permissões de tabelas e colunas que podem ser editadas pelo instalador de declarações

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Nome do módulo onde a lista de permissões será gerada

- Padrão: `all`
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


## `setup:db-schema:upgrade`

Instala e atualiza o esquema do BD

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db:status`

Verifica se o esquema ou os dados do banco de dados exigem atualização

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:di:compile`

Gera a configuração de ID e todas as classes ausentes que podem ser geradas automaticamente

```bash
bin/magento setup:di:compile
```

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


## `setup:install`

Instala o aplicativo Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome da frente de backend (será gerado automaticamente se estiver faltando)

- Requer um valor

### `--enable-debug-logging`

Habilitar log de depuração

- Requer um valor

### `--enable-syslog-logging`

Habilitar registro do syslog

- Requer um valor

### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-endpoint`

Ponto de extremidade de armazenamento remoto

- Requer um valor

### `--remote-storage-bucket`

Compartimento de armazenamento remoto

- Requer um valor

### `--remote-storage-region`

Região de armazenamento remoto

- Requer um valor

### `--remote-storage-key`

Chave de acesso do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-secret`

Chave secreta do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-path-style`

Estilo do caminho de armazenamento remoto

- Padrão: `0`
- Requer um valor

### `--id_salt`

Sal GraphQl

- Requer um valor

### `--amqp-host`

Host do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-port`

Porta do servidor Amqp

- Padrão: `5672`
- Requer um valor

### `--amqp-user`

Nome de usuário do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-password`

Senha do servidor Amqp

- Padrão: &quot;
- Requer um valor

### `--amqp-virtualhost`

Virtualhost Amqp

- Padrão: `/`
- Requer um valor

### `--amqp-ssl`

Amqp SSL

- Padrão: &quot;
- Requer um valor

### `--amqp-ssl-options`

Opções de SSL Amqp (JSON)

- Padrão: &quot;
- Requer um valor

### `--config-async`

Habilitar Salvar Configuração de Administração assíncrona? 1 - Sim, 0 - Não

- Requer um valor

### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

### `--queue-default-connection`

Conexão padrão de filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve estar instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

### `--key`

Chave de criptografia

- Requer um valor

### `--db-host`

Host do servidor de banco de dados

- Requer um valor

### `--db-name`

Nome do banco de dados

- Requer um valor

### `--db-user`

Usuário do servidor de banco de dados

- Requer um valor

### `--db-engine`

Mecanismo do servidor de banco de dados

- Requer um valor

### `--db-password`

Senha do servidor de banco de dados

- Requer um valor

### `--db-prefix`

Prefixo da tabela do banco de dados

- Requer um valor

### `--db-model`

Tipo de banco de dados

- Requer um valor

### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Requer um valor

### `--skip-db-validation`, `-s`

Se especificado, a validação da conexão com o banco de dados será ignorada

- Padrão: `false`
- Não aceita um valor

### `--http-cache-hosts`

hosts de cache http

- Requer um valor

### `--db-ssl-key`

Caminho completo do arquivo de chave do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente para estabelecer uma conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer conexão de banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-verify`

Verificar certificação do servidor

- Padrão: `false`
- Não aceita um valor

### `--session-save`

Manipulador de salvamento de sessão

- Requer um valor

### `--session-save-redis-host`

Nome de host totalmente qualificado, endereço IP ou caminho absoluto se estiver usando soquetes UNIX

- Requer um valor

### `--session-save-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--session-save-redis-password`

Senha do servidor Redis

- Requer um valor

### `--session-save-redis-timeout`

Tempo limite da conexão, em segundos

- Requer um valor

### `--session-save-redis-persistent-id`

Sequência de caracteres exclusiva para habilitar conexões persistentes

- Requer um valor

### `--session-save-redis-db`

Número do banco de dados Redis

- Requer um valor

### `--session-save-redis-compression-threshold`

Limite de compactação Redis

- Requer um valor

### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

### `--session-save-redis-log-level`

Nível de log Redis. Valores: 0 (menos explícito) a 7 (mais explícito)

- Requer um valor

### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar um bloqueio em uma sessão

- Requer um valor

### `--session-save-redis-break-after-frontend`

Número de segundos a aguardar antes de tentar interromper um bloqueio para uma sessão de front-end

- Requer um valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos a aguardar antes de tentar interromper um bloqueio para a sessão de administrador

- Requer um valor

### `--session-save-redis-first-lifetime`

Tempo de vida, em segundos, da sessão para não bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-first-lifetime`

Tempo de vida, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-lifetime`

Tempo de vida da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

### `--session-save-redis-disable-locking`

Redis desabilita o bloqueio. Valores: falso (padrão), verdadeiro

- Requer um valor

### `--session-save-redis-min-lifetime`

Tempo de vida mínimo da sessão Redis, em segundos

- Requer um valor

### `--session-save-redis-max-lifetime`

Tempo de vida máximo da sessão do Redis, em segundos

- Requer um valor

### `--session-save-redis-sentinel-master`

Redis Sentinel principal

- Requer um valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgula

- Requer um valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifique principal. Valores: falso (padrão), verdadeiro

- Requer um valor

### `--session-save-redis-sentinel-connect-retries`

Tentativas de conexão do Redis Sentinel.

- Requer um valor

### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

### `--cache-backend-redis-db`

Número do banco de dados do cache

- Requer um valor

### `--cache-backend-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--cache-backend-redis-password`

Senha do servidor Redis

- Requer um valor

### `--cache-backend-redis-compress-data`

Defina como 0 para desativar a compactação (o padrão é 1, ativado)

- Requer um valor

### `--cache-backend-redis-compression-lib`

Biblioteca de compactação a ser usada [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--allow-parallel-generation`

Permitir gerar cache de forma não bloqueada

- Padrão: `false`
- Não aceita um valor

### `--page-cache`

Manipulador de cache padrão

- Requer um valor

### `--page-cache-redis-server`

Servidor Redis

- Requer um valor

### `--page-cache-redis-db`

Número do banco de dados do cache

- Requer um valor

### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página inteira (use 0 para desativar)

- Requer um valor

### `--page-cache-redis-compression-lib`

Biblioteca de compactação a ser usada [snappy,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--lock-provider`

Nome do provedor de bloqueio

- Requer um valor

### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

### `--lock-zookeeper-host`

Host e porta para conexão com o cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/locks

- Requer um valor

### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Requer um valor

### `--document-root-is-pub`

O sinalizador para mostrar se o Pub está na raiz e pode ser verdadeiro ou falso apenas

- Requer um valor

### `--backpressure-logger`

Manipulador de registrador de pressão inversa

- Requer um valor

### `--backpressure-logger-redis-server`

Servidor Redis

- Requer um valor

### `--backpressure-logger-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-timeout`

Tempo limite do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-persistent`

Redis persistente

- Requer um valor

### `--backpressure-logger-redis-db`

Número do banco de dados Redis

- Requer um valor

### `--backpressure-logger-redis-password`

Senha do servidor Redis

- Requer um valor

### `--backpressure-logger-redis-user`

Usuário do servidor Redis

- Requer um valor

### `--backpressure-logger-id-prefix`

Prefixo de ID para chaves

- Requer um valor

### `--base-url`

URL em que o armazenamento deveria estar disponível. Obsoleto, use config:set com o caminho web/unsecure/base_url

- Requer um valor

### `--language`

Código de idioma padrão. Obsoleto, use config:set com o caminho general/locale/code

- Requer um valor

### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com o caminho general/locale/timezone

- Requer um valor

### `--currency`

Código de moeda padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

### `--use-rewrites`

Use regravações. Obsoleto, use config:set com o caminho web/seo/use_rewrites

- Requer um valor

### `--use-secure`

Use URLs seguros. Habilite essa opção somente se o SSL estiver disponível. Obsoleto, use config:set com o caminho web/secure/use_in_frontend

- Requer um valor

### `--base-url-secure`

URL base da conexão SSL. Obsoleto, use config:set com o caminho web/secure/base_url

- Requer um valor

### `--use-secure-admin`

Execute a interface do administrador com SSL. Obsoleto, use config:set com o caminho web/secure/use_in_adminhtml

- Requer um valor

### `--admin-use-security-key`

Usar um recurso de &quot;chave de segurança&quot; nos formulários e URLs do administrador do Magento. Obsoleto, use config:set com o caminho admin/security/use_form_key

- Requer um valor

### `--admin-user`

Usuário administrador

- Aceita um valor

### `--admin-password`

Senha do administrador

- Aceita um valor

### `--admin-email`

Email do administrador

- Aceita um valor

### `--admin-firstname`

Nome do administrador

- Aceita um valor

### `--admin-lastname`

Sobrenome do administrador

- Aceita um valor

### `--search-engine`

Mecanismo de pesquisa. Valores: elasticsearch5, elasticsearch7, elasticsearch8, opensearch

- Requer um valor

### `--elasticsearch-host`

host do servidor Elasticsearch.

- Requer um valor

### `--elasticsearch-port`

porta do servidor Elasticsearch.

- Requer um valor

### `--elasticsearch-enable-auth`

Defina como 1 para ativar a autenticação. (o padrão é 0, desativado)

- Requer um valor

### `--elasticsearch-username`

nome de usuário do Elasticsearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

### `--elasticsearch-password`

Senha do Elasticsearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

### `--elasticsearch-index-prefix`

prefixo do índice Elasticsearch.

- Requer um valor

### `--elasticsearch-timeout`

Tempo limite do servidor Elasticsearch.

- Requer um valor

### `--opensearch-host`

Host do servidor OpenSearch.

- Requer um valor

### `--opensearch-port`

Porta do servidor OpenSearch.

- Requer um valor

### `--opensearch-enable-auth`

Defina como 1 para ativar a autenticação. (o padrão é 0, desativado)

- Requer um valor

### `--opensearch-username`

Nome de usuário do OpenSearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

### `--opensearch-password`

Senha do OpenSearch. Aplicável somente se a autenticação HTTP estiver habilitada

- Requer um valor

### `--opensearch-index-prefix`

Prefixo do índice OpenSearch.

- Requer um valor

### `--opensearch-timeout`

Tempo limite do servidor OpenSearch.

- Requer um valor

### `--cleanup-database`

Limpar o banco de dados antes da instalação

- Padrão: `false`
- Não aceita um valor

### `--sales-order-increment-prefix`

Prefixo do número da ordem de venda

- Requer um valor

### `--use-sample-data`

Usar dados de amostra

- Padrão: `false`
- Não aceita um valor

### `--enable-modules`

Lista de nomes de módulo separados por vírgulas. Isso deve ser incluído durante a instalação. Parâmetro mágico disponível &quot;tudo&quot;.

- Aceita um valor

### `--disable-modules`

Lista de nomes de módulo separados por vírgulas. Isso deve ser evitado durante a instalação. Parâmetro mágico disponível &quot;tudo&quot;.

- Aceita um valor

### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

### `--interactive`, `-i`

Instalação de Magento interativa

- Padrão: `false`
- Não aceita um valor

### `--safe-mode`

Instalação segura de Magento com despejos em operações destrutivas, como remoção de coluna

- Aceita um valor

### `--data-restore`

Restaurar dados removidos de despejos

- Aceita um valor

### `--dry-run`

A instalação do Magento será executada no modo de simulação

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:performance:generate-fixtures`

Gera luminárias

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Caminho para o arquivo de configuração do perfil

- Obrigatório

### `--skip-reindex`, `-s`

Ignorar reindexação

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


## `setup:rollback`

Reverte a base de código, a mídia e o banco de dados do aplicativo Magento

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

Nome de base do arquivo de backup de código em var/backups

- Requer um valor

### `--media-file`, `-m`

Nome de base do arquivo de backup de mídia em var/backups

- Requer um valor

### `--db-file`, `-d`

Nome de base do arquivo de backup de banco de dados em var/backups

- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:static-content:deploy`

Implanta arquivos de visualização estáticos

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Lista separada por espaços de códigos de linguagem ISO-639 para os quais serão gerados arquivos de visualização estáticos.

- Padrão: `[]`

- Matriz

### `--force`, `-f`

Implante arquivos em qualquer modo.

- Padrão: `false`
- Não aceita um valor

### `--strategy`, `-s`

Implantar arquivos usando a estratégia especificada.

- Padrão: `quick`
- Aceita um valor

### `--area`, `-a`

Gera arquivos somente para as áreas especificadas.

- Padrão: `all`
- Aceita vários valores

### `--exclude-area`

Não gerar arquivos para as áreas especificadas.

- Padrão: `none`
- Aceita vários valores

### `--theme`, `-t`

Gera arquivos de visualização estáticos apenas para os temas especificados.

- Padrão: `all`
- Aceita vários valores

### `--exclude-theme`

Não gerar arquivos para os temas especificados.

- Padrão: `none`
- Aceita vários valores

### `--language`, `-l`

Gera arquivos somente para os idiomas especificados.

- Padrão: `all`
- Aceita vários valores

### `--exclude-language`

Não gerar arquivos para os idiomas especificados.

- Padrão: `none`
- Aceita vários valores

### `--jobs`, `-j`

Habilite o processamento paralelo usando o número especificado de trabalhos.

- Padrão: `0`
- Aceita um valor

### `--max-execution-time`

O tempo máximo de execução esperado do processo estático de implantação (em segundos).

- Padrão: `900`
- Aceita um valor

### `--symlink-locale`

Crie symlinks para os arquivos dessas localidades, que são transmitidos para implantação, mas não têm personalizações.

- Padrão: `false`
- Não aceita um valor

### `--content-version`

A versão personalizada do conteúdo estático pode ser usada se a implantação estiver em execução em vários nós para garantir que a versão do conteúdo estático seja idêntica e o armazenamento em cache funcione corretamente.

- Requer um valor

### `--refresh-content-version-only`

Atualizar a versão somente do conteúdo estático pode ser usado para atualizar o conteúdo estático no cache do navegador e do CDN.

- Padrão: `false`
- Não aceita um valor

### `--no-javascript`

Não implante arquivos JavaScript.

- Padrão: `false`
- Não aceita um valor

### `--no-js-bundle`

Não implante arquivos de pacote JavaScript.

- Padrão: `false`
- Não aceita um valor

### `--no-css`

Não implante arquivos CSS.

- Padrão: `false`
- Não aceita um valor

### `--no-less`

Não implante MENOS arquivos.

- Padrão: `false`
- Não aceita um valor

### `--no-images`

Não implantar imagens.

- Padrão: `false`
- Não aceita um valor

### `--no-fonts`

Não implantar arquivos de fonte.

- Padrão: `false`
- Não aceita um valor

### `--no-html`

Não implante arquivos HTML.

- Padrão: `false`
- Não aceita um valor

### `--no-misc`

Não implante arquivos de outros tipos (.md, .jbf, .csv etc.).

- Padrão: `false`
- Não aceita um valor

### `--no-html-minify`

Não minifique arquivos HTML.

- Padrão: `false`
- Não aceita um valor

### `--no-parent`

Não compile temas principais. Compatível somente com estratégias rápidas e padrão.

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


## `setup:store-config:set`

Instala a configuração de armazenamento. Obsoleto desde 2.2.0. Use config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

URL em que o armazenamento deveria estar disponível. Obsoleto, use config:set com o caminho web/unsecure/base_url

- Requer um valor

### `--language`

Código de idioma padrão. Obsoleto, use config:set com o caminho general/locale/code

- Requer um valor

### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com o caminho general/locale/timezone

- Requer um valor

### `--currency`

Código de moeda padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

### `--use-rewrites`

Use regravações. Obsoleto, use config:set com o caminho web/seo/use_rewrites

- Requer um valor

### `--use-secure`

Use URLs seguros. Habilite essa opção somente se o SSL estiver disponível. Obsoleto, use config:set com o caminho web/secure/use_in_frontend

- Requer um valor

### `--base-url-secure`

URL base da conexão SSL. Obsoleto, use config:set com o caminho web/secure/base_url

- Requer um valor

### `--use-secure-admin`

Execute a interface do administrador com SSL. Obsoleto, use config:set com o caminho web/secure/use_in_adminhtml

- Requer um valor

### `--admin-use-security-key`

Usar um recurso de &quot;chave de segurança&quot; nos formulários e URLs do administrador do Magento. Obsoleto, use config:set com o caminho admin/security/use_form_key

- Requer um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:uninstall`

Desinstala o aplicativo Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:upgrade`

Atualiza o aplicativo Magento, os dados do banco de dados e o esquema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Impede que os arquivos gerados sejam excluídos. Desencorajamos o uso dessa opção, exceto ao implantar na produção. Consulte o integrador de sistemas ou administrador para obter mais informações.

- Padrão: `false`
- Não aceita um valor

### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

### `--safe-mode`

Instalação segura de Magento com despejos em operações destrutivas, como remoção de coluna

- Aceita um valor

### `--data-restore`

Restaurar dados removidos de despejos

- Aceita um valor

### `--dry-run`

A instalação do Magento será executada no modo de simulação

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicione a qualquer comando para personalizar parâmetros de inicialização de Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `store:list`

Exibe a lista de armazenamentos

```bash
bin/magento store:list
```

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


## `store:website:list`

Exibe a lista de sites

```bash
bin/magento store:website:list
```

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


## `theme:uninstall`

Desinstala o tema

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

Caminho do tema. O caminho do tema deve ser especificado como o caminho completo, que é área/fornecedor/nome. Por exemplo, front-end/Magento/blank

- Padrão: `[]`

- Obrigatório
- Matriz

### `--backup-code`

Fazer backup do código (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estáticos gerados.

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


## `varnish:vcl:generate`

Gera um VCL verniz e o ecoa na linha de comando

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Lista de acesso IPs que pode limpar o verniz

- Padrão: `localhost`
- Requer um valor

### `--backend-host`

Host do back-end da Web

- Padrão: `localhost`
- Requer um valor

### `--backend-port`

Porta do back-end da Web

- Padrão: `8080`
- Requer um valor

### `--export-version`

A versão do arquivo verniz

- Padrão: `4`
- Requer um valor

### `--grace-period`

Período de carência em segundos

- Padrão: `300`
- Requer um valor

### `--output-file`

Caminho para o arquivo para gravar vcl

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
