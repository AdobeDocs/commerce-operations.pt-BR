---
title: '"Execute o [!DNL Upgrade Compatibility Tool]"'
description: Siga estas etapas para executar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando para seu projeto do Adobe Commerce.
source-git-commit: a0bb188eea38688c5bfe68e8c6bb7b3d040f5e0a
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# Baixe o [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para começar a usar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando, baixe-a executando o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Talvez seja necessário dar à ferramenta permissões executáveis com o `chmod` comando:

```bash
chmod +x ./uct/bin/uct
```

## O [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando

O [!DNL Upgrade Compatibility Tool] é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.

Veja isso [tutorial em vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para saber mais sobre a [!DNL Upgrade Compatibility Tool].

Comandos disponíveis para o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando:

| **Comando** | **Descrição** |
|----------------|-----------------|
| `upgrade:check` | Esse comando executa o [!DNL Upgrade Compatibility Tool] analisando todos os módulos instalados nele. |
| `core:code:changes` | Este comando compara a instalação atual do Adobe Commerce com uma instalação baunilha limpa. |
| `refactor` | Esse comando corrige automaticamente um conjunto reduzido de problemas. |
| `graphql:compare` | Este comando fornece a opção de introspecção de dois pontos de extremidade GraphQL e comparação de seus esquemas. |
| `list` | Esse comando retorna uma lista de todos os [!DNL Upgrade Compatibility Tool] comandos disponíveis. |
| `help` | Este comando retorna todos os disponíveis `help`para a [!DNL Upgrade Compatibility Tool]. Esse comando pode ser executado, bem como uma opção com os comandos anteriores. |

## Use o `upgrade:check` comando

O `upgrade:check` O comando verifica se há alterações no código principal para essa instância específica do Adobe Commerce e todas as alterações no código personalizado instaladas nela.

O `upgrade:check` é o comando principal para executar a ferramenta:

```bash
bin/uct upgrade:check <dir>
```

Onde `<dir>` é o diretório onde sua instância do Adobe Commerce está localizada.

Opções disponíveis para o `upgrade:check` comando:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—ajuda: Retorna todas as opções disponíveis.</li><li>—nível mínimo de edição: Você pode filtrar os problemas de acordo com o nível mínimo de emissão (o valor padrão é AVISO).</li><li>—ignore-current-version-compatibility-issues (ou -i): Se você não quiser incluir problemas críticos, erros e avisos da versão atual em seu relatório.</li><li>—versão futura (ou -c): Direcione uma versão específica do Adobe Commerce.</li></ul> |

O [!DNL Upgrade Compatibility Tool] permite que você execute o `upgrade:check` com um `--ignore-current-version-compatibility-issues` opção. Use esta opção quando quiser obter apenas novos problemas que foram introduzidos com a atualização da sua versão atual para a versão direcionada em seu [!DNL Upgrade Compatibility Tool] relatório:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Isso se aplica somente às validações da API PHP.

### Adicionar a `--coming-version` opção

Você pode comparar sua instalação atual do Adobe Commerce com qualquer versão do Adobe Commerce `>=2.3` usando o `--coming-version` opção.

É necessário fornecer a versão como parâmetro ao executar o `upgrade:check` comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Onde `-c, --coming-version[=COMING-VERSION]` refere-se à versão de destino do Adobe Commerce.

Há algumas limitações ao executar o `--coming-version`:

- Esse parâmetro se refere a qualquer tag que identifique uma versão específica do Adobe Commerce.
- Trata-se de um requisito que prevê explicitamente esta disposição; a condição de apenas o valor não funcionar.
- Forneça a versão da tag sem aspas (nem simples nem duplo): ~~&quot;2.4.1-desenvolver&quot;~~.
- Você NÃO deve fornecer versões mais antigas do que as que instalou atualmente, ou mais antigas do que a 2.3, que é a mais antiga compatível no momento.

## Use o `core:code:changes` comando

Você pode comparar sua instalação atual do Adobe Commerce para validar se o código principal do Adobe Commerce foi modificado para implementar uma personalização. Este comando mostra apenas uma lista de modificações principais:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `<vanilla dir>`: Diretório de instalação Adobe Commerce vanilla.

Opções disponíveis para o `core:code:changes` comando:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Retorna todos os disponíveis `--help` opções. |

>[!NOTE]
>
> É uma prática recomendada manter o código personalizado fora do código principal. Veja o Adobe Commerce 2.4 [guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) para obter mais práticas recomendadas de atualização.

### Instalação de baunilha

A _baunilha_ instalação é uma instalação limpa de uma tag ou ramificação de versão especificada para uma versão específica.

O `bin/uct core:code:changes` O comando verifica se há uma instância baunilha no sistema. Se esta for a primeira vez usando uma instalação baunilha, uma pergunta interativa de linha de comando solicitará que você baixe o projeto baunilha do repositório do Adobe Commerce (`https://repo.magento.com/`).

Você pode executar um [!DNL Upgrade Compatibility Tool] com o `--vanilla-dir` para especificar o diretório de instalação Adobe Commerce baunilha.

Consulte a [Implantar instância baunilha](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obter mais informações.

## Use o `refactor` comando

O [!DNL Upgrade Compatibility Tool] O tem a capacidade de corrigir automaticamente um conjunto reduzido de problemas:

- Funções que podiam ser usadas sem passar um argumento, mas com esse uso agora se tornaram obsoletas.
- Utilização de `$this` em templates Magento.
- Uso de palavra-chave PHP `final` em métodos privados.

Para isso, execute o `refactor` comando:

```bash
bin/uct refactor <dir>
```

Onde `<dir>` é o diretório onde sua instância do Adobe Commerce está localizada.

Opções disponíveis para o `refactor` comando:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `refactor` | `--help`: Retorna todos os disponíveis `--help` opções. |

## Use o `graphql:compare` comando

Esse comando fornece a opção para [!DNL Upgrade Compatibility Tool] para analisar dois pontos de extremidade GraphQL e comparar seus esquemas que buscam alterações perigosas e de quebra entre eles:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Onde os argumentos são os seguintes:

- `<schema1>`: URL do terminal para a instalação existente.
- `<schema2>`: URL de terminal para a instalação baunilha.

Opções disponíveis para o `graphql:compare` comando:

| **Comando** | **Opções disponíveis** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Retorna todos os disponíveis `--help` opções. |

## Use o `list` comando

Para retornar uma lista de [!DNL Upgrade Compatibility Tool] comandos disponíveis, executar:

```bash
bin/uct list
```

## Use o `--help` comando

Para ver o [!DNL Upgrade Compatibility Tool] comando opções gerais e ajuda, executar:

```bash
bin/uct --help
```

Isso retorna uma lista com todas as opções disponíveis `help` para a [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando:

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

No entanto, é possível executar `--help` como uma opção ao executar um comando específico. Isso retornará informações específicas `--help` opções para esse comando específico.

Exemplo da variável `upgrade:check` comando com `--help` opção:

```bash
bin/uct upgrade:check --help
```

Isso retorna opções específicas que podem ser executadas para a variável `upgrade:check` comando:

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Siga as práticas recomendadas do Adobe Commerce

- Evite ter dois módulos com o mesmo nome.
- Seguir o Adobe Commerce [normas de codificação](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [Guia de atualização](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) práticas recomendadas.

## Otimize seus resultados

O [!DNL Upgrade Compatibility Tool] O fornece um relatório contendo resultados com todos os problemas identificados em seu projeto por padrão. Você pode otimizar os resultados para se concentrar nos problemas que você deve corrigir para concluir a atualização:

- Use a opção `--ignore-current-version-compatibility-issues` quando quiser obter apenas novos problemas que foram introduzidos com a atualização da sua versão atual para a versão direcionada em seu [!DNL Upgrade Compatibility Tool] relatório.
- Adicionar a `--min-issue-level` , essa configuração permite definir o nível mínimo de edição para ajudar a priorizar apenas os problemas mais importantes com sua atualização.
- O [!DNL Upgrade Compatibility Tool] requer pelo menos 2 GB de RAM para ser executado. Essa configuração é recomendada para evitar problemas devido a uma limitação de memória baixa. O [!DNL Upgrade Compatibility Tool] exibe uma pergunta se você executar a variável `upgrade:check` comando com baixo `memory_limit` configuração.
- Se quiser analisar apenas um determinado fornecedor, módulo ou diretório par, também poderá especificar o caminho como uma opção. Execute o `bin` com a opção adicionada `-m`. Isso permite que a variável [!DNL Upgrade Compatibility Tool] para analisar um módulo específico de maneira independente e ajudar com problemas de memória que podem ocorrer ao executar o [!DNL Upgrade Compatibility Tool]. Especifique a `-m` para executar a ferramenta em relação a um módulo específico:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `[=MODULE-PATH]`: Diretório de caminho do módulo específico.
