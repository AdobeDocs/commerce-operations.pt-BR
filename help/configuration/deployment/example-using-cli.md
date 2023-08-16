---
title: Exemplo usando comandos CLI
description: Veja um exemplo de como definir valores compartilhados, específicos do sistema e confidenciais no sistema de desenvolvimento usando a linha de comando.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Exemplo usando comandos CLI

Esse exemplo mostra como definir valores compartilhados, específicos do sistema e confidenciais no sistema de desenvolvimento e, em seguida, implantar esses valores no sistema de produção.
Isso é feito usando uma combinação de configurações compartilhadas, a variável `config.php` e o comando da CLI do Commerce.

Este exemplo usa as seguintes definições de configuração:

- **Número De Iva** e **Nome do armazenamento** para as definições de configuração compartilhadas.

  Eles são encontrados em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.

- **Enviar Emails Para** para o valor de configuração confidencial.

  Isso é encontrado em **Lojas** > Configurações > **Configuração** > Geral > **Contatos**.

- **Domínio de email padrão** para o valor de configuração específico do sistema.

  Isso é encontrado em **Lojas** > Configurações > **Configuração** > Clientes > **Configuração do cliente** > **Criar novas opções de conta**.

Você pode usar o mesmo procedimento mostrado neste exemplo para definir qualquer configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência a outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](../reference/config-reference-b2b.md)

## Antes de começar

Antes de começar, configure as permissões e a propriedade do sistema de arquivos conforme discutido em [Pré-requisito para sistemas de desenvolvimento, compilação e produção](../deployment/prerequisites.md).

## Suposições

Este tópico fornece um exemplo de modificação da configuração do sistema de produção. Se desejar, você poderá escolher diferentes opções de configuração.

Para os fins deste exemplo, pressupomos o seguinte:

- Você usa o controle de origem do Git
- O sistema de desenvolvimento está disponível em um repositório remoto Git chamado `mconfig`
- Sua ramificação de trabalho Git é chamada de `m2.2_deploy`

## Etapa 1: definir a configuração no sistema de desenvolvimento

Para definir o local padrão e as unidades de peso no sistema de desenvolvimento:

1. Faça logon no Administrador.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. Se você tiver mais de um site disponível, use o **Exibição da loja** no canto superior esquerdo para alternar para um site diferente, como mostra a figura a seguir.

   ![Alternar sites](../../assets/configuration/split-deploy-switch-website.png)

1. No painel direito, expanda **Armazenar informações**.
1. Se necessário, limpe a **Usar padrão** ao lado da caixa de seleção **Número IVA** e **Nome do armazenamento** campos.
1. Insira um número no campo (por exemplo, `12345`).
1. No **Nome do armazenamento** insira um valor (como `My Store`).
1. Clique em **Salvar configuração**.
1. Na navegação à esquerda, em Geral, clique em **Contatos**.
1. No painel direito, expanda **Opções de email**.
1. Se necessário, limpe a **Usar padrão** ao lado da caixa de seleção **Enviar Emails Para** campo.
1. Insira um endereço de email no campo.
1. Clique em **Salvar configuração**.
1. Use o **Exibição da loja** para selecionar o **Configuração padrão** como mostra a figura a seguir.

   ![Alternar para a configuração padrão](../../assets/configuration/split-deploy-default-config.png)

1. No painel esquerdo, clique em Clientes > **Configuração do cliente**.
1. No painel direito, expanda **Criar novas opções de conta**.
1. Se necessário, limpe a **Usar valor do sistema** ao lado da caixa de seleção **Domínio de email padrão** campo.
1. Insira um nome de domínio no campo.
1. Clique em **Salvar configuração**.
1. Se solicitado, limpe o cache.

## Etapa 2: atualizar a configuração

Agora que você alterou a configuração no Admin, grave a configuração compartilhada em um arquivo usando as seguintes etapas:

{{$include /help/_includes/config-save-config.md}}

