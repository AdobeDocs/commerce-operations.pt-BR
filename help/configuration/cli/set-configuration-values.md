---
title: Definir valores de configuração
description: Saiba como definir valores de configuração e alterar valores que estão bloqueados no Administrador.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---


# Definir valores de configuração

{{file-system-owner}}

Este tópico discute os comandos de configuração avançados que você pode usar para:

- Defina qualquer opção de configuração a partir da linha de comando
- Opcionalmente, bloqueie qualquer opção de configuração para que seu valor não possa ser alterado em Admin
- Altere uma opção de configuração bloqueada no Administrador

Você pode usar esses comandos para definir a configuração do Commerce manualmente ou usando scripts. Você define opções de configuração usando um _caminho da configuração_, que é um `/`string delimitada por caracteres que identifica exclusivamente essa opção de configuração. Você pode encontrar caminhos de configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração gerais](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão do Commerce Enterprise B2B](../reference/config-reference-b2b.md)

Você pode definir valores nos seguintes momentos:

- Antes de instalar o Commerce, você pode definir valores de configuração somente para o escopo padrão, pois esse é o único escopo válido.

- Depois de instalar o Commerce, você pode definir valores de configuração para qualquer site ou escopo de visualização de loja.

Use os seguintes comandos:

- `bin/magento config:set` define qualquer valor de configuração não sensível pelo seu caminho de configuração
- `bin/magento config:sensitive:set` define qualquer valor de configuração sensível pelo seu caminho de configuração
- `bin/magento config:show` mostra valores de configuração salvos; valores de configurações criptografadas são exibidos como asteriscos

## Pré-requisitos

Para definir um valor de configuração, você deve saber pelo menos um dos seguintes itens:

- O caminho de configuração
- Para definir um valor de configuração para um escopo específico, você deve saber o código do escopo.

   Para definir um valor de configuração para o escopo padrão, não é necessário fazer nada.

### Encontre o caminho de configuração

Consulte as seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão do Commerce Enterprise B2B](../reference/config-reference-b2b.md)

### Localizar o código de escopo

Você pode encontrar o código do escopo no banco de dados do Commerce ou no Administrador do Commerce.

**Para encontrar o código do escopo no Administrador**:

1. Faça logon no Admin como um usuário que pode visualizar sites e armazenar visualizações.
1. Clique em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL All Stores]**.
1. No painel direito, clique no nome do site ou da exibição de loja para ver seu código.

   A figura a seguir mostra um exemplo de código do site.

   ![Obter um código de exibição de site ou loja no Administrador](../../assets/configuration/website-code.png)

1. Continue com [Definir valores](#set-values).

**Para localizar o código do escopo no banco de dados**:

Os códigos de escopo para sites e exibições de armazenamento são armazenados no banco de dados do Commerce na `store_website` e `store` tabelas, respectivamente.

1. Conecte-se ao banco de dados do Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Insira os seguintes comandos:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Um exemplo de resultado é o seguinte:

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Use o valor na variável `code` coluna.

1. Continue com a próxima seção.

## Definir valores

**Para definir valores de configuração específicos do sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Para definir valores de configuração confidenciais**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

A tabela a seguir descreve o `set` parâmetros de comando:

| Parâmetro | Descrição |
| --- | --- |
| `--scope` | O escopo da configuração. Os valores possíveis são `default`, `website`ou `store`. O padrão é `default`. |
| `--scope-code` | O código de escopo da configuração (código de site ou código de exibição de loja) |
| `-e or --lock-env` | Bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor no `<Commerce base dir>/app/etc/env.php` arquivo. |
| `-c or --lock-config` | Bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor no `<Commerce base dir>/app/etc/config.php` arquivo. O `--lock-config` substitui a opção `--lock-env` se você especificar ambas as opções. |
| `path` | _Obrigatório_. O caminho de configuração |
| `value` | _Obrigatório_. O valor da configuração |

>[!INFO]
>
>A partir do Commerce 2.2.4, a variável `--lock-env` e `--lock-config` substituem o `--lock` opção.
>
>Se você usar a variável `--lock-env` ou `--lock-config` para definir ou alterar um valor, você deve usar a variável [`bin/magento app:config:import` comando](../cli/import-configuration.md) para importar a configuração antes de acessar o Admin ou a loja.

Se você inserir um caminho de configuração incorreto, esse comando retornará um erro

```text
The "wrong/config/path" does not exist
```

Consulte uma das seguintes seções para obter mais informações:

- [Definir valores de configuração que podem ser editados no Administrador](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Definir valores de configuração que não podem ser editados no Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Definir valores de configuração que podem ser editados no Administrador

Use `bin/magento config:set` _without_ `--lock-env` ou `--lock-config` para gravar o valor no banco de dados. Os valores definidos dessa forma podem ser editados no Administrador.

Seguem-se alguns exemplos para definir um URL de base de loja:

Defina o URL base para o escopo padrão:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Defina o URL base para a variável `base` sítio web:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Defina o URL base para a variável `test` exibição de loja:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Definir valores de configuração que não podem ser editados no Administrador

Se você usar a variável `--lock-env`  da seguinte maneira, o comando salva o valor de configuração em `<Commerce base dir>/app/etc/env.php` e desativa o campo para editar esse valor em Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Você pode usar o `--lock-env` para definir valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>O `env.php` O arquivo é específico do sistema. Você não deve transferi-lo para outro sistema. Você pode usá-lo para substituir valores de configuração do banco de dados. Por exemplo, você pode obter um despejo de banco de dados de outro sistema e substituir a variável `base_url` e outros valores para que não seja necessário modificar o banco de dados.

Se você usar a variável `--lock-config` da seguinte maneira, o valor de configuração é salvo em `<Commerce base dir>/app/etc/config.php`. O campo para editar esse valor em Admin está desativado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Você pode usar `--lock-config` para definir valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>Você pode transferir `config.php` para outro sistema para usar os mesmos valores de configuração lá. Por exemplo, se você tiver um sistema de teste, usando o mesmo `config.php` significa que não é necessário definir os mesmos valores de configuração novamente.

## Exibir o valor das configurações

Opções de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

em que

- `--scope` é o escopo da configuração (padrão, site, loja). O valor padrão é `default`
- `--scope-code` é o código de escopo da configuração (código de site ou código de exibição de loja)
- `path` é o caminho de configuração no formato first_part/Second_part/third_part/etc (_obrigatório_)

>[!INFO]
>
>O `bin/magento config:show` exibe os valores de qualquer [valores criptografados](../reference/config-reference-sens.md) como uma série de asteriscos: `******`.

### Exemplos

**Para mostrar todas as configurações salvas**:

```bash
bin/magento config:show
```

Resultado:

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Para mostrar todas as configurações salvas para a `base` site**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Para mostrar o URL base do escopo padrão**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example.com/
```

**Para mostrar o URL base da variável `base` site**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Para mostrar o URL base da variável `default` loja**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
