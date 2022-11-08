---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '15643'
ht-degree: 0%

---
# bin/magento (Adobe Commerce no local)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Versão**: 2.4.5

Esta referência contém 118 comandos disponíveis através do `bin/magento` ferramenta de linha de comando.
A lista inicial é gerada automaticamente usando o `bin/magento list` na edição.
Use o [&quot;Adicionar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) guia para adicionar um comando CLI personalizado.

>[!NOTE]
>
>Você pode chamar `bin/magento` Comandos CLI usando atalhos em vez do nome completo do comando. Por exemplo, você pode chamar `bin/magento setup:upgrade` usar `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxe de atalho](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para entender como usar atalhos com qualquer comando da CLI.

>[!NOTE]
>
>Essa referência é gerada a partir da base de código do aplicativo. Para alterar o conteúdo, você pode atualizar o código-fonte para a implementação do comando correspondente no [base de código](https://github.com/magento) e envie suas alterações para análise. Outra maneira de _Fornecer feedback_ (localize o link no canto superior direito). Para obter as diretrizes de contribuição, consulte [Contribuições de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Exibir ajuda de um comando

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `list`

Comandos de lista

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```


### `namespace`

O nome do namespace


### `--raw`

Para exibir a lista de comandos brutos

- Padrão: `false`
- Não aceita um valor

### `--format`

O formato de saída (txt, xml, json ou md)

- Padrão: `txt`
- Requer um valor


## `admin:adobe-ims:disable`

Desativar o módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `admin:adobe-ims:enable`

Habilite o Adobe IMS Module.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Defina a ID da organização para a configuração do Adobe IMS. Necessário ao habilitar o módulo

- Aceita um valor

### `--client-id`, `-c`

Defina a ID do cliente para a configuração do Adobe IMS. Necessário ao habilitar o módulo

- Aceita um valor

### `--client-secret`, `-s`

Defina o Segredo do cliente para a configuração do Adobe IMS. Necessário ao habilitar o módulo

- Aceita um valor

### `--2fa`, `-t`

Verifique se o 2FA está ativado para Organização na Adobe Admin Console. Necessário ao habilitar o módulo

- Aceita um valor

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `admin:adobe-ims:info`

Informações sobre a configuração do Adobe IMS Module

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `admin:adobe-ims:status`

Status do módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `admin:user:unlock`

Desbloquear conta de administrador

```bash
bin/magento admin:user:unlock <username>
```


### `username`

O nome de usuário do administrador a ser desbloqueado

- Obrigatório

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `app:config:dump`

Criar despejo do aplicativo

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Lista de tipos de configuração separada por espaços ou omite para despejar todos [escopos, temas, sistema, i18n]

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome de usuário do banco de dados. Deve ter acesso de leitura

- Requer um valor

### `--password`

Senha

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cache:clean`

Limpa o(s) tipo(s) de cache

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de cache separados por espaços ou omite para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cache:disable`

Desativa o(s) tipo(s) de cache

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de cache separados por espaços ou omite para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Lista de tipos de cache separados por espaços ou omite para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cache:flush`

Libera o armazenamento de cache usado pelo(s) tipo(s) de cache

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de cache separados por espaços ou omite para aplicar a todos os tipos de cache.

- Padrão: `[]`

- Matriz

### `--bootstrap`

adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `catalog:images:resize`

Cria imagens de produto redimensionadas

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Redimensionar imagem no modo assíncrono

- Padrão: `false`
- Não aceita um valor

### `--skip_hidden_images`

Não processar imagens marcadas como ocultas na página do produto

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cms:wysiwyg:restrict`

Defina se deseja impor a validação do conteúdo do HTML do usuário ou mostrar um aviso em vez disso

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- Obrigatório

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Caminho de configuração para, por exemplo, group/section/field_name


### `value`

Valor de configuração


### `--interactive`, `-i`

Ativar o modo interativo para definir todas as variáveis confidenciais

- Padrão: `false`
- Não aceita um valor

### `--scope`

Escopo para configuração, se não estiver definido, use &#39;padrão&#39;

- Padrão: `default`
- Aceita um valor

### `--scope-code`

Código de escopo para configuração, string vazia por padrão

