---
title: Exemplo usando comandos CLI
description: Veja um exemplo de como definir valores compartilhados, específicos do sistema e confidenciais em seu sistema de desenvolvimento usando a linha de comando.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# Exemplo usando comandos CLI

Este exemplo mostra como definir valores compartilhados, específicos do sistema e confidenciais no sistema de desenvolvimento e, em seguida, implantar esses valores no sistema de produção.
Isso é feito usando uma combinação de configurações compartilhadas, o `config.php` e comando Commerce CLI.

Esse exemplo usa as seguintes configurações:

- **Número Vat** e **Nome da loja** para as configurações compartilhadas.

   Estes são encontrados em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.

- **Enviar Emails para** para o valor de configuração sensível.

   Isso é encontrado em **Lojas** > Configurações > **Configuração** > Geral > **Contatos**.

- **Domínio de email padrão** para o valor de configuração específico do sistema.

   Isso é encontrado em **Lojas** > Configurações > **Configuração** > Clientes > **Configuração do cliente** > **Criar novas opções de conta**.

Você pode usar o mesmo procedimento mostrado neste exemplo para configurar qualquer configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração da extensão do Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Antes de começar

Antes de começar, configure as permissões e a propriedade do sistema de arquivos, conforme descrito em [Pré-requisito para os sistemas de desenvolvimento, criação e produção](../deployment/prerequisites.md).

## Pressupostos

Este tópico fornece um exemplo de modificação da configuração do sistema de produção. Se desejar, é possível escolher opções de configuração diferentes.

Para os fins deste exemplo, assumimos o seguinte:

- Você usa o controle de origem Git
- O sistema de desenvolvimento está disponível em um repositório remoto do Git chamado `mconfig`
- Sua ramificação de trabalho do Git é chamada de `m2.2_deploy`

## Etapa 1: Defina a configuração no sistema de desenvolvimento

Para definir a localidade e as unidades de peso padrão em seu sistema de desenvolvimento:

1. Faça logon em Admin.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. Se você tiver mais de um site disponível, use a variável **Exibição da loja** no canto superior esquerdo para alternar para um site diferente, como mostra a figura a seguir.

   ![Alternar sites](../../assets/configuration/split-deploy-switch-website.png)

1. No painel direito, expanda **Informações da loja**.
1. Se necessário, limpe o **Usar padrão** caixa de seleção ao lado da **Número do IVA** e **Nome da loja** campos.
1. Insira um número no campo (por exemplo, `12345`).
1. No **Nome da loja** insira um valor (como `My Store`).
1. Clique em **Salvar configuração**.
1. Na navegação à esquerda, em Geral, clique em **Contatos**.
1. No painel direito, expanda **Opções de email**.
1. Se necessário, limpe o **Usar padrão** caixa de seleção ao lado da **Enviar Emails para** campo.
1. Insira um endereço de email no campo .
1. Clique em **Salvar configuração**.
1. Use o **Exibição da loja** para selecionar a **Configuração padrão** como mostra a figura a seguir.

   ![Alternar para a configuração padrão](../../assets/configuration/split-deploy-default-config.png)

1. No painel esquerdo, clique em Clientes > **Configuração do cliente**.
1. No painel direito, expanda **Criar novas opções de conta**.
1. Se necessário, limpe o **Usar valor do sistema** caixa de seleção ao lado da **Domínio de email padrão** campo.
1. Insira um nome de domínio no campo .
1. Clique em **Salvar configuração**.
1. Se solicitado, libere o cache.

## Etapa 2: Atualizar a configuração

Agora que você alterou a configuração no Administrador, grave a configuração compartilhada em um arquivo usando as seguintes etapas:

{{$include /help/_includes/config-save-config.md}}

Apesar de `app/etc/env.php` (a configuração específica do sistema) foi atualizada, não faça o check-in no controle do código-fonte.
Posteriormente, você criará as mesmas configurações em seu sistema de produção, neste procedimento.

## Etapa 3: Atualize seu sistema de build e gere arquivos

Depois de confirmar as alterações na configuração compartilhada com o controle de origem, você pode inserir essas alterações no sistema de criação, compilar o código e gerar arquivos estáticos.

{{$include /help/_includes/config-update-build-system.md}}

## Etapa 4: Atualizar o sistema de produção

A última etapa do processo é atualizar seu sistema de produção. Você deve fazer isso em duas partes:

- Atualizar as configurações sensíveis e específicas do sistema
- Atualizar as configurações compartilhadas

### Atualizar as configurações sensíveis e específicas do sistema

Para definir as configurações confidenciais e específicas do sistema usando variáveis de ambiente, você deve saber o seguinte:

- Escopo para cada configuração

   Se você seguiu as instruções na Etapa 1, o escopo de **Enviar Emails para** é o site e o escopo de **Domínio de email padrão** é global (ou seja, o escopo da configuração padrão).

   Você precisa do código do site para definir a variável **Enviar Emails para** valor de configuração.

   Para obter mais informações sobre como descobrir esse valor, consulte: [Usar variáveis de ambiente para substituir configurações](../reference/override-config-settings.md#environment-variables).

- Caminhos de configuração para as configurações usadas neste exemplo:

   | Nome da configuração | Caminho de configuração |
   | -------------------- | -------------------------------------- |
   | Enviar Emails para | `contact/email/recipient_email` |
   | Domínio de email padrão | `customer/create_account/email_domain` |

   Para todos os caminhos de configuração confidenciais e específicos do sistema, consulte: [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md).

### Defina as variáveis usando comandos CLI

Use os seguintes comandos da CLI para definir configurações confidenciais e específicas do sistema:

- `magento config:set` para configurações específicas do sistema
- `magento config:sensitive:set` para configurações sensíveis

Para definir a configuração específica do sistema **Domínio de email padrão**, que está no escopo padrão, use o seguinte comando:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Não é necessário usar o escopo no comando porque ele é o escopo padrão.

Para definir valores para **Enviar Emails para**, no entanto, você deve saber o tipo de escopo (`website`) e o código do escopo, que provavelmente é diferente em cada site.

Exemplo:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Atualizar as configurações compartilhadas

Esta seção discute como transferir todas as alterações feitas em seu desenvolvimento e criar sistemas para um ambiente de produção, que atualiza as configurações compartilhadas (Nome da loja e Número de IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifique as configurações no Administrador

Para verificar as configurações:

1. Faça logon no Administrador do sistema de produção.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. Use o **Exibição da loja** no canto superior esquerdo para alternar para um site diferente.

   As opções de configuração compartilhadas definidas no sistema de desenvolvimento são exibidas de forma semelhante ao seguinte.

   ![Verifique as configurações no sistema de produção](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >O **Nome da loja** O campo é editável no escopo do site, mas se você alternar para o escopo de configuração padrão, ele não será editável. Esse é o resultado de como você define as opções no sistema de desenvolvimento. O valor de **Número do IVA** não é editável no escopo do site.

1. Se ainda não tiver feito isso, alterne para o escopo de configuração padrão.
1. Na navegação à esquerda, em Geral, clique em **Contatos**.

   O **Enviar Emails para** não é editável, como mostra a figura a seguir. Esta é uma configuração sensível.

   ![Verifique as configurações no sistema de produção](../../assets/configuration/split-deploy-verify-contacts.png)

1. No painel esquerdo, clique em Clientes > **Configuração do cliente**.
1. No painel direito, expanda **Criar novas opções de conta**.

   O valor da variável **Domínio de email padrão** é exibido da seguinte maneira. Esta é uma configuração específica do sistema.

   ![Verifique as configurações no sistema de produção](../../assets/configuration/split-default-domain.png)
