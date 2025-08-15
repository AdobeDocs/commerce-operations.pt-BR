---
title: Substituir definições de configuração
description: Saiba como usar variáveis de ambiente para substituir as configurações.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Substituir definições de configuração

Este tópico discute como derivar um nome de variável de ambiente conhecendo um caminho de configuração. Você pode substituir as definições de configuração do Adobe Commerce usando variáveis de ambiente. Por exemplo, você pode substituir o valor do URL ativo de um processador de pagamento em seu sistema de produção.

Você pode substituir o valor de _qualquer_ definição de configuração usando variáveis de ambiente; no entanto, a Adobe recomenda que você mantenha configurações consistentes usando o arquivo de configuração compartilhado, `config.php`, e o arquivo de configuração específico do sistema, `env.php`, conforme discutido na [Visão geral da implantação](../deployment/overview.md).

>[!TIP]
>
>Confira o tópico [Configurar ambientes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) no _guia do Commerce sobre a infraestrutura na nuvem_.

## Variáveis de ambiente

Um nome de variável de ambiente consiste em seu escopo seguido por seu caminho de configuração em um formato específico. As seções a seguir discutem como determinar um nome de variável com mais detalhes.

É possível usar variáveis para qualquer um dos seguintes:

- [Valores confidenciais](config-reference-sens.md) devem ser definidos usando variáveis de ambiente ou o comando [`magento config:sensitive:set`](../cli/set-configuration-values.md).
- Os valores específicos do sistema devem ser definidos usando:

   - Variáveis de ambiente
   - O comando [`magento config:set`](../cli/set-configuration-values.md)
   - O Administrador seguido pelo comando [`magento app:config:dump` ](../cli/export-configuration.md)

Os caminhos de configuração podem ser encontrados em:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](config-reference-payment.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce](config-reference-b2b.md)
- [Referência a outros caminhos de configuração](config-reference-general.md)

### Nomes de variáveis

O formato geral dos nomes das variáveis de configurações do sistema é o seguinte:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` pode ser:

- Escopo global (isto é, a configuração global de _todos_ escopos)

  As variáveis de escopo globais têm o seguinte formato:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Um escopo específico (ou seja, a configuração afeta apenas uma exibição de loja ou site especificado)

  As variáveis de escopo de visualização de armazenamento, por exemplo, têm o seguinte formato:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Para obter mais informações sobre escopos, consulte:

   - [Etapa 1: Localizar o valor do escopo de exibição do site ou da loja](#step-1-find-the-website-or-store-view-scope-value)
   - [Tópico do Guia do Usuário do Commerce sobre o escopo](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Referência rápida do escopo](https://experienceleague.adobe.com/en/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` é o caminho de configuração com caracteres de sublinhado duplo substituído por `/`. Para obter mais informações, consulte [Etapa 2: definir variáveis do sistema](#step-2-set-global-website-or-store-view-variables).

### Formato da variável

`<SCOPE>` está separado de `<SYSTEM__VARIABLE__NAME>` por dois caracteres sublinhados.

`<SYSTEM__VARIABLE__NAME>` é derivado do _caminho de configuração_ de uma definição de configuração, que é uma cadeia de caracteres delimitada por `/` que identifica exclusivamente uma configuração específica. Substitua cada `/` caractere no caminho de configuração por dois caracteres sublinhados para criar a variável de sistema.

Se um caminho de configuração contiver um caractere de sublinhado, ele permanecerá na variável.

Uma lista completa de caminhos de configuração pode ser encontrada em:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](config-reference-payment.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](config-reference-b2b.md)
- [Referência a outros caminhos de configuração](config-reference-general.md)

## Etapa 1: Localizar o valor do escopo de exibição do site ou da loja