- Padrão: &quot;
- Aceita um valor

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Código de escopo (obrigatório somente se o escopo não for &#39;padrão&#39;)

- Requer um valor

### `--lock-env`, `-e`

Bloquear valor que impede a modificação no Administrador (será salvo em app/etc/env.php)

- Padrão: `false`
- Não aceita um valor

### `--lock-config`, `-c`

Bloquear e compartilhar valor com outras instalações impede a modificação no Administrador (será salvo em app/etc/config.php)

- Padrão: `false`
- Não aceita um valor

### `--lock`, `-l`

Obsoleto, use a opção —lock-env.

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `config:show`

Mostra o valor de configuração de um determinado caminho. Se o caminho não for especificado, todos os valores salvos serão mostrados

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Caminho de configuração, por exemplo, section_id/group_id/field_id


### `--scope`

Escopo para configuração, se não especificado, o escopo &#39;padrão&#39; será usado

- Padrão: `default`
- Aceita um valor

### `--scope-code`

Código de escopo (obrigatório somente se o escopo não for `default`)

- Padrão: &quot;
- Aceita um valor

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cron:install`

Gera e instala crontab para o usuário atual

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Forçar tarefas de instalação

- Padrão: `false`
- Não aceita um valor

### `--non-optional`, `-d`

Instalar apenas as tarefas não opcionais (padrão)

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cron:remove`

Remove tarefas de crontab

```bash
bin/magento cron:remove
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `cron:run`

Executa tarefas por programação

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

Executar trabalhos somente a partir de um grupo especificado

- Requer um valor

### `--bootstrap`

Adicionar ou substituir parâmetros do bootstrap

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `deploy:mode:set`

Defina o modo de aplicativo.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

O modo de aplicativo a ser definido. As opções disponíveis são &quot;desenvolvedor&quot; ou &quot;produção&quot;

- Obrigatório

### `--skip-compilation`, `-s`

Ignora a limpeza e a regeneração do conteúdo estático (código gerado, CSS pré-processado e ativos em pub/static/)

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `deploy:mode:show`

Exibe o modo de aplicativo atual.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:di:info`

Fornece informações sobre a configuração de Injeção de Dependência para o Comando.

```bash
bin/magento dev:di:info <class>
```


### `class`

Nome da classe

- Obrigatório

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:email:newsletter-compatibility-check`

Verifica modelos de boletim informativo para possíveis problemas de compatibilidade de uso de variáveis

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:email:override-compatibility-check`

Verifica se há possíveis problemas de compatibilidade de uso de variáveis nas substituições de modelos de email

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:profiler:disable`

Desative o criador de perfis.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:profiler:enable`

Ative o criador de perfis.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Tipo de perfil


### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:query-log:disable`

Desativar log de consulta de BD

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:query-log:enable`

Ativar log de consultas de BD

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Registre todas as consultas. [true\|false]

- Padrão: `true`
- Aceita um valor

### `--query-time-threshold`

Limites de tempo da consulta.

- Padrão: `0.001`
- Aceita um valor

### `--include-call-stack`

Inclua a pilha de chamadas. [true\|false]

- Padrão: `true`
- Aceita um valor

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:source-theme:deploy`

Coleta e publica arquivos de origem para tema.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Arquivos a serem pré-processados (o arquivo deve ser especificado sem extensão)

- Padrão: `css/styles-mcss/styles-l`

- Matriz

### `--type`

Tipo de arquivos de origem: [less]

- Padrão: `less`
- Requer um valor

### `--locale`

Localidade: [en_US]

- Padrão: `en_US`
- Requer um valor

### `--area`

Área: [frontend\|adminhtml]

- Padrão: `frontend`
- Requer um valor

### `--theme`

Tema: [Fornecedor/tema]

- Padrão: `Magento/luma`
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:template-hints:disable`

Desative as dicas do modelo de front-end. Pode ser necessária uma liberação de cache.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:template-hints:enable`

Ativar dicas de modelo de front-end. Pode ser necessária uma liberação de cache.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:template-hints:status`

Mostrar status de dicas do modelo de primeiro plano.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:tests:run`

Executar testes

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Tipo de teste a ser executado. Tipos disponíveis: tudo, unidade, integração, integração tudo, estático, estático-tudo, integridade, herdado, padrão

- Padrão: `default`


### `--arguments`, `-c`

Argumentos adicionais para PHPUnit. Exemplo: &quot;-c&#39;—filter=MyTest&#39;&quot; (sem espaços)

- Padrão: &quot;
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:urn-catalog:generate`

Gera o catálogo de URNs para *.xsd mappings para o IDE para realçar xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Caminho do arquivo para exibir o catálogo. Para PhpStorm, use .idea/misc.xml

- Obrigatório

### `--ide`

Formato no qual o catálogo será gerado. Suportado: [phpstorm, vscode]

- Padrão: `phpstorm`
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `dev:xml:convert`

Converte o arquivo XML usando folhas de estilos XSL

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `downloadable:domains:add`

Adicionar domínios à lista de permissões dos domínios baixáveis

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nome dos domínios

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `encryption:payment-data:update`

Recriptografa os dados de cartão de crédito criptografados com a criptografia mais recente.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Caminho do diretório a ser analisado. Não é necessário se o sinalizador —magento estiver definido


### `--output`, `-o`

Caminho (incluindo o nome do arquivo) para um arquivo de saída. Sem arquivo especificado, o padrão é stdout.

- Requer um valor

### `--magento`, `-m`

Use o parâmetro —magento para analisar a base de código Magento atual. Omita o parâmetro se um diretório for especificado.

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Caminho para o arquivo de dicionário de origem com traduções

- Obrigatório

### `locale`

Local de destino para dicionário, por exemplo &quot;de_DE&quot;

- Obrigatório

### `--mode`, `-m`

Salvar modo para dicionário - &quot;substituir&quot; - substituir pacote de idiomas por novo - &quot;mesclar&quot; - mesclar pacotes de idioma, por padrão &quot;substituir&quot;

- Padrão: `replace`
- Requer um valor

### `--allow-duplicates`, `-d`

Use o parâmetro —allow-duplicates para permitir salvar duplicatas de tradução. Caso contrário, omita o parâmetro .

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `i18n:uninstall`

Desinstala pacotes de idioma

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Nome do pacote de idioma

- Padrão: `[]`

- Obrigatório
- Matriz

### `--backup-code`, `-b`

Faça backup de arquivos de código e configuração (excluindo arquivos temporários)

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `indexer:reindex`

Dados de índices

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `indexer:set-dimensions-mode`

Definir Modo Dimension do Indexador

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nome do indexador [catalog_product_price|catalogpermissions_category]


### `mode`

Modos de dimensão de indexador catalog_product_price none, site, customer_group, site_and_customer_group catalogpermissions_category none, customer_group


### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Tipo de modo de indexador [realtime|schedule]


### `index`

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `indexer:show-dimensions-mode`

Mostra o Modo Dimension do Indexador

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices (catalog_product_price,catalogpermissions_category)

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `indexer:show-mode`

Mostra o Modo de Índice

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Lista de tipos de índice separada por espaços ou omite para aplicar a todos os índices.

- Padrão: `[]`

- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `info:adminuri`

Exibe o URI do administrador do Magento

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do arquivo de relatório

- Padrão: `framework-dependencies.csv`
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do arquivo de relatório

- Padrão: `modules-dependencies.csv`
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do arquivo de relatório

- Padrão: `modules-circular-dependencies.csv`
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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `inventory:reservation:create-compensations`

Criar reservas por argumentos de compensação fornecidos

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Lista de argumentos de compensação no formato &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Padrão: `[]`

- Matriz

### `--raw`, `-r`

Saída bruta

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `inventory:reservation:list-inconsistencies`

Mostrar todos os pedidos e produtos com inconsistências em quantidade comercializável

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Mostrar somente inconsistências para pedidos completos

- Padrão: `false`
- Não aceita um valor

### `--incomplete-orders`, `-i`

Mostrar somente inconsistências para pedidos incompletos

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `inventory-geonames:import`

Baixe e importe nomes geográficos para o algoritmo de seleção de origem

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Lista de códigos de país a importar

- Padrão: `[]`

- Obrigatório
- Matriz

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `maintenance:disable`

Desativa o modo de manutenção

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Endereços IP permitidos (use &#39;nenhum&#39; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Requer um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Endereços IP permitidos (use &#39;nenhum&#39; para limpar a lista de IP permitidos)

- Padrão: `[]`
- Requer um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `media-gallery:sync`

Sincronizar o armazenamento de mídia e os ativos de mídia no banco de dados

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `module:disable`

Desativa os módulos especificados

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

Limpar arquivos de visualização estática gerados. Necessário, se os módulos tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Ativar todos os módulos

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estática gerados. Necessário, se os módulos tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do módulo opcional

- Padrão: `[]`

- Matriz

### `--enabled`

Imprimir apenas módulos ativados

- Padrão: `false`
- Não aceita um valor

### `--disabled`

Imprimir apenas módulos desativados

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Faça backup de arquivos de código e configuração (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--backup-media`

Faça backup de mídia

- Padrão: `false`
- Não aceita um valor

### `--backup-db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

### `--non-composer`

Todos os módulos, que passarão aqui, serão baseados em não compositor

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estática gerados. Necessário, se os módulos tiverem arquivos de visualização estáticos

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `queue:consumers:start`

Iniciar o consumidor do MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

O nome do consumidor a ser iniciado.

- Obrigatório

### `--max-messages`

O número de mensagens a serem processadas pelo consumidor antes do término do processo. Se não especificado - termine após processar todas as mensagens em fila.

- Requer um valor

### `--batch-size`

O número de mensagens por lote. Aplicável apenas ao consumidor do lote.

- Requer um valor

### `--area-code`

O padrão de área preferencial (global, adminhtml etc..) é global.

- Requer um valor

### `--single-thread`

Essa opção impede a execução simultânea de várias cópias de um consumidor.

- Padrão: `false`
- Não aceita um valor

### `--multi-process`

O número de processos por consumidor.

- Aceita um valor

### `--pid-file-path`

O caminho do arquivo para salvar o PID (esta opção está obsoleta, use —single-thread em vez disso)

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `remote-storage:sync`

Sincronize arquivos de mídia com o armazenamento remoto.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `sampledata:deploy`

Implantar módulos de dados de amostra para instalações de Magento com base em compositor

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Atualize o composer.json sem executar a atualização do compositor

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Atualize o composer.json sem executar a atualização do compositor

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `sampledata:reset`

Redefinir todos os módulos de dados de amostra para reinstalação

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `security:recaptcha:disable-for-user-forgot-password`

Desative o reCAPTCHA para usuário administrador esqueceu o formulário de senha

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `security:recaptcha:disable-for-user-login`

Desative o reCAPTCHA para o formulário de logon de usuário administrador

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do usuário

- Obrigatório

### `secret`

Segredo

- Obrigatório

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do usuário

- Obrigatório

### `provider`

Código do provedor

- Obrigatório

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:backup`

Faz backup da base de código, mídia e banco de dados do Magento Application

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Faça backup de arquivos de código e configuração (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--media`

Faça backup de mídia

- Padrão: `false`
- Não aceita um valor

### `--db`

Fazer backup completo do banco de dados

- Padrão: `false`
- Não aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:config:set`

Cria ou modifica a configuração da implantação

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome frontal do backend (será gerado automaticamente se estiver ausente)

- Requer um valor

### `--enable-debug-logging`

Ativar log de depuração

- Requer um valor

### `--enable-syslog-logging`

Habilitar o registro do syslog

- Requer um valor

### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-endpoint`

Ponto final de armazenamento remoto

- Requer um valor

### `--remote-storage-bucket`

Bucket de armazenamento remoto

- Requer um valor

### `--remote-storage-region`

Região de armazenamento remoto

- Requer um valor

### `--remote-storage-key`

Chave de acesso do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-secret`

Chave secreta de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-path-style`

Estilo do caminho de armazenamento remoto

- Padrão: `0`
- Requer um valor

### `--checkout-async`

Habilitar o processamento de pedidos assíncronos? 1 - Sim, 0 - Não

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

virtualhost Amqp

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

### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

### `--queue-default-connection`

Conexão padrão das filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve ser instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

### `--deferred-total-calculating`

Ativar o cálculo total diferido? 1 - Sim, 0 - Não

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

Nome de usuário do servidor de banco de dados

- Requer um valor

### `--db-engine`

Mecanismo do servidor de banco de dados

- Requer um valor

### `--db-password`

Senha do servidor de banco de dados

- Requer um valor

### `--db-prefix`

Prefixo da tabela de banco de dados

- Requer um valor

### `--db-model`

Tipo de banco de dados

- Requer um valor

### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Requer um valor

### `--skip-db-validation`, `-s`

Se especificado, a validação da conexão do db será ignorada

- Padrão: `false`
- Não aceita um valor

### `--http-cache-hosts`

Hosts de cache http

- Requer um valor

### `--db-ssl-key`

Caminho completo do arquivo de chave do cliente para estabelecer a conexão do banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente para estabelecer a conexão do banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer a conexão do db por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-verify`

Verificar a certificação do servidor

- Padrão: `false`
- Não aceita um valor

### `--session-save`

Manipulador de salvamento da sessão

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

Sequência de caracteres exclusiva para ativar conexões persistentes

- Requer um valor

### `--session-save-redis-db`

Número da base de dados Redis

- Requer um valor

### `--session-save-redis-compression-threshold`

Limite de compactação de Redis

- Requer um valor

### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

### `--session-save-redis-log-level`

Nível de log de Redis. Valores: 0 (menos verboso) a 7 (mais verboso)

- Requer um valor

### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar um bloqueio em uma sessão

- Requer um valor

### `--session-save-redis-break-after-frontend`

Número de segundos para aguardar antes de tentar quebrar um bloqueio para a sessão de primeiro plano

- Requer um valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos para aguardar antes de tentar interromper um bloqueio para a sessão de Administrador

- Requer um valor

### `--session-save-redis-first-lifetime`

Duração, em segundos, da sessão para não bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-first-lifetime`

Duração, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-lifetime`

Duração da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

### `--session-save-redis-disable-locking`

Redis desativa o bloqueio. Valores: false (padrão), true

- Requer um valor

### `--session-save-redis-min-lifetime`

Duração da sessão principal do Redis, em segundos

- Requer um valor

### `--session-save-redis-max-lifetime`

Duração máxima da sessão de Redis, em segundos

- Requer um valor

### `--session-save-redis-sentinel-master`

Redis Sentinel principal

- Requer um valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgulas

- Requer um valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verificar principal. Valores: false (padrão), true

- Requer um valor

### `--session-save-redis-sentinel-connect-retries`

Redis Tentativas de conexão do Sentinel.

- Requer um valor

### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

### `--cache-backend-redis-db`

Número do banco de dados para o cache

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

Link de compactação para usar [instantâneo,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

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

Número do banco de dados para o cache

- Requer um valor

### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página completo (use 0 para desativar)

- Requer um valor

### `--page-cache-redis-compression-lib`

Biblioteca de compactação para usar [instantâneo,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--lock-provider`

Bloquear nome do provedor

- Requer um valor

### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

### `--lock-zookeeper-host`

Host e porta para se conectar ao cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/bloqueios

- Requer um valor

### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Requer um valor

### `--document-root-is-pub`

Sinalizador para mostrar é Pub está na raiz, pode ser verdadeiro ou falso apenas

- Requer um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-data:upgrade`

Instala e atualiza dados no banco de dados

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-declaration:generate-patch`

Gere o patch e coloque-o em uma pasta específica.

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Nome do módulo no qual a lista de permissões será gerada

- Padrão: `all`
- Aceita um valor

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-schema:add-slave`

Mover tabelas relacionadas à cotação de finalização para um servidor de banco de dados separado

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host do Servidor de Banco de Dados Escravo

- Padrão: `localhost`
- Requer um valor

### `--dbname`

Nome do Banco de Dados Subordinado

- Requer um valor

### `--username`

Nome de usuário do banco de dados subordinado

- Padrão: `root`
- Requer um valor

### `--password`

Senha do usuário do BD subordinado

- Aceita um valor

### `--connection`

Nome da conexão escrava

- Padrão: `default`
- Aceita um valor

### `--resource`

Nome do recurso subordinado

- Padrão: `default`
- Aceita um valor

### `--maxAllowedLag`

Máx. de Conexão Escrava com Atraso Permitida (em segundos)

- Padrão: &quot;
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-schema:split-quote`

Mova tabelas relacionadas à cotação de check-out para um servidor de banco de dados separado. Obsoleto desde a versão 2.4.2 e será removido

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Fazendo check-out do host do Servidor de Banco de Dados

- Requer um valor

### `--dbname`

Nome do Banco de Dados de Check-out

- Requer um valor

### `--username`

Nome de usuário do banco de dados de check-out

- Requer um valor

### `--password`

Confira a senha do usuário do DB

- Aceita um valor

### `--connection`

Nome da conexão de check-out

- Padrão: `checkout`
- Aceita um valor

### `--resource`

Nome do recurso de check-out

- Padrão: `checkout`
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-schema:split-sales`

Mova tabelas relacionadas às vendas para um servidor de banco de dados separado. Obsoleto desde a versão 2.4.2 e será removido

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host do Servidor de Banco de Dados de Vendas

- Requer um valor

### `--dbname`

Nome do Banco de Dados de Vendas

- Requer um valor

### `--username`

Nome de usuário da BD de Vendas

- Requer um valor

### `--password`

Senha do usuário do banco de dados de vendas

- Aceita um valor

### `--connection`

Nome da conexão de vendas

- Padrão: `sales`
- Aceita um valor

### `--resource`

Nome do recurso de vendas

- Padrão: `sales`
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:db-schema:upgrade`

Instala e atualiza o esquema de banco de dados

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:install`

Instala o aplicativo Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome frontal do backend (será gerado automaticamente se estiver ausente)

- Requer um valor

### `--enable-debug-logging`

Ativar log de depuração

- Requer um valor

### `--enable-syslog-logging`

Habilitar o registro do syslog

- Requer um valor

### `--remote-storage-driver`

Driver de armazenamento remoto

- Requer um valor

### `--remote-storage-prefix`

Prefixo de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-endpoint`

Ponto final de armazenamento remoto

- Requer um valor

### `--remote-storage-bucket`

Bucket de armazenamento remoto

- Requer um valor

### `--remote-storage-region`

Região de armazenamento remoto

- Requer um valor

### `--remote-storage-key`

Chave de acesso do armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-secret`

Chave secreta de armazenamento remoto

- Padrão: &quot;
- Requer um valor

### `--remote-storage-path-style`

Estilo do caminho de armazenamento remoto

- Padrão: `0`
- Requer um valor

### `--checkout-async`

Habilitar o processamento de pedidos assíncronos? 1 - Sim, 0 - Não

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

virtualhost Amqp

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

### `--consumers-wait-for-messages`

Os consumidores devem aguardar uma mensagem da fila? 1 - Sim, 0 - Não

- Requer um valor

### `--queue-default-connection`

Conexão padrão das filas de mensagens. Pode ser &#39;db&#39;, &#39;amqp&#39; ou um sistema de fila personalizado.O sistema de fila deve ser instalado e configurado, caso contrário, as mensagens não serão processadas corretamente.

- Requer um valor

### `--deferred-total-calculating`

Ativar o cálculo total diferido? 1 - Sim, 0 - Não

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

Nome de usuário do servidor de banco de dados

- Requer um valor

### `--db-engine`

Mecanismo do servidor de banco de dados

- Requer um valor

### `--db-password`

Senha do servidor de banco de dados

- Requer um valor

### `--db-prefix`

Prefixo da tabela de banco de dados

- Requer um valor

### `--db-model`

Tipo de banco de dados

- Requer um valor

### `--db-init-statements`

Conjunto inicial de comandos do banco de dados

- Requer um valor

### `--skip-db-validation`, `-s`

Se especificado, a validação da conexão do db será ignorada

- Padrão: `false`
- Não aceita um valor

### `--http-cache-hosts`

Hosts de cache http

- Requer um valor

### `--db-ssl-key`

Caminho completo do arquivo de chave do cliente para estabelecer a conexão do banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-cert`

Caminho completo do arquivo de certificado do cliente para estabelecer a conexão do banco de dados por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-ca`

Caminho completo do arquivo de certificado do servidor para estabelecer a conexão do db por meio do SSL

- Padrão: &quot;
- Requer um valor

### `--db-ssl-verify`

Verificar a certificação do servidor

- Padrão: `false`
- Não aceita um valor

### `--session-save`

Manipulador de salvamento da sessão

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

Sequência de caracteres exclusiva para ativar conexões persistentes

- Requer um valor

### `--session-save-redis-db`

Número da base de dados Redis

- Requer um valor

### `--session-save-redis-compression-threshold`

Limite de compactação de Redis

- Requer um valor

### `--session-save-redis-compression-lib`

Biblioteca de compactação Redis. Valores: gzip (padrão), lzf, lz4, snappy

- Requer um valor

### `--session-save-redis-log-level`

Nível de log de Redis. Valores: 0 (menos verboso) a 7 (mais verboso)

- Requer um valor

### `--session-save-redis-max-concurrency`

Número máximo de processos que podem aguardar um bloqueio em uma sessão

- Requer um valor

### `--session-save-redis-break-after-frontend`

Número de segundos para aguardar antes de tentar quebrar um bloqueio para a sessão de primeiro plano

- Requer um valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos para aguardar antes de tentar interromper um bloqueio para a sessão de Administrador

- Requer um valor

### `--session-save-redis-first-lifetime`

Duração, em segundos, da sessão para não bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-first-lifetime`

Duração, em segundos, da sessão para bots na primeira gravação (use 0 para desativar)

- Requer um valor

### `--session-save-redis-bot-lifetime`

Duração da sessão para bots em gravações subsequentes (use 0 para desativar)

- Requer um valor

### `--session-save-redis-disable-locking`

Redis desativa o bloqueio. Valores: false (padrão), true

- Requer um valor

### `--session-save-redis-min-lifetime`

Duração da sessão principal do Redis, em segundos

- Requer um valor

### `--session-save-redis-max-lifetime`

Duração máxima da sessão de Redis, em segundos

- Requer um valor

### `--session-save-redis-sentinel-master`

Redis Sentinel principal

- Requer um valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por vírgulas

- Requer um valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verificar principal. Valores: false (padrão), true

- Requer um valor

### `--session-save-redis-sentinel-connect-retries`

Redis Tentativas de conexão do Sentinel.

- Requer um valor

### `--cache-backend`

Manipulador de cache padrão

- Requer um valor

### `--cache-backend-redis-server`

Servidor Redis

- Requer um valor

### `--cache-backend-redis-db`

Número do banco de dados para o cache

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

Link de compactação para usar [instantâneo,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

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

Número do banco de dados para o cache

- Requer um valor

### `--page-cache-redis-port`

Porta de escuta do servidor Redis

- Requer um valor

### `--page-cache-redis-password`

Senha do servidor Redis

- Requer um valor

### `--page-cache-redis-compress-data`

Defina como 1 para compactar o cache de página completo (use 0 para desativar)

- Requer um valor

### `--page-cache-redis-compression-lib`

Biblioteca de compactação para usar [instantâneo,lzf,l4z,zstd,gzip] (deixe em branco para determinar automaticamente)

- Requer um valor

### `--page-cache-id-prefix`

Prefixo de ID para chaves de cache

- Requer um valor

### `--lock-provider`

Bloquear nome do provedor

- Requer um valor

### `--lock-db-prefix`

Prefixo de bloqueio específico da instalação para evitar conflitos de bloqueio

- Requer um valor

### `--lock-zookeeper-host`

Host e porta para se conectar ao cluster Zookeeper. Por exemplo: 127.0.0.1:2181

- Requer um valor

### `--lock-zookeeper-path`

O caminho onde o Zookeeper salvará bloqueios. O caminho padrão é: /magento/bloqueios

- Requer um valor

### `--lock-file-path`

O caminho onde os bloqueios de arquivo serão salvos.

- Requer um valor

### `--document-root-is-pub`

Sinalizador para mostrar é Pub está na raiz, pode ser verdadeiro ou falso apenas

- Requer um valor

### `--base-url`

O URL em que a loja deve estar disponível. Obsoleto, use config:set com caminho web/unsecure/base_url

- Requer um valor

### `--language`

Código de idioma padrão. Obsoleto, use config:set com caminho geral/locale/code

- Requer um valor

### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com caminho geral/locale/fuso horário

- Requer um valor

### `--currency`

Código monetário padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

### `--use-rewrites`

Use regravações. Obsoleto, use config:set com caminho web/seo/use_rewrites

- Requer um valor

### `--use-secure`

Use URLs seguros. Habilite esta opção somente se o SSL estiver disponível. Obsoleto, use config:set com caminho web/secure/use_in_frontend

- Requer um valor

### `--base-url-secure`

URL base para conexão SSL. Obsoleto, use config:set com caminho web/secure/base_url

- Requer um valor

### `--use-secure-admin`

Execute a interface de administrador com SSL. Obsoleto, use config:set com o caminho web/secure/use_in_adminhtml

- Requer um valor

### `--admin-use-security-key`

Se você deve usar um recurso de &quot;chave de segurança&quot; em URLs e formulários de Magento Admin. Obsoleto, use config:set com caminho admin/security/use_form_key

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

Mecanismo de pesquisa. Valores: elasticsearch5, elasticsearch6, elasticsearch7

- Requer um valor

### `--elasticsearch-host`

Host de servidor Elasticsearch.

- Requer um valor

### `--elasticsearch-port`

Porta do servidor Elasticsearch.

- Requer um valor

### `--elasticsearch-enable-auth`

Defina como 1 para habilitar a autenticação. (o padrão é 0, desabilitado)

- Requer um valor

### `--elasticsearch-username`

Nome de usuário do Elasticsearch. Aplicável somente se a autenticação HTTP estiver ativada

- Requer um valor

### `--elasticsearch-password`

Senha do Elasticsearch. Aplicável somente se a autenticação HTTP estiver ativada

- Requer um valor

### `--elasticsearch-index-prefix`

Prefixo do índice Elasticsearch.

- Requer um valor

### `--elasticsearch-timeout`

Tempo limite do servidor Elasticsearch.

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

Lista de nomes de módulos separados por vírgulas. Isso deve ser incluído durante a instalação. Param mágico disponível &quot;todos&quot;.

- Aceita um valor

### `--disable-modules`

Lista de nomes de módulos separados por vírgulas. Isso deve ser evitado durante a instalação. Param mágico disponível &quot;todos&quot;.

- Aceita um valor

### `--convert-old-scripts`

Permite converter scripts antigos (InstallSchema, UpgradeSchema) para o formato db_schema.xml

- Padrão: `false`
- Aceita um valor

### `--interactive`, `-i`

Instalação do Magento interativo

- Padrão: `false`
- Não aceita um valor

### `--safe-mode`

Instalação segura de Magento com despejos em operações destrutivas, como remoção de coluna

- Aceita um valor

### `--data-restore`

Restaurar dados removidos dos despejos

- Aceita um valor

### `--dry-run`

A instalação do Magento será executada no modo de execução a seco

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:performance:generate-fixtures`

Gera correções

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:rollback`

Reverte a base de código, a mídia e o banco de dados do Magento Application

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

Nome de base do arquivo de backup de código em var/backups

- Requer um valor

### `--media-file`, `-m`

Nome básico do arquivo de backup de mídia em var/backups

- Requer um valor

### `--db-file`, `-d`

Nome básico do arquivo de backup do db em var/backups

- Requer um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Lista separada por espaços de códigos de idioma ISO-639 para os quais serão enviados arquivos de visualização estática.

- Padrão: `[]`

- Matriz

### `--force`, `-f`

Implante arquivos em qualquer modo.

- Padrão: `false`
- Não aceita um valor

### `--strategy`, `-s`

Implante arquivos usando a estratégia especificada.

- Padrão: `quick`
- Aceita um valor

### `--area`, `-a`

Gere arquivos somente para as áreas especificadas.

- Padrão: `all`
- Aceita vários valores

### `--exclude-area`

Não gerar arquivos para as áreas especificadas.

- Padrão: `none`
- Aceita vários valores

### `--theme`, `-t`

Gere arquivos de visualização estática somente para os temas especificados.

- Padrão: `all`
- Aceita vários valores

### `--exclude-theme`

Não gerar arquivos para os temas especificados.

- Padrão: `none`
- Aceita vários valores

### `--language`, `-l`

Gere arquivos somente para os idiomas especificados.

- Padrão: `all`
- Aceita vários valores

### `--exclude-language`

Não gere arquivos para os idiomas especificados.

- Padrão: `none`
- Aceita vários valores

### `--jobs`, `-j`

Habilite o processamento paralelo usando o número especificado de tarefas.

- Padrão: `0`
- Aceita um valor

### `--max-execution-time`

O tempo máximo de execução esperado do processo estático de implantação (em segundos).

- Padrão: `900`
- Aceita um valor

### `--symlink-locale`

Crie links simbólicos para os arquivos dessas localidades, que são passados para implantação, mas não têm personalizações.

- Padrão: `false`
- Não aceita um valor

### `--content-version`

A versão personalizada do conteúdo estático pode ser usada se a implantação for executada em vários nós para garantir que a versão do conteúdo estático seja idêntica e o armazenamento em cache funcione corretamente.

- Requer um valor

### `--refresh-content-version-only`

Atualizar a versão do conteúdo estático somente pode ser usado para atualizar o conteúdo estático no cache do navegador e no cache CDN.

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

Não implante arquivos MENOS.

- Padrão: `false`
- Não aceita um valor

### `--no-images`

Não implante imagens.

- Padrão: `false`
- Não aceita um valor

### `--no-fonts`

Não implante arquivos de fonte.

- Padrão: `false`
- Não aceita um valor

### `--no-html`

Não implante arquivos HTML.

- Padrão: `false`
- Não aceita um valor

### `--no-misc`

Não implante arquivos de outros tipos (.md, .jbf, .csv, etc.).

- Padrão: `false`
- Não aceita um valor

### `--no-html-minify`

Não minificar arquivos HTML.

- Padrão: `false`
- Não aceita um valor

### `--no-parent`

Não compilar temas principais. Suportado somente em estratégias rápidas e padrão.

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:store-config:set`

Instala a configuração da loja. Obsoleto desde 2.2.0. Use config:set em vez disso

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

O URL em que a loja deve estar disponível. Obsoleto, use config:set com caminho web/unsecure/base_url

- Requer um valor

### `--language`

Código de idioma padrão. Obsoleto, use config:set com caminho geral/locale/code

- Requer um valor

### `--timezone`

Código de fuso horário padrão. Obsoleto, use config:set com caminho geral/locale/fuso horário

- Requer um valor

### `--currency`

Código monetário padrão. Obsoleto, use config:set com o caminho currency/options/base, currency/options/default e currency/options/allow

- Requer um valor

### `--use-rewrites`

Use regravações. Obsoleto, use config:set com caminho web/seo/use_rewrites

- Requer um valor

### `--use-secure`

Use URLs seguros. Habilite esta opção somente se o SSL estiver disponível. Obsoleto, use config:set com caminho web/secure/use_in_frontend

- Requer um valor

### `--base-url-secure`

URL base para conexão SSL. Obsoleto, use config:set com caminho web/secure/base_url

- Requer um valor

### `--use-secure-admin`

Execute a interface de administrador com SSL. Obsoleto, use config:set com o caminho web/secure/use_in_adminhtml

- Requer um valor

### `--admin-use-security-key`

Se você deve usar um recurso de &quot;chave de segurança&quot; em URLs e formulários de Magento Admin. Obsoleto, use config:set com caminho admin/security/use_form_key

- Requer um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `setup:upgrade`

Atualiza o aplicativo do Magento, os dados do banco de dados e o esquema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Impede que os arquivos gerados sejam excluídos. Desincentivamos o uso dessa opção, exceto ao implantar na produção. Consulte o integrador de sistema ou o administrador para obter mais informações.

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

Restaurar dados removidos dos despejos

- Aceita um valor

### `--dry-run`

A instalação do Magento será executada no modo de execução a seco

- Padrão: `false`
- Aceita um valor

### `--magento-init-params`

Adicionar a qualquer comando para personalizar os parâmetros de inicialização do Magento Por exemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `store:list`

Exibe a lista de lojas

```bash
bin/magento store:list
```

### `--help`, `-h`

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `support:backup:code`

Criar backup de código

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

Nome do despejo

- Aceita um valor

### `--output`, `-o`

Caminho de saída

- Aceita um valor

### `--logs`, `-l`

Incluir logs

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `support:backup:db`

Criar backup de banco de dados

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

Nome do despejo

- Aceita um valor

### `--output`, `-o`

Caminho de saída

- Aceita um valor

### `--logs`, `-l`

Incluir logs

- Padrão: `false`
- Não aceita um valor

### `--ignore-sanitize`, `-i`

Ignorar sanitize

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `support:utility:check`

Verifique os utilitários de backup necessários

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

Verifique apenas os utilitários de console necessários

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `support:utility:paths`

Criar lista de caminhos de utilitários

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

Força

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

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

Caminho do tema. O caminho do tema deve ser especificado como um caminho completo que seja área/fornecedor/nome. Por exemplo, frontend/Magento/blank

- Padrão: `[]`

- Obrigatório
- Matriz

### `--backup-code`

Faça backup do código (excluindo arquivos temporários)

- Padrão: `false`
- Não aceita um valor

### `--clear-static-content`, `-c`

Limpar arquivos de visualização estática gerados.

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

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor


## `varnish:vcl:generate`

Gera VCL Varnish e a exibe na linha de comando

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Lista de acesso de IPs que pode limpar o Varnish

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

A versão do arquivo Varnish

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

Exibir esta mensagem de ajuda

- Padrão: `false`
- Não aceita um valor

### `--quiet`, `-q`

Não gerar nenhuma mensagem

- Padrão: `false`
- Não aceita um valor

### `--verbose`, `-v|-vv|-vvv`

Aumente a verbosidade das mensagens: 1 para saída normal, 2 para saída mais detalhada e 3 para depuração

- Padrão: `false`
- Não aceita um valor

### `--version`, `-V`

Exibir esta versão do aplicativo

- Padrão: `false`
- Não aceita um valor

### `--ansi`

Forçar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-ansi`

Desativar saída ANSI

- Padrão: `false`
- Não aceita um valor

### `--no-interaction`, `-n`

Não faça nenhuma pergunta interativa

- Padrão: `false`
- Não aceita um valor
