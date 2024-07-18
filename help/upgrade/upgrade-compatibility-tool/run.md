---
title: Executar o  [!DNL Upgrade Compatibility Tool]
description: Siga estas etapas para executar o  [!DNL Upgrade Compatibility Tool]  em uma interface de linha de comando para o seu projeto do Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Baixar o [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para começar a usar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando, baixe-o executando o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Talvez seja necessário conceder permissões executáveis à ferramenta com o comando `chmod`:

```bash
chmod +x ./uct/bin/uct
```

## O [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando

O [!DNL Upgrade Compatibility Tool] é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.

Veja este [tutorial em vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para saber mais sobre o [!DNL Upgrade Compatibility Tool].

Comandos disponíveis para [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando:

| **Comando** | **Descrição** |
|----------------|-----------------|
| `upgrade:check` | Este comando executa o [!DNL Upgrade Compatibility Tool] analisando todos os módulos instalados nele. |
| `dbschema:diff` | Este comando exibe todas as diferenças do esquema de banco de dados entre duas versões do Adobe Commerce especificadas. |
| `core:code:changes` | Este comando compara sua instalação atual do Adobe Commerce a uma instalação limpa do baunilla. |
| `refactor` | Esse comando corrige automaticamente um conjunto reduzido de problemas. |
| `graphql:compare` | Esse comando fornece a opção de introduzir dois endpoints do GraphQL e comparar seus esquemas. |
| `list` | Este comando retorna uma lista de todos os [!DNL Upgrade Compatibility Tool] comandos disponíveis. |
| `help` | Este comando retorna todas as `help`opções disponíveis para o [!DNL Upgrade Compatibility Tool]. Esse comando pode ser executado, bem como uma opção com os comandos anteriores. |

## Usar o comando `upgrade:check`

O comando `upgrade:check` verifica as alterações do código principal daquela instância específica do Adobe Commerce e todas as alterações do código personalizado instaladas nela.

O comando `upgrade:check` é o principal comando para executar a ferramenta:

```bash
bin/uct upgrade:check <dir>
```

Onde o valor `<dir>` é o diretório onde a instância do Adobe Commerce está localizada.

Opções disponíveis para o comando `upgrade:check`:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: retorna todas as opções disponíveis.</li><li>—current-version: Versão atual do Adobe Commerce. Esse parâmetro é obrigatório e deve ser sempre usado.</li><li>—min-issue-level: você pode filtrar problemas de acordo com o nível mínimo de problema (o valor padrão é AVISO).</li><li>—ignore-current-version-compatibility-issues (ou -i): se você não quiser incluir problemas críticos, erros e avisos da versão atual no seu relatório.</li><li>—coming-version (ou -c): aponta para uma versão específica do Adobe Commerce. O último disponível será usado se omitido.</li></ul> |

O [!DNL Upgrade Compatibility Tool] permite executar o comando `upgrade:check` com uma opção `--ignore-current-version-compatibility-issues`. Use esta opção somente quando quiser obter novos problemas introduzidos com a atualização da sua versão atual para a versão de destino em seu relatório [!DNL Upgrade Compatibility Tool]:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Isso se aplica somente às validações de API do PHP.

### Adicionando a opção `--coming-version`

Você pode comparar sua instalação atual do Adobe Commerce com qualquer versão do Adobe Commerce `>=2.3` usando a opção `--coming-version`.

Você deve fornecer a versão como um parâmetro ao executar o comando `upgrade:check`:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Onde `-c, --coming-version[=COMING-VERSION]` refere-se à versão de destino do Adobe Commerce.

Existem algumas limitações ao executar o `--coming-version`:

- Esse parâmetro se refere a qualquer tag que identifique uma versão específica do Adobe Commerce.
- É um requisito fornecer este explicitamente; fornecer apenas o valor dele não funciona.
- Forneça a versão da marca sem aspas (simples ou duplas): ~~&#39;2.4.1-develop&#39;~~.
- Você NÃO deve fornecer versões mais antigas do que a versão instalada no momento, nem mais antigas do que a 2.3, que é a mais antiga com suporte no momento.

## Usar o comando `dbschema:diff`

Você pode recuperar a diferença entre o esquema do banco de dados de duas versões do Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Onde os argumentos são os seguintes:

- `<current-version>`: qualquer versão do Adobe Commerce para comparação.
- `<target-version>`: também qualquer versão do Adobe Commerce para comparação.

Exemplo de execução:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Usar o comando `core:code:changes`

É possível comparar sua instalação atual do Adobe Commerce para validar se o código principal do Adobe Commerce foi modificado para implementar uma personalização. Este comando mostra apenas uma lista das modificações principais:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Onde os argumentos são os seguintes:

- `<dir>`: diretório de instalação do Adobe Commerce.
- `<vanilla dir>`: diretório de instalação do Adobe Commerce Vanilla.

Opções disponíveis para o comando `core:code:changes`:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Retorna todas as opções de `--help` disponíveis. |

>[!NOTE]
>
> É uma prática recomendada manter o código personalizado fora do código principal. Consulte o [guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) do Adobe Commerce 2.4 para obter mais práticas recomendadas de atualização.

### Instalação do Vanilla

Uma instalação _vanilla_ é uma instalação limpa de uma marca ou ramificação de versão especificada para uma versão de lançamento específica.

O comando `bin/uct core:code:changes` verifica se há uma instância padrão no sistema. Se esta for a primeira vez usando uma instalação baunilha, uma pergunta interativa de linha de comando solicitará que você baixe o projeto baunilha do repositório do Adobe Commerce (`https://repo.magento.com/`).

Você pode executar um comando [!DNL Upgrade Compatibility Tool] com a opção `--vanilla-dir` para especificar o diretório de instalação do Adobe Commerce Vanilla.

Consulte o tópico [Implantar instância básica](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) para obter mais informações.

## Usar o comando `refactor`

O [!DNL Upgrade Compatibility Tool] pode corrigir automaticamente um conjunto reduzido de problemas:

- Funções que podiam ser usadas sem passar um argumento, mas com esse uso agora se tornaram obsoletas.
- Uso de `$this` em modelos de Magento.
- Uso da palavra-chave PHP `final` em métodos privados.

Para isso, execute o comando `refactor`:

```bash
bin/uct refactor <dir>
```

Onde o valor `<dir>` é o diretório onde a instância do Adobe Commerce está localizada.

Opções disponíveis para o comando `refactor`:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `refactor` | `--help`: Retorna todas as opções de `--help` disponíveis. |

## Usar o comando `graphql:compare`

Este comando fornece a opção ao [!DNL Upgrade Compatibility Tool] para introduzir dois endpoints do GraphQL e comparar seus esquemas em busca de alterações perigosas entre eles:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Onde os argumentos são os seguintes:

- `<schema1>`: URL do ponto de extremidade da instalação existente.
- `<schema2>`: URL do ponto de extremidade para a instalação baunilha.

Opções disponíveis para o comando `graphql:compare`:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Retorna todas as opções de `--help` disponíveis. |

## Usar o comando `list`

Para retornar uma lista dos [!DNL Upgrade Compatibility Tool] comandos disponíveis, execute:

```bash
bin/uct list
```

## Usar o comando `help`

Para ver as opções gerais e a ajuda do comando [!DNL Upgrade Compatibility Tool], execute:

```bash
bin/uct --help
```

Que retorna uma lista com todas as opções `help` disponíveis para [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando:

```
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

É possível executar `--help` como uma opção ao executar um comando específico. Retorna `--help` opções para o comando especificado.

Exemplo do comando `upgrade:check` com a opção `--help`:

```bash
bin/uct upgrade:check --help
```

Isso retorna opções específicas que podem ser executadas para o comando `upgrade:check`:

```
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Seguir as práticas recomendadas do Adobe Commerce

- Evite ter dois módulos com o mesmo nome.
- Siga os [padrões de codificação](https://developer.adobe.com/commerce/php/coding-standards/) do Adobe Commerce.
- Práticas recomendadas do [Guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) do Adobe Commerce 2.4.
- Execute o [!DNL Upgrade Compatibility Tool] a partir do [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) para projetos do [Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.

## Otimizar os resultados

O [!DNL Upgrade Compatibility Tool] fornece um relatório contendo resultados com todos os problemas identificados em seu projeto por padrão. Você pode otimizar os resultados para se concentrar nesses problemas que você deve corrigir para concluir a atualização:

- Use a opção `--ignore-current-version-compatibility-issues` somente quando quiser obter novos problemas introduzidos com a atualização da sua versão atual para a versão de destino em seu relatório [!DNL Upgrade Compatibility Tool].
- Adicionando a opção `--min-issue-level`, esta configuração permite definir o nível mínimo de problema, para ajudar a priorizar apenas os problemas mais importantes com sua atualização.
- O [!DNL Upgrade Compatibility Tool] requer pelo menos 2 GB de RAM para ser executado. Essa configuração é recomendada para evitar problemas devido a uma limitação de memória baixa. O [!DNL Upgrade Compatibility Tool] exibe uma pergunta se você executar o comando `upgrade:check` com uma configuração baixa de `memory_limit`.