Mesmo que `app/etc/env.php` (a configuração específica do sistema) foi atualizada, não faça check-in dela no controle de origem.
Você criará as mesmas configurações no sistema de produção posteriormente neste procedimento.

## Etapa 3: atualizar o sistema de compilação e gerar arquivos

Agora que você confirmou as alterações na configuração compartilhada para o controle de origem, é possível puxar essas alterações no sistema de compilação, compilar o código e gerar arquivos estáticos.

{{$include /help/_includes/config-update-build-system.md}}

## Etapa 4: atualizar o sistema de produção

A última etapa do processo é atualizar o sistema de produção. Você deve fazer isso em duas partes:

- Atualizar as configurações confidenciais e específicas do sistema
- Atualizar as configurações compartilhadas

### Atualizar as configurações confidenciais e específicas do sistema

Para definir as configurações confidenciais e específicas do sistema usando variáveis de ambiente, você deve saber o seguinte:

- Escopo para cada configuração

  Se você seguiu as instruções da Etapa 1, o escopo para **Enviar Emails Para** é o site e o escopo para **Domínio de email padrão** é global (ou seja, o escopo de Configuração padrão).

  É necessário o código do site para definir a variável **Enviar Emails Para** valor de configuração.

  Para obter mais informações sobre como descobrir esse valor, consulte: [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables).

- Caminhos de configuração para as configurações usadas neste exemplo:

  | Nome da configuração | Caminho de configuração |
  | -------------------- | -------------------------------------- |
  | Enviar Emails Para | `contact/email/recipient_email` |
  | Domínio de email padrão | `customer/create_account/email_domain` |

  Para todos os caminhos de configuração confidenciais e específicos do sistema, consulte: [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md).

### Defina as variáveis usando comandos CLI

Use os seguintes comandos da CLI para definir configurações específicas e confidenciais do sistema:

- `magento config:set` para configurações específicas do sistema
- `magento config:sensitive:set` para configurações confidenciais

Para definir as configurações específicas do sistema **Domínio de email padrão**, que está no escopo padrão, use o seguinte comando:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Você não precisa usar o escopo no comando porque ele é o escopo padrão.

Para definir valores para **Enviar Emails Para** No entanto, você deve saber o tipo de escopo (`website`) e o código do escopo, que provavelmente é diferente em cada site.

Exemplo:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Atualizar as configurações compartilhadas

Esta seção discute como transferir todas as alterações feitas nos sistemas de desenvolvimento e criação para um ambiente de produção, que atualiza as configurações compartilhadas (nome da loja e número IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifique as configurações no Administrador

Para verificar as definições de configuração:

1. Faça logon no Administrador do sistema de produção.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. Use o **Exibição da loja** no canto superior esquerdo para alternar para um site diferente.

   As opções de configuração compartilhada definidas no sistema de desenvolvimento são exibidas de forma semelhante a seguir.

   ![Verificar configurações no sistema de produção](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >A variável **Nome do armazenamento** O campo é editável no escopo do site, mas se você alternar para o escopo Configuração padrão, ele não será editável. Esse é o resultado de como você define as opções no sistema de desenvolvimento. O valor de **Número IVA** não é editável no escopo do site.

1. Se ainda não tiver feito isso, alterne para o Escopo de configuração padrão.
1. Na navegação à esquerda, em Geral, clique em **Contatos**.

   A variável **Enviar Emails Para** não é editável, como mostra a figura a seguir. Essa é uma configuração delicada.

   ![Verificar configurações no sistema de produção](../../assets/configuration/split-deploy-verify-contacts.png)

1. No painel esquerdo, clique em Clientes > **Configuração do cliente**.
1. No painel direito, expanda **Criar novas opções de conta**.

   O valor de **Domínio de email padrão** é exibido da seguinte maneira: Esta é uma configuração específica do sistema.

   ![Verificar configurações no sistema de produção](../../assets/configuration/split-default-domain.png)
