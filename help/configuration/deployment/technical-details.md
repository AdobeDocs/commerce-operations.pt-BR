---
title: Detalhes técnicos
description: Leia sobre os detalhes técnicos da implantação de pipeline, os tipos de configurações e os fluxos de trabalho recomendados.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Detalhes técnicos

Este tópico discute detalhes de implementação técnica sobre a implantação de pipeline no Commerce 2.2 e versões posteriores. As melhorias podem ser divididas nas seguintes áreas:

- [Gerenciamento de configuração](#configuration-management)
- [Alterações no Administrador](#changes-in-the-admin)
- [Instalar e remover o cron](#install-and-remove-cron)

Este tópico também discute o [fluxo de trabalho recomendado](#recommended-workflow) para implantação do pipeline e fornece alguns exemplos para ajudá-lo a entender como ele funciona.

Antes de começar, leia os [Pré-requisitos para os sistemas de desenvolvimento, compilação e produção](../deployment/prerequisites.md).

## Gerenciamento de configuração

Para permitir que você sincronize e mantenha a configuração dos sistemas de desenvolvimento e produção, use o esquema de substituição a seguir.

![Como os valores da variável de configuração são determinados](../../assets/configuration/override-flow-diagram.png)

Como mostra o diagrama, os valores de configuração são usados na seguinte ordem:

1. As variáveis de ambiente, se existirem, substituirão todos os outros valores.
1. Dos arquivos de configuração compartilhados `env.php` e `config.php`. Valores em `env.php` substituem valores em `config.php`.
1. De valores armazenados no banco de dados.
1. Se não houver valor em nenhuma dessas origens, o valor default ou NULL será usado.

### Gerenciar a configuração compartilhada

A configuração compartilhada está armazenada em `app/etc/config.php`, que deve estar no controle do código-fonte.

Defina a configuração compartilhada no Administrador em seu sistema de desenvolvimento (ou Adobe Commerce na infraestrutura de nuvem _integração_) e grave a configuração em `config.php` usando o comando [`magento app:config:dump`](../cli/export-configuration.md).

### Gerenciar a configuração específica do sistema

A configuração específica do sistema é armazenada em `app/etc/env.php`, que deve _não_ estar no controle de origem.

Defina a configuração específica do sistema no Admin em seu sistema de desenvolvimento (ou Adobe Commerce na integração da infraestrutura em nuvem) e grave a configuração em `env.php` usando o comando [`magento app:config:dump` ](../cli/export-configuration.md).

Este comando também grava configurações confidenciais em `env.php`.

### Gerenciar a configuração confidencial

A configuração confidencial também é armazenada em `app/etc/env.php`.

Você pode gerenciar a configuração confidencial de qualquer uma das seguintes maneiras:

- Variáveis de ambiente
- Salve a configuração confidencial em `env.php` em seu sistema de produção usando o comando [`magento config:set:sensitive`](../cli/set-configuration-values.md)

### Configurações bloqueadas no Admin

Todas as definições de configuração em `config.php` ou `env.php` estão bloqueadas no Administrador; ou seja, essas definições não podem ser alteradas no Administrador.
Use o comando [`magento config:set` ou `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) para alterar as configurações nos arquivos `config.php` ou `env.php`.

## O administrador do Commerce

O Administrador exibe o seguinte comportamento enquanto está no modo de produção:

- Não é possível ativar ou desativar os tipos de cache no Administrador
- As configurações do desenvolvedor não estão disponíveis (**Lojas** > Configurações > **Configuração** > Avançado > **Desenvolvedor**), incluindo:

   - Reduza CSS, JavaScript e HTML
   - Mesclar CSS e JavaScript
   - Compilação LESS do lado do servidor ou do lado do cliente
   - Traduções integradas
   - Conforme discutido anteriormente, qualquer definição de configuração em `config.php` ou `env.php` está bloqueada e não pode ser editada no Administrador.
   - Você pode alterar a localidade do administrador somente para idiomas usados por temas implantados

     A figura a seguir mostra um exemplo da lista **Configuração da Conta** > **Localidade da Interface** no Administrador mostrando apenas duas localidades implantadas:

     ![Você pode alterar a localidade do Administrador somente para localidades implantadas](../../assets/configuration/split-deploy-admin-locale.png)

- Não é possível alterar as configurações de local de nenhum escopo usando o Administrador.

  Recomendamos fazer essas alterações antes de alternar para o modo de Produção.

  Você ainda pode configurar a localidade usando variáveis de ambiente ou o comando da CLI `config:set` com o caminho `general/locale/code`.

## Instalar e remover o cron

Na versão 2.2, pela primeira vez, ajudamos você a configurar seu trabalho cron fornecendo o comando [`magento cron:install` ](../cli/configure-cron-jobs.md). Este comando configura um crontab como o usuário que executa o comando.

Além disso, você pode remover o crontab usando o comando `magento cron:remove`.

## Fluxo de trabalho de implantação de pipeline recomendado

O diagrama a seguir mostra como recomendamos usar a implantação de pipeline para gerenciar a configuração.

![Fluxo de trabalho de implantação de pipeline recomendado](../../assets/configuration/split-deploy-workflow.png)

### Sistema de desenvolvimento

No sistema de desenvolvimento, você faz alterações de configuração no Administrador e gera a configuração compartilhada, `app/etc/config.php`, e a configuração específica do sistema, `app/etc/env.php`. Verifique o código Commerce e a configuração compartilhada no controle do código-fonte e envie-o para o servidor de compilação.

Você também deve instalar extensões e personalizar o código do Commerce no sistema de desenvolvimento.

Em seu sistema de desenvolvimento:

1. Defina a configuração no Admin.

1. Use o comando `magento app:config:dump` para gravar a configuração no sistema de arquivos.

   - `app/etc/config.php` é a configuração compartilhada, que contém todas as configurações _exceto_ as configurações específicas do sistema e as confidenciais. Este arquivo deve estar no controle do código-fonte.
   - `app/etc/env.php` é a configuração específica do sistema, que contém configurações exclusivas de um sistema específico (por exemplo, nomes de host e números de porta). Este arquivo deve _não_ estar no controle de origem.

1. Adicione o código modificado e a configuração compartilhada ao controle do código-fonte.

1. Para remover o código php gerado e os arquivos de ativos estáticos enquanto em desenvolvimento, execute os seguintes comandos:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Após executar os comandos para limpar os ativos, o Commerce gera arquivos de trabalho.

>[!WARNING]
>
>Tenha cuidado com a abordagem acima. Excluir o arquivo `.htacces`s na pasta `generated` ou `pub` pode causar problemas.

### Criar sistema

O sistema de compilação compila o código e gera arquivos de visualização estáticos para temas registrados no Commerce. Ela não precisa de uma conexão com o banco de dados do Commerce; ela precisa apenas da base de código do Commerce.

No sistema de compilação:

1. Extrair o arquivo de configuração compartilhado do controle do código-fonte.
1. Use o comando `magento setup:di:compile` para compilar o código.
1. Use o comando `magento setup:static-content:deploy -f` para atualizar arquivos de exibição de arquivo estáticos.
1. Verifique as atualizações no controle de origem.

>[!INFO]
>
>Consulte [Estratégias de implantação para arquivos de exibição estáticos](../cli/static-view-file-strategy.md).

### Sistema de produção

No sistema de produção (ou seja, na loja em tempo real), você extrai ativos gerados e atualizações de código do controle de origem e define configurações confidenciais e específicas do sistema usando a linha de comando ou variáveis de ambiente.

Em seu sistema de produção:

1. Iniciar modo de manutenção.
1. Obter atualizações de código e configuração do controle do código-fonte.
1. Se você usar o Adobe Commerce, interrompa os trabalhadores em fila.
1. Use o comando `magento app:config:import` para importar alterações de configuração no sistema de produção.
1. Se você instalou componentes que alteraram o esquema do banco de dados, execute `magento setup:upgrade --keep-generated` para atualizar o esquema do banco de dados e os dados, preservando os arquivos estáticos gerados.
1. Para definir configurações específicas do sistema, use o comando `magento config:set` ou as variáveis de ambiente.
1. Para definir configurações confidenciais, use o comando `magento config:sensitive:set` ou as variáveis de ambiente.
1. Limpar (também conhecido como _liberar_) o cache.
1. Encerrar modo de manutenção.

## Comandos de gerenciamento de configuração

Fornecemos os seguintes comandos para ajudá-lo a gerenciar a configuração:

- [`magento app:config:dump`](../cli/export-configuration.md) para gravar as definições de configuração do Administrador em `config.php` e `env.php` (exceto para definições confidenciais)
- [`magento config:set`](../cli/set-configuration-values.md) para definir os valores de configurações específicas do sistema no sistema de produção.

  Use a opção `--lock` opcional para bloquear a opção no Administrador (ou seja, tornar a configuração não editável). Se uma configuração já estiver bloqueada, use a opção `--lock` para alterá-la.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) para definir os valores de configurações confidenciais no sistema de produção.
- [`magento app:config:import`](../cli/import-configuration.md) para importar alterações de configuração de `config.php` e `env.php` para o sistema de produção.

## Exemplos de gerenciamento de configuração

Esta seção mostra exemplos de gerenciamento da configuração para que você possa ver como as alterações são feitas em `config.php` e `env.php`.

### Alterar o local padrão

Esta seção mostra a alteração feita em `config.php` quando você altera a unidade de peso padrão usando Admin (**Lojas** > Configurações > **Configuração** > Geral > **Geral** > **Opções de Localidade**).

Depois de fazer a alteração no Administrador, execute `bin/magento app:config:dump` para gravar o valor em `config.php`. O valor é gravado na matriz `general` em `locale` como mostra o seguinte trecho de `config.php`:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Alterar várias definições de configuração

Esta seção discute as seguintes alterações de configuração:

- Adicionando um modo de exibição de site, loja e loja (**Lojas** > Configurações > **Todas as Lojas**)
- Alterando o domínio de email padrão (**Lojas** > Configurações > **Configuração** > Clientes > **Configuração do Cliente**)
- Definindo o Nome de Usuário da API do PayPal e a senha da API (**Lojas** > Configurações > **Configuração** > Vendas > **Métodos de Pagamento** > **PayPal** > **Configurações do PayPal necessárias**)

Depois de fazer a alteração no Administrador, execute o `bin/magento app:config:dump` no sistema de desenvolvimento. Desta vez, nem todas as suas alterações são gravadas em `config.php`; na verdade, somente o site, armazenamento e exibição de armazenamento são gravados nesse arquivo, conforme mostrado nos seguintes trechos.

### config.php

`config.php` contém:

- Alterações na exibição do site, da loja e da loja.
- Configurações do mecanismo de pesquisa não específicas do sistema
- Configurações não confidenciais do PayPal
- Comentários que informam sobre configurações confidenciais que foram omitidas de `config.php`

Matriz `websites`:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

Matriz `groups`:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

Matriz `stores`:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

Matriz `payment`:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

A definição de configuração específica do sistema de domínio de email padrão é gravada em `app/etc/env.php`.

As configurações do PayPal não são gravadas em nenhum arquivo porque o comando `bin/magento app:config:dump` não grava configurações confidenciais. Você deve definir as configurações do PayPal no sistema de produção usando os seguintes comandos:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
