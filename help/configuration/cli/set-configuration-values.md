---
title: Definir valores de configuração
description: Saiba como definir valores de configuração e alterar valores de Admin bloqueados no Adobe Commerce. Descubra comandos e técnicas de configuração avançada.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Definir valores de configuração

{{file-system-owner}}

Este tópico discute comandos de configuração avançados que podem ser usados para:

- Definir qualquer opção de configuração na linha de comando
- Opcionalmente, bloqueie qualquer opção de configuração para que seu valor não possa ser alterado no Administrador
- Alterar uma opção de configuração que esteja bloqueada no Administrador

Você pode usar esses comandos para definir a configuração do Commerce manualmente ou usando scripts. Você define opções de configuração usando um _caminho de configuração_, que é uma cadeia de caracteres delimitada por `/` que identifica exclusivamente essa opção de configuração. Você pode encontrar caminhos de configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração geral](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](../reference/config-reference-b2b.md)

Você pode definir valores nos seguintes horários:

- Antes de instalar o Commerce, você pode definir valores de configuração somente para o escopo padrão, pois ele é o único escopo válido.

- Após instalar o Commerce, é possível definir valores de configuração para qualquer escopo de exibição de site ou loja.

Use os seguintes comandos:

- `bin/magento config:set` define qualquer valor de configuração não confidencial por seu caminho de configuração
- `bin/magento config:sensitive:set` define qualquer valor de configuração confidencial por seu caminho de configuração
- `bin/magento config:show` mostra valores de configuração salvos; valores de configurações criptografadas são exibidos como asteriscos

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

Você pode encontrar o código do escopo no banco de dados do Commerce ou no Commerce Admin.

**Para localizar o código do escopo no Admin**:

1. Faça logon no Administrador como um usuário que pode exibir sites e armazenar visualizações.
1. Clique em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL All Stores]**.
1. No painel direito, clique no nome do site ou na exibição de loja para ver o código.

   A figura a seguir mostra um exemplo de código de site.

   ![Obter um código de exibição de site ou loja do Administrador](../../assets/configuration/website-code.png)

1. Continuar com [Definir valores](#set-values).

**Para localizar o código do escopo no banco de dados**:

Os códigos de escopo para sites e exibições de armazenamento são armazenados no banco de dados do Commerce nas tabelas `store_website` e `store`, respectivamente.

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Use o valor na coluna `code`.

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

A tabela a seguir descreve os parâmetros do comando `set`:

| Parâmetro | Descrição |
| --- | --- |
| `--scope` | O escopo da configuração. Os valores possíveis são `default`, `website` ou `store`. O padrão é `default`. |
| `--scope-code` | O código de escopo da configuração (código de site ou código de exibição de loja) |
| `-e or --lock-env` | O bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor no arquivo `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | O bloqueia o valor para que ele não possa ser editado no Administrador ou altera uma configuração que já está bloqueada no Administrador. O comando grava o valor no arquivo `<Commerce base dir>/app/etc/config.php`. A opção `--lock-config` substitui `--lock-env` se você especificar ambas as opções. |
| `path` | _Obrigatório_. O caminho de configuração |
| `value` | _Obrigatório_. O valor da configuração |

>[!INFO]
>
>A partir do Commerce 2.2.4, as opções `--lock-env` e `--lock-config` substituem a opção `--lock`.
>
>Se você usar a opção `--lock-env` ou `--lock-config` para definir ou alterar um valor, deverá usar o comando [`bin/magento app:config:import` ](../cli/import-configuration.md) para importar a configuração antes de acessar o Administrador ou a loja.

Se você inserir um caminho de configuração incorreto, esse comando retornará um erro

```text
The "wrong/config/path" does not exist
```

Consulte uma das seguintes seções para obter mais informações:

- [Defina os valores de configuração que podem ser editados no painel](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Definir valores de configuração que não podem ser editados no Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Defina os valores de configuração que podem ser editados no painel

Use `bin/magento config:set` _sem_ `--lock-env` ou `--lock-config` para gravar o valor no banco de dados. Os valores definidos dessa maneira podem ser editados no Administrador.

A seguir, alguns exemplos para definir um URL de base de armazenamento:

Defina o URL base para o escopo padrão:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Defina a URL de base para o site `base`:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Defina a URL de base para a exibição de armazenamento `test`:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Definir valores de configuração que não podem ser editados no Administrador

Se você usar a opção `--lock-env` da seguinte maneira, o comando salva o valor de configuração em `<Commerce base dir>/app/etc/env.php` e desabilita o campo para edição desse valor no Administrador.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Você pode usar a opção `--lock-env` para definir valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>O arquivo `env.php` é específico do sistema. Você não deve transferi-lo para outro sistema. Você pode usá-lo para substituir valores de configuração do banco de dados. Por exemplo, você pode pegar um despejo de banco de dados de outro sistema e substituir o `base_url` e outros valores para que não seja necessário modificar o banco de dados.

Se você usar a opção `--lock-config` da seguinte maneira, o valor de configuração será salvo em `<Commerce base dir>/app/etc/config.php`. O campo para editar esse valor no Admin está desativado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Você pode usar `--lock-config` para definir valores de configuração se o Commerce não estiver instalado. No entanto, é possível definir valores somente para o escopo padrão.

>[!INFO]
>
>Você pode transferir `config.php` para outro sistema para usar os mesmos valores de configuração. Por exemplo, se você tiver um sistema de teste, usar o mesmo `config.php` significa que não é necessário definir os mesmos valores de configuração novamente.

## Exibir o valor das definições de configuração

Opções de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

onde

- `--scope` é o escopo da configuração (padrão, site, armazenamento). O valor padrão é `default`
- `--scope-code` é o código de escopo da configuração (código de site ou código de exibição de armazenamento)
- `path` é o caminho de configuração no formato primeira_parte/segunda_parte/terceira_parte/etc (_necessário_)

>[!INFO]
>
>O comando `bin/magento config:show` exibe os valores de quaisquer [valores criptografados](../reference/config-reference-sens.md) como uma série de asteriscos: `******`.

### Exemplos

**Para mostrar todas as configurações salvas**:

```bash
bin/magento config:show
```

Resultado:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Para mostrar todas as configurações salvas do site `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultado:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Para mostrar a URL base do escopo padrão**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example.com/
```

**Para mostrar a URL base do site `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example-for-website.com/
```

**Para mostrar a URL base do `default` armazenamento**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>O código do escopo pode incluir somente letras (a-z ou A-Z), números (0-9) e sublinhados (_). Além disso, o primeiro caractere deve ser uma letra. Se forem usadas maiúsculas ou minúsculas como camelo ao criar uma visualização de site ou loja, internamente, a correspondência não diferencia maiúsculas de minúsculas para acomodar a substituição das definições de configuração por meio de variáveis de ambiente. Consulte [Usar variáveis de ambiente para substituir as configurações](../reference/override-config-settings.md#environment-variables).

