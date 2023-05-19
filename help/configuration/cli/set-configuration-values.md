---
title: Definir valores de configuração
description: Saiba como definir valores de configuração e alterar valores bloqueados no Administrador.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Definir valores de configuração

{{file-system-owner}}

Este tópico discute comandos de configuração avançados que podem ser usados para:

- Definir qualquer opção de configuração na linha de comando
- Opcionalmente, bloqueie qualquer opção de configuração para que seu valor não possa ser alterado no Administrador
- Alterar uma opção de configuração que esteja bloqueada no Administrador

Você pode usar esses comandos para definir a configuração do Commerce manualmente ou usando scripts. Defina as opções de configuração usando um _caminho de configuração_, que é uma `/`-uma string delimitada que identifica exclusivamente essa opção de configuração. Você pode encontrar caminhos de configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração geral](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](../reference/config-reference-b2b.md)

Você pode definir valores nos seguintes horários:

- Antes de instalar o Commerce, você pode definir valores de configuração somente para o escopo padrão, pois ele é o único escopo válido.

- Depois de instalar o Commerce, você pode definir os valores de configuração para qualquer escopo de exibição de site ou loja.

Use os seguintes comandos:

- `bin/magento config:set` define qualquer valor de configuração não confidencial por seu caminho de configuração
- `bin/magento config:sensitive:set` define qualquer valor de configuração confidencial por seu caminho de configuração
- `bin/magento config:show` mostra os valores de configuração salvos; os valores das configurações criptografadas são exibidos como asteriscos

## Pré-requisitos

Para definir um valor de configuração, você deve saber pelo menos um dos seguintes itens:

- O caminho de configuração
- Para definir um valor de configuração para um escopo específico, você deve saber o código do escopo.

   Para definir um valor de configuração para o escopo padrão, não é necessário fazer nada.

### Encontrar o caminho de configuração

Consulte as seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência a outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](../reference/config-reference-b2b.md)

### Localizar o código do escopo

Você pode encontrar o código do escopo no banco de dados do Commerce ou no Administrador do Commerce.

**Para encontrar o código do escopo no Administrador**:

1. Faça logon no Administrador como um usuário que pode exibir sites e armazenar visualizações.
1. Clique em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL All Stores]**.
1. No painel direito, clique no nome do site ou na exibição de loja para ver o código.

   A figura a seguir mostra um exemplo de código de site.

   ![Obter um código de exibição de site ou loja do Administrador](../../assets/configuration/website-code.png)

1. Continuar com [Definir valores](#set-values).

**Para encontrar o código do escopo no banco de dados**:

Os códigos de escopo para sites e exibições de loja são armazenados no banco de dados do Commerce na `store_website` e `store` tabelas, respectivamente.

1. Conecte-se ao banco de dados do Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Digite os seguintes comandos:

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

1. Prossiga para a próxima seção.

## Definir valores

**Para definir valores de configuração específicos do sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Para definir valores de configuração confidenciais**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

A tabela a seguir descreve as `set` parâmetros de comando:

| Parâmetro | Descrição |
| --- | --- |
| `--scope` | O escopo da configuração. Os valores possíveis são `default`, `website`ou `store`. O padrão é `default`. |
| `--scope-code` | O código de escopo da configuração (código de site ou código de exibição de loja) |
| `-e or --lock-env` | O bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor na variável `<Commerce base dir>/app/etc/env.php` arquivo. |
| `-c or --lock-config` | O bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor na variável `<Commerce base dir>/app/etc/config.php` arquivo. A variável `--lock-config` a opção substitui `--lock-env` se você especificar ambas as opções. |
| `path` | _Obrigatório_. O caminho de configuração |
| `value` | _Obrigatório_. O valor da configuração |

>[!INFO]
>
>A partir do Commerce 2.2.4, o `--lock-env` e `--lock-config` as opções substituem o `--lock` opção.
>
>Se você usar o `--lock-env` ou `--lock-config` para definir ou alterar um valor, você deve usar a opção [`bin/magento app:config:import` comando](../cli/import-configuration.md) para importar a configuração antes de acessar o Admin ou a loja.

Se você inserir um caminho de configuração incorreto, esse comando retornará um erro

```text
The "wrong/config/path" does not exist
```

Consulte uma das seguintes seções para obter mais informações:

- [Defina os valores de configuração que podem ser editados no painel](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Definir valores de configuração que não podem ser editados no Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Defina os valores de configuração que podem ser editados no painel

Uso `bin/magento config:set` _sem_ `--lock-env` ou `--lock-config` para gravar o valor no banco de dados. Os valores definidos dessa maneira podem ser editados no Administrador.

A seguir, alguns exemplos para definir um URL de base de armazenamento:

Defina o URL base para o escopo padrão:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Defina o URL de base para a variável `base` site:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Defina o URL de base para a variável `test` exibição de loja:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Definir valores de configuração que não podem ser editados no Administrador

Se você usar o `--lock-env`  da seguinte maneira, o comando salva o valor de configuração em `<Commerce base dir>/app/etc/env.php` e desativa o campo para editar esse valor no campo Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Você pode usar o `--lock-env` opção para definir valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>A variável `env.php` O arquivo é específico do sistema. Você não deve transferi-lo para outro sistema. Você pode usá-lo para substituir valores de configuração do banco de dados. Por exemplo, você pode pegar um dump de banco de dados de outro sistema e substituir o `base_url` e outros valores para que você não precise modificar o banco de dados.

Se você usar o `--lock-config` da seguinte maneira, o valor de configuração é salvo em `<Commerce base dir>/app/etc/config.php`. O campo para editar esse valor no Admin está desativado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Você pode usar `--lock-config` para definir os valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>Você pode transferir `config.php` para outro sistema para usar os mesmos valores de configuração. Por exemplo, se você tiver um sistema de teste, usando o mesmo `config.php` significa que não é necessário definir os mesmos valores de configuração novamente.

## Exibir o valor das definições de configuração

Opções de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

onde

- `--scope` é o escopo da configuração (padrão, site, loja). O valor padrão é `default`
- `--scope-code` é o código de escopo da configuração (código de site ou código de exibição de loja)
- `path` é o caminho de configuração no formato primeira_parte/segunda_parte/terceira_parte/etc (_obrigatório_)

>[!INFO]
>
>A variável `bin/magento config:show` exibe os valores de qualquer [valores codificados](../reference/config-reference-sens.md) como uma série de asteriscos: `******`.

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

**Para mostrar todas as configurações salvas para o `base` site**:

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