Esta seção discute como você pode encontrar e definir valores de configuração do sistema por _escopo_ (exibição de loja ou site). Para definir variáveis de escopo globais, consulte [Etapa 2: Definir variáveis de exibição globais, de site ou de repositório](#step-2-set-global-website-or-store-view-variables).

Os valores de escopo vêm das tabelas `store`, `store_group` e `store_website`.

- A tabela `store` especifica nomes e códigos de exibição de armazenamento
- A tabela `store_website` especifica nomes e códigos de sites

Você também pode encontrar os valores do código usando o Admin.

Como ler a tabela:

- `Path in Admin` coluna

  Os valores antes da vírgula são caminhos na navegação de Admin. Os valores depois da vírgula são opções no painel direito.

- A coluna `Variable name` é o nome da variável de ambiente correspondente.

  Você tem a opção de especificar valores do sistema para esses parâmetros de configuração como variáveis de ambiente, se desejar.

   - O nome inteiro da variável é sempre ALL CAPS
   - Iniciar um nome de variável com `CONFIG__` (observe dois caracteres sublinhados)
   - Você pode encontrar a parte `<STORE_VIEW_CODE>` ou `<WEBSITE_CODE>` de um nome de variável no banco de dados de Administração ou Commerce, conforme indicado nas seções a seguir.
   - Você pode encontrar `<SYSTEM__VARIABLE__NAME>` conforme discutido em [Etapa 2: definir variáveis de exibição globais, de site ou de repositório](#step-2-set-global-website-or-store-view-variables).

### Localizar um escopo de exibição de site ou loja no Administrador

A tabela a seguir resume como localizar o site ou armazenar o valor da exibição no Administrador.

| Descrição | Caminho no administrador | Nome da variável |
|--------------|--------------|----------------------|
| Criar, editar, excluir visualizações de loja | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Criar, editar, excluir sites | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Por exemplo, para localizar um site ou um valor de escopo de exibição de loja no campo Admin:

1. Faça logon no Administrador como um usuário autorizado a visualizar sites.
1. Clique em **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Clique no nome de um site ou exibição de loja.

   O painel direito é exibido de forma semelhante ao seguinte.

   ![Localizar um código de site](../../assets/configuration/website-code.png)

1. O nome do escopo é exibido no campo **[!UICONTROL Code]**.
1. Continuar com [Etapa 2: definir variáveis de exibição globais, de site ou de repositório](#step-2-set-global-website-or-store-view-variables).

### Localizar um escopo de exibição de site ou loja no banco de dados

Para obter esses valores do banco de dados:

1. Faça logon no sistema de desenvolvimento como proprietário do sistema de arquivos, se ainda não tiver feito isso.
1. Digite o seguinte comando:

   ```bash
   mysql -u <database-username> -p
   ```

1. No prompt `mysql>`, digite os seguintes comandos na ordem mostrada:

   ```shell
   use <database-name>;
   ```

1. Use as seguintes consultas SQL para localizar os valores relevantes:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   A seguir, há uma amostra:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Use o valor da coluna `code` como o nome do escopo, não o valor `name`.

   Por exemplo, para definir uma variável de configuração para o Site de teste, use o seguinte formato:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   onde `<SYSTEM__VARIABLE__NAME>` vem da próxima seção.

## Etapa 2: definir variáveis de exibição globais, de site ou de loja

Esta seção discute como definir variáveis do sistema.

- Para definir valores para o escopo global (ou seja, todos os sites, lojas e exibições de loja), inicie o nome da variável com `CONFIG__DEFAULT__`.

- Para definir um valor para uma exibição de loja ou site específico, inicie o nome da variável conforme discutido em [Etapa 1: Localize o valor do escopo](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- A última parte do nome da variável é o caminho de configuração, que é exclusivo para cada definição de configuração.

[Veja alguns exemplos](#examples).

A tabela a seguir mostra alguns exemplos de variáveis.

| Descrição | Caminho no Administrador (omitindo **Lojas** > **Configurações** > **Configuração**) | Nome da variável |
|--------------|--------------|----------------------|
| hostname do servidor do Elasticsearch | Catálogo > **Catálogo**, **Nome de Host do Elasticsearch Server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Porta do servidor do Elasticsearch | Catálogo > **Catálogo**, **Porta do Elasticsearch Server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origem do país de remessa | Vendas > **Configurações de envio** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL de administração personalizada | Avançado > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Caminho de administração personalizado | Avançado > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exemplos

Esta seção mostra como localizar valores de algumas variáveis de exemplo.

### hostname do servidor do Elasticsearch

Para localizar o nome da variável para a minificação global do HTML:

1. Determine o escopo.

   É o escopo global, então o nome da variável começa com `CONFIG__DEFAULT__`

1. O restante do nome da variável é `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultado**: o nome da variável é `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origem do país de remessa

Para localizar o nome da variável para a origem do país de entrega:

1. Determine o escopo.

   Localize o escopo no [banco de dados](#find-a-website-or-store-view-scope-in-the-database) conforme discutido na Etapa 1: encontre o valor do escopo de exibição do site ou do repositório. (Você também pode encontrar o valor no Administrador como mostrado na [tabela da Etapa 2: definir variáveis de exibição globais, de site ou de armazenamento]&#x200B;(#step-2-set-global-website-or-store-view-variables.

   Por exemplo, o escopo pode ser `CONFIG__WEBSITES__DEFAULT`.

1. O restante do nome da variável é `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultado**: o nome da variável é `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Como usar variáveis de ambiente

Defina os valores de configuração como variáveis usando a matriz associada [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) do PHP. Você pode definir os valores em qualquer script PHP executado quando o Commerce é executado.

>[!TIP]
>
>A definição de valores de variável em `index.php` ou `pub/index.php` nem sempre funciona como esperado, pois diferentes pontos de entrada de aplicativo podem ser usados, dependendo da configuração do servidor Web. Ao colocar diretivas `$_ENV` no arquivo `app/bootstrap.php`, independentemente dos diferentes pontos de entrada do aplicativo, as diretivas `$_ENV` sempre são executadas, pois o arquivo `app/bootstrap.php` é carregado como parte da arquitetura do Commerce.

Este é um exemplo de configuração de dois valores `$_ENV`:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Um exemplo passo a passo é mostrado em [Definir valores de configuração usando variáveis de ambiente](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Para usar os valores definidos na matriz `$_ENV`, você deve definir `variables_order = "EGPCS"`(Ambiente, Obtenção, Publicação, Cookie e Servidor) no arquivo `php.ini`. Para obter detalhes, consulte [documentação sobre PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Para o Adobe Commerce na infraestrutura em nuvem, se você estiver tentando substituir as definições de configuração usando a [Interface da Web do Project](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), você deve anexar o nome da variável a `env:` como prefixo. Por exemplo:
>
>![Exemplo de variável de ambiente](../../assets/configuration/cloud-console-envvariable.png)
