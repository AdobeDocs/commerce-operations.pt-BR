---
title: Detalhes técnicos
description: Leia sobre os detalhes técnicos da implantação de pipeline, tipos de configurações e fluxos de trabalho recomendados.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# Detalhes técnicos

Este tópico discute os detalhes de implementação técnica sobre a implantação de pipeline no Commerce 2.2 e posterior. As melhorias podem ser divididas nas seguintes áreas:

- [Gerenciamento de configurações](#configuration-management)
- [Mudanças no Administrador](#changes-in-the-admin)
- [Instalar e remover o cron](#install-and-remove-cron)

Este tópico também discute o [fluxo de trabalho recomendado](#recommended-workflow) para implantação de pipeline e fornece alguns exemplos para ajudar você a entender como ele funciona.

Antes de começar, reveja o [Pré-requisitos para os sistemas de desenvolvimento, criação e produção](../deployment/prerequisites.md).

## Gerenciamento de configurações

Para permitir que você sincronize e mantenha a configuração de seus sistemas de desenvolvimento e produção, use o seguinte esquema de substituição.

![Como os valores da variável de configuração são determinados](../../assets/configuration/override-flow-diagram.png)

Como mostra o diagrama, os valores de configuração são usados na seguinte ordem:

1. As variáveis de ambiente, se existirem, substituem todos os outros valores.
1. Nos arquivos de configuração compartilhados `env.php` e `config.php`. Valores em `env.php` substituir valores em `config.php`.
1. A partir de valores armazenados no banco de dados.
1. Se não houver valor em nenhuma dessas fontes, o valor padrão ou NULL será usado.

### Gerenciar a configuração compartilhada

A configuração compartilhada é armazenada em `app/etc/config.php`, que deve estar no controle de origem.

Defina a configuração compartilhada no Administrador em seu desenvolvimento (ou no Adobe Commerce na infraestrutura em nuvem) _integração_) e gravar a configuração em `config.php` usando o [`magento app:config:dump` comando](../cli/export-configuration.md).

### Gerenciar a configuração específica do sistema

A configuração específica do sistema é armazenada em `app/etc/env.php`, que _not_ estar no controle de origem.

Defina a configuração específica do sistema no Administrador do sistema de desenvolvimento (ou Adobe Commerce na integração da infraestrutura em nuvem) e grave a configuração em `env.php` usando o [`magento app:config:dump` comando](../cli/export-configuration.md).

Este comando também grava configurações confidenciais em `env.php`.

### Gerenciar a configuração sensível

A configuração sensível também é armazenada em `app/etc/env.php`.

Você pode gerenciar a configuração sensível de qualquer uma das seguintes maneiras:

- Variáveis de ambiente
- Salve a configuração sensível em `env.php` no sistema de produção usando o [`magento config:set:sensitive` comando](../cli/set-configuration-values.md)

### Configurações bloqueadas no Administrador

Qualquer configuração em `config.php` ou `env.php` estiverem bloqueadas no Administrador; ou seja, essas configurações não podem ser alteradas no Admin.
Use o [`magento config:set` ou `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) para alterar as configurações no `config.php` ou `env.php` arquivos.

## Administrador de comércio

O Administrador exibe o seguinte comportamento no modo de produção:

- Não é possível ativar ou desativar tipos de cache no Administrador
- As configurações do desenvolvedor não estão disponíveis (**Lojas** > Configurações > **Configuração** > Avançado > **Desenvolvedor**), incluindo:

   - Minimizar CSS, JavaScript e HTML
   - Mesclar CSS e JavaScript
   - Compilação LESS do lado do servidor ou do lado do cliente
   - Traduções em linha
   - Conforme discutido anteriormente, qualquer configuração em `config.php` ou `env.php` está bloqueado e não pode ser editado no Admin.
   - Você pode alterar o local do Administrador somente para idiomas usados por temas implantados

      A figura a seguir mostra um exemplo da variável **Configuração da conta** > **Localidade da interface** lista no Administrador mostrando apenas duas localidades implantadas:

      ![Você pode alterar o local do Administrador somente para as localidades implantadas](../../assets/configuration/split-deploy-admin-locale.png)

- Não é possível alterar as configurações de local de nenhum escopo usando o Administrador.

   Recomendamos fazer essas alterações antes de alternar para o modo Produção.

   Você ainda pode configurar o local usando variáveis de ambiente ou a variável `config:set` comando CLI com o caminho `general/locale/code`.

## Instalar e remover o cron

Na versão 2.2 pela primeira vez, ajudamos você a configurar seu trabalho do cron fornecendo o [`magento cron:install` comando](../cli/configure-cron-jobs.md). Esse comando configura um crontab como o usuário que executa o comando.

Além disso, é possível remover o crontab usando o `magento cron:remove` comando.

## Fluxo de trabalho de implantação de pipeline recomendado

O diagrama a seguir mostra como recomendamos usar a implantação de pipeline para gerenciar a configuração.

![Fluxo de trabalho de implantação de pipeline recomendado](../../assets/configuration/split-deploy-workflow.png)

### Sistema de desenvolvimento

Em seu sistema de desenvolvimento, você faz alterações na configuração no Administrador e gera a configuração compartilhada, `app/etc/config.php` e a configuração específica do sistema, `app/etc/env.php`. Verifique o código do Commerce e a configuração compartilhada no controle de origem e envie-o para o servidor de compilação.

Você também deve instalar extensões e personalizar o código do Commerce no sistema de desenvolvimento.

Em seu sistema de desenvolvimento:

1. Defina a configuração em Admin.

1. Use o `magento app:config:dump` para gravar a configuração no sistema de arquivos.

   - `app/etc/config.php` é a configuração compartilhada, que contém todas as configurações _Except_ configurações confidenciais e específicas do sistema. Esse arquivo deve estar no controle de origem.
   - `app/etc/env.php` é a configuração específica do sistema, que contém configurações exclusivas para um sistema específico (por exemplo, nomes de host e números de porta). Esse arquivo deve _not_ estar no controle de origem.

1. Adicione o código modificado e a configuração compartilhada ao controle de origem.

1. Para remover o código php gerado e os arquivos de ativos estáticos durante o desenvolvimento, execute os seguintes comandos:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Depois de executar os comandos para limpar os ativos, o Commerce gera arquivos de trabalho.

>[!WARNING]
>
>Tenha cuidado com a abordagem acima. Excluir o `.htacces`Arquivo s no `generated` ou `pub` pode causar problemas na pasta.

### Criar sistema

O sistema de compilação compila o código e gera arquivos de exibição estáticos para temas registrados no Commerce. Não necessita de uma ligação à base de dados Comércio; ele precisa apenas da base de código do Commerce.

No sistema de build:

1. Puxe o arquivo de configuração compartilhado do controle de origem.
1. Use o `magento setup:di:compile` para compilar o código.
1. Use o `magento setup:static-content:deploy -f` para atualizar arquivos estáticos de visualização de arquivo.
1. Verifique as atualizações no controle de origem.

>[!INFO]
>
>Consulte [Estratégias de implantação para arquivos de visualização estática](../cli/static-view-file-strategy.md).

### Sistema de produção

Em seu sistema de produção (ou seja, em sua loja ativa), você obtém ativos gerados e atualizações de código do controle de origem e define configurações específicas e confidenciais do sistema usando a linha de comando ou as variáveis de ambiente.

No sistema de produção:

1. Inicie o modo de manutenção.
1. Obter atualizações de código e configuração do controle de origem.
1. Se você usar o Adobe Commerce, pare os trabalhadores da fila.
1. Use o `magento app:config:import` para importar alterações de configuração no sistema de produção.
1. Se você instalou componentes que alteraram o schema do banco de dados, execute `magento setup:upgrade --keep-generated` para atualizar o esquema e os dados do banco de dados, preservando os arquivos estáticos gerados.
1. Para definir configurações específicas do sistema, use `magento config:set` variáveis de comando ou ambiente.
1. Para definir configurações confidenciais, use `magento config:sensitive:set` variáveis de comando ou ambiente.
1. Limpo (também conhecido como _liberação_) o cache.
1. Encerre o modo de manutenção.

## Comandos do gerenciamento de configurações

Fornecemos os seguintes comandos para ajudá-lo a gerenciar a configuração:

- [`magento app:config:dump`](../cli/export-configuration.md) para gravar as configurações do administrador no `config.php` e `env.php` (exceto para configurações confidenciais)
- [`magento config:set`](../cli/set-configuration-values.md) para definir os valores de configurações específicas do sistema no sistema de produção.

   Use o `--lock` para bloquear a opção no Administrador (ou seja, tornar a configuração ineditável). Se uma configuração já estiver bloqueada, use a `--lock` para alterar a configuração.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) para definir os valores de configurações confidenciais no sistema de produção.
- [`magento app:config:import`](../cli/import-configuration.md) para importar alterações de configuração de `config.php` e `env.php` ao sistema de produção.

## Exemplos de gerenciamento de configuração

Esta seção mostra exemplos de gerenciamento da configuração para que você possa ver como as alterações são feitas no `config.php` e `env.php`.

### Alterar a localidade padrão

Esta seção mostra a alteração feita em `config.php` ao alterar a unidade de peso padrão usando o Administrador (**Lojas** > Configurações > **Configuração** > Geral > **Geral** > **Opções de localidade**).

Depois de fazer a alteração no Administrador, execute `bin/magento app:config:dump` para gravar o valor em `config.php`. O valor é gravado na variável `general` array em `locale` como o seguinte trecho de `config.php` mostra:

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

### Alterar várias configurações

Esta seção discute fazer as seguintes alterações de configuração:

- Adicionar um site, loja e exibição de loja (**Lojas** > Configurações > **Todas as lojas**)
- Alterar o domínio de email padrão (**Lojas** > Configurações > **Configuração** > Clientes > **Configuração do cliente**)
- Configuração do nome de usuário e senha da API do PayPal (**Lojas** > Configurações > **Configuração** > Vendas > **Métodos de pagamento** > **PayPal** > **Configurações necessárias do PayPal**)

Depois de fazer a alteração no Administrador, execute `bin/magento app:config:dump` no seu sistema de desenvolvimento. Desta vez, nem todas as suas alterações são gravadas em `config.php`; na verdade, somente o site, a loja e a exibição de loja são gravados nesse arquivo como os seguintes trechos mostram.

### config.php

`config.php` contém:

- Alterações no site, armazenamento e visualização de armazenamento.
- Configurações de mecanismo de pesquisa não específicas do sistema
- Configurações PayPal não sensíveis
- Comentários que informam sobre configurações confidenciais que foram omitidas de `config.php`

`websites` array:

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

`groups` array:

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

`stores` array:

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

`payment` array:

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

A configuração padrão específica do sistema do domínio de email é gravada em `app/etc/env.php`.

As configurações de PayPal não são gravadas em nenhum arquivo porque a variável `bin/magento app:config:dump` O comando não grava configurações confidenciais. Você deve definir as configurações do PayPal no sistema de produção usando os seguintes comandos:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
