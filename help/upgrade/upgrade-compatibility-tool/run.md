---
title: '"Execute o [!DNL Upgrade Compatibility Tool]"'
description: Siga estas etapas para executar o [!DNL Upgrade Compatibility Tool] no seu projeto do Adobe Commerce.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# Baixe o [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para começar a usar o [!DNL Upgrade Compatibility Tool] em uma interface de linha de comando, baixe-a executando o seguinte comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

>[!NOTE]
>
> Consulte a [pré-requisitos](../upgrade-compatibility-tool/prerequisites.md) para obter mais informações sobre os requisitos mínimos para usar a ferramenta.

## Execute o [!DNL Upgrade Compatibility Tool]

O [!DNL Upgrade Compatibility Tool] é uma ferramenta que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.

O [!DNL Upgrade Compatibility Tool] O identifica possíveis problemas que devem ser corrigidos no código antes de tentar atualizar para uma versão mais recente do Adobe Commerce.

Veja isso [tutorial em vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para saber mais sobre a [!DNL Upgrade Compatibility Tool].

## Ações recomendadas

### Otimize seus resultados

O [!DNL Upgrade Compatibility Tool] O fornece um relatório contendo resultados com todos os problemas identificados em seu projeto por padrão. Você pode otimizar os resultados para se concentrar nos problemas que você deve corrigir para concluir a atualização:

- Use a opção `--ignore-current-version-compatibility-issues`, que suprime todos os problemas críticos, erros e avisos conhecidos em relação à versão atual do Adobe Commerce. Ela só fornece erros em relação à versão para a qual você está tentando atualizar.
- Adicione o `--min-issue-level` , essa configuração permite definir o nível mínimo de edição para ajudar a priorizar apenas os problemas mais importantes com sua atualização.
- Se quiser analisar apenas um determinado fornecedor, módulo ou diretório par, também poderá especificar o caminho como uma opção. Execute o `bin` com a opção adicionada `-m`. Isso permite que a variável [!DNL Upgrade Compatibility Tool] para analisar um módulo específico de maneira independente e ajudar com problemas de memória que podem ocorrer ao executar o [!DNL Upgrade Compatibility Tool].

### Siga as práticas recomendadas do Adobe Commerce

- Evite ter dois módulos com o mesmo nome.
- Seguir o Adobe Commerce [normas de codificação](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## Use o `upgrade:check` comando

O `upgrade:check` é o comando principal para executar a ferramenta:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>O `<dir>` é o diretório onde sua instância do Adobe Commerce está localizada.

O `upgrade:check` executa o [!DNL Upgrade Compatibility Tool] e verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica ao analisar todos os módulos instalados nela. Ele retorna uma lista de problemas críticos, erros e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.

>[!WARNING]
>
>Executar somente quando o diretório raiz do projeto (ou principal) for fornecido.

Esse comando verifica as alterações no código principal da instância específica do Adobe Commerce e todas as alterações no código personalizado instaladas na instância.

Você pode executar o `core:code:changes` para analisar apenas as alterações do código principal para essa instância específica do Adobe Commerce. Consulte [Alterações no código principal](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) seção.

Você pode usar o `graphql:compare` para comparar dois esquemas GraphQL e verificar se há alterações entre eles. Consulte a [Verificação de compatibilidade de esquema GraphQL](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) seção.

### Recommendations para usar o `upgrade:check` comando

- O [!DNL Upgrade Compatibility Tool] requer pelo menos 2 GB de RAM para ser executado. Essa configuração é recomendada para evitar problemas devido a uma limitação de memória baixa. O [!DNL Upgrade Compatibility Tool] exibe uma pergunta se você executar a variável `upgrade:check` comando com baixo `memory_limit` configuração.
- Especifique a `-m` para executar a ferramenta em relação a um módulo específico:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `[=MODULE-PATH]`: Diretório de caminho do módulo específico.

### Use o `--help` opção

Para ver o [!DNL Upgrade Compatibility Tool] comando opções gerais e ajuda, executar:

```bash
bin/uct --help
```

No entanto, é possível executar `--help` como uma opção ao executar um comando específico, como `bin/uct upgrade:check`. Isso retorna específico `--help` opções para esse comando:

```bash
bin/uct upgrade:check --help
```

Disponível `--help` para a `upgrade:check` comando:

- `-m, --module-path[=MODULE-PATH]`: Caminho dos módulos a serem analisados
- `-a, --current-version[=CURRENT-VERSION]`: A versão atual do Adobe Commerce, versão da instalação do Adobe Commerce, será usada se omitida.
- `-c, --coming-version[=COMING-VERSION]`: Versão do Adobe Commerce do Target, a versão mais recente do Adobe Commerce será usada se omitida. Fornece uma lista de todas as versões disponíveis do Adobe Commerce.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Caminho do arquivo em que a saída será exportada no formato json.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Caminho do arquivo no qual a saída será exportada no formato HTML.
- `--min-issue-level`: Nível mínimo de problema a ser exibido no relatório. O nível padrão é [AVISO].
- `-i, --ignore-current-version-compatibility-issues`: Use esta opção quando não quiser incluir problemas críticos conhecidos, erros e avisos na sua [!DNL Upgrade Compatibility Tool] relatório.
- `--context=CONTEXT`: Contexto de execução. Essa opção é para fins de integração e não afeta o resultado da execução.
- `-h, --help`: Exibe a ajuda desse comando específico. Se nenhum comando for fornecido, `list` é o resultado padrão.
- `-q, --quiet`: Não envie mensagens durante a execução do comando.
- `-v, --version`: Exibir versão do aplicativo.
- `--ansi, --no-ansi`: Ative a saída ANSI.
- `-n, --no-interaction`: Não faça nenhuma pergunta interativa ao executar o comando.
- `-v, --vv, --vvv, --verbose`: Aumente a verbosidade das comunicações de saída. 1 para saída normal, 2 para saída detalhada e 3 para saída DEBUG.

### Use o `--ignore-current-version-compatibility-issues` opção

O [!DNL Upgrade Compatibility Tool] permite que você execute o `upgrade:check` com um `--ignore-current-version-compatibility-issues` , portanto, mostra somente problemas críticos novos ou desconhecidos, erros e avisos. Use esta opção quando não quiser incluir problemas críticos conhecidos, erros e avisos na sua [!DNL Upgrade Compatibility Tool] relatório.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Isso se aplica somente às validações da API PHP.

### Instalação de baunilha

A _baunilha_ instalação é uma instalação limpa de uma tag ou ramificação de versão especificada para uma versão específica.

O `bin/uct core:code:changes` O comando verifica se há uma instância baunilha no sistema. Se esta for a primeira vez usando uma instalação baunilha, uma pergunta interativa de linha de comando solicitará que você baixe o projeto baunilha do repositório do Adobe Commerce (`https://repo.magento.com/`).

Você pode executar um [!DNL Upgrade Compatibility Tool] com o `--vanilla-dir` para especificar o diretório de instalação Adobe Commerce baunilha.

Consulte a [Implantar instância baunilha](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obter mais informações.

## Use o `list` comando

Para retornar uma lista de [!DNL Upgrade Compatibility Tool] comandos disponíveis, executar:

```bash
bin/uct list
```

O `list` retorna o seguinte:

- `-h, --help`: Exibe a ajuda desse comando específico. Se nenhum comando for fornecido, `list` é o resultado padrão.
- `-q, --quiet`: Não envie mensagens durante a execução do comando.
- `-v, --version`: Exibir versão do aplicativo.
- `--ansi, --no-ansi`: Ative a saída ANSI.
- `-n, --no-interaction`: Não faça nenhuma pergunta interativa ao executar o comando.
- `-v, --vv, --vvv, --verbose`: Aumente a verbosidade das comunicações de saída. 1 para saída normal, 2 para saída detalhada e 3 para saída DEBUG.

## Use o `core:code:changes` comando

Você pode comparar sua instalação atual do Adobe Commerce com uma instalação baunilha limpa para ver se o código principal tem modificações feitas para implementar um novo recurso ou personalização. Essa validação ajuda a estimar o esforço que a atualização requer com base nessas alterações.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.
- `<vanilla dir>`: Diretório de instalação Adobe Commerce vanilla.

Existem algumas limitações ao executar este comando:

- Executar somente quando o diretório raiz do projeto (ou principal) for fornecido.
- Mostra apenas uma lista de modificações principais.

### Use o `core:code:changes` com o `--help` opção

Disponível `--help` para a `core:code:changes` comando:

- `-h, --help`: Exibe a ajuda desse comando específico. Se nenhum comando for fornecido, `list` é o resultado padrão.
- `-q, --quiet`: Não envie mensagens durante a execução do comando.
- `-v, --version`: Exibir versão do aplicativo.
- `--ansi, --no-ansi`: Ative a saída ANSI.
- `-n, --no-interaction`: Não faça nenhuma pergunta interativa ao executar o comando.
- `-v, --vv, --vvv, --verbose`: Aumente a verbosidade das comunicações de saída. 1 para saída normal, 2 para saída detalhada e 3 para saída DEBUG.

## Versão

Você pode comparar sua instalação atual do Adobe Commerce com as versões do Adobe Commerce `>=2.3`.

Você deve fornecer a versão como um parâmetro ao executar o comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>Esse parâmetro fornece uma lista de todas as versões disponíveis do Adobe Commerce.

Em que:

- `-c, --coming-version[=COMING-VERSION]`: A versão de destino do Adobe Commerce.

Existem algumas limitações ao executar o comando anterior:

- Esse parâmetro se refere a qualquer tag que identifique uma versão específica do Adobe Commerce.
- Trata-se de um requisito que prevê explicitamente esta disposição; a condição de apenas o valor não funcionar.
- Forneça a versão da tag sem aspas (nem simples nem duplo): ~~&quot;2.4.1-desenvolver&quot;~~.
- Você NÃO deve fornecer versões mais antigas do que as que instalou atualmente, ou mais antigas do que a 2.3, que é a mais antiga compatível no momento.

### Use o `refactor` comando

O [!DNL Upgrade Compatibility Tool] O tem a capacidade de corrigir automaticamente um conjunto reduzido de problemas:

- Funções que podiam ser usadas sem passar um argumento, mas com esse uso agora se tornaram obsoletas.
- Utilização de `$this` em templates Magento.
- Uso de palavra-chave PHP `final` em métodos privados.

Executar:

```bash
bin/uct refactor <dir>
```

Onde os argumentos são os seguintes:

- `<dir>`: Diretório de instalação do Adobe Commerce.

## Verificação de compatibilidade de esquema GraphQL

O [!DNL Upgrade Compatibility Tool] O também oferece a opção de inserir dois pontos de extremidade GraphQL e comparar seus esquemas que buscam alterações perigosas e de quebra entre eles:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Onde os argumentos são os seguintes:

- `<schema1>`: URL do terminal para a instalação existente.
- `<schema2>`: URL de terminal para a instalação baunilha.

Você deve estar executando `instance before` e `instance after` a atualização.

### comando de comparação GraphQL `--help` opções

Disponível `--help` para a `graphql:compare` comando:

- `-h, --help`: Exibe a ajuda desse comando específico. Se nenhum comando for fornecido, `list` é o resultado padrão.
- `-q, --quiet`: Não envie mensagens durante a execução do comando.
- `-v, --version`: Exibir versão do aplicativo.
- `--ansi, --no-ansi`: Ative a saída ANSI.
- `-n, --no-interaction`: Não faça nenhuma pergunta interativa ao executar o comando.
- `-v, --vv, --vvv, --verbose`: Aumente a verbosidade das comunicações de saída. 1 para saída normal, 2 para saída detalhada e 3 para saída DEBUG.

### Exemplo com uma lista de problemas críticos, erros e avisos para GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

## Solução de problemas

### Erro de falha de segmentação

Quando dois módulos têm o mesmo nome, a variável [!DNL Upgrade Compatibility Tool] mostra um erro de falha de segmentação.

Para evitar esse erro, é recomendável executar a variável `bin` com a opção adicionada `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>O `<dir>` é o diretório onde sua instância do Adobe Commerce está localizada.

O `-m` permite [!DNL Upgrade Compatibility Tool] para analisar cada módulo específico independentemente para evitar encontrar dois módulos com o mesmo nome na instância do Adobe Commerce.

Essa opção de comando também permite [!DNL Upgrade Compatibility Tool] para analisar uma pasta contendo vários módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Essa recomendação também ajuda com problemas de memória que podem ocorrer ao executar o [!DNL Upgrade Compatibility Tool].

### Saída vazia

>[!NOTE]
>
>O `M2_VERSION` é a versão de destino do Adobe Commerce que você deseja comparar com a instância do Adobe Commerce.

Se depois de executar este comando:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

A única saída é `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

A causa provável é uma limitação de memória PHP.
Substitua a limitação de memória definindo `memory_limit` para `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
