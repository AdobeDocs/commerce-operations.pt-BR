---
title: Exemplo usando variáveis de ambiente
description: Veja um exemplo de como definir valores compartilhados, específicos do sistema e confidenciais no sistema de desenvolvimento usando variáveis de ambiente.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---

# Exemplo usando variáveis de ambiente

Esse exemplo mostra como definir valores compartilhados, específicos do sistema e confidenciais no sistema de desenvolvimento e, em seguida, definir todos os valores no sistema de produção usando uma combinação da configuração compartilhada, `config.php`, e variáveis de ambiente PHP.

Essas configurações podem ser compartilhadas entre os sistemas de desenvolvimento e produção:

Número IVA e Nome da Loja de **Lojas** > Configurações > **Configuração** > Geral > **Geral**

Essas configurações são específicas do sistema ou confidenciais, conforme indicado:

- Enviar Emails para (confidencial) de **Lojas** > Configurações > **Configuração** > Geral > **Contatos**
- Domínio de email padrão (específico do sistema) de **Lojas** > Configurações > **Configuração** > Clientes > **Configuração do cliente** > **Criar novas opções de conta**

Você pode usar o mesmo procedimento para definir qualquer configuração nas seguintes referências:

- [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração geral](../reference/config-reference-general.md)
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
1. Se necessário, limpe a **Usar padrão** ao lado da caixa de seleção **Número IVA** campo.
1. Insira um número no campo (por exemplo, `12345`).
1. No **Nome do armazenamento** insira um valor (como `My Store`).
1. Clique em **Salvar configuração**.
1. Use o **Exibição da loja** para selecionar o **Configuração padrão** como mostra a figura a seguir.

   ![Alternar para a configuração padrão](../../assets/configuration/split-deploy-default-config.png)

1. Na navegação à esquerda, em Geral, clique em **Contatos**.
1. Limpe a **Usar padrão** ao lado da caixa de seleção **Enviar Emails Para** campo.
1. Insira um endereço de email no campo.
1. Clique em **Salvar configuração**.
1. No painel esquerdo, clique em Clientes > **Configuração do cliente**.
1. No painel direito, expanda **Criar novas opções de conta**.
1. Limpe a **Usar valor do sistema** ao lado da caixa de seleção **Domínio de email padrão** campo.
1. Insira um nome de domínio no campo.
1. Clique em **Salvar configuração**.
1. Se solicitado, limpe o cache.

## Etapa 2: atualizar a configuração

Agora que você alterou a configuração no Admin, grave a configuração compartilhada em um arquivo, conforme discutido nesta seção.

{{$include /help/_includes/config-save-config.md}}

Observe que, mesmo que `app/etc/env.php` (a configuração específica do sistema) foi atualizada, não faça check-in dela no controle de origem. Você criará as mesmas configurações no sistema de produção posteriormente neste procedimento.

## Etapa 3: atualizar o sistema de compilação e gerar arquivos

Agora que você confirmou as alterações na configuração compartilhada para o controle de origem, é possível obter essas alterações no sistema de compilação, compilar o código e gerar arquivos estáticos. A última etapa é transferir essas alterações para o sistema de produção.

{{$include /help/_includes/config-update-build-system.md}}

## Etapa 4: atualizar o sistema de produção

A última etapa do processo é atualizar o sistema de produção. Você deve fazer isso em duas partes:

- Atualizar as configurações confidenciais e específicas do sistema
- Atualizar as configurações compartilhadas

### Atualizar as configurações confidenciais e específicas do sistema

Para definir as configurações confidenciais e específicas do sistema usando variáveis de ambiente, você deve saber o seguinte:

- Escopo para cada configuração

  Se você seguiu as instruções na Etapa 1, o escopo para Enviar emails para é global (ou seja, o escopo Configuração padrão) e o escopo para Domínio de email padrão é site.

  Você deve saber o código do site para definir o valor de configuração do Domínio de email padrão. Consulte [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables) para obter mais informações sobre como encontrá-lo.

- Caminho de configuração para cada configuração

  Os caminhos de configuração usados neste exemplo seguem:

  | Nome da configuração | Caminho de configuração |
  |--------------|--------------|
  | Enviar Emails Para | `contact/email/recipient_email` |
  | Domínio de email padrão | `customer/create_account/email_domain` |

  Você pode encontrar todos os caminhos de configuração confidenciais e específicos do sistema em [Referência de caminhos de configuração sensíveis e específicos do sistema](../reference/config-reference-sens.md).

#### Converter caminhos de configuração em nomes de variáveis

Conforme discutido em [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables), o formato das variáveis é:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

O valor de `<SCOPE>` é `CONFIG__DEFAULT__` para escopo global ou `CONFIG__WEBSITES__<WEBSITE CODE>` para escopo de site.

Para encontrar o valor de `<SYSTEM__VARIABLE__NAME>`, substitua cada `/` caractere no caminho de configuração com dois sublinhados.

Os nomes das variáveis são os seguintes:

| Nome | Caminho de configuração | Nome da variável |
|--------------|--------------|--------------|
| Enviar Emails Para | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Domínio de email padrão | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>A tabela anterior tem um código de site de exemplo, `BASE`, para a definição de configuração Domínio de email padrão. Substituir `BASE` com o código de site apropriado para sua loja.

#### Definir as variáveis usando variáveis de ambiente

É possível definir os valores da variável nas `index.php` usando o seguinte formato:

```php
$_ENV['VARIABLE'] = 'value';
```

**Para definir valores de variáveis**:

1. Faça logon no sistema de produção como proprietário do sistema de arquivos ou alterne para ele.
1. Abertura `<Commerce root dir>/pub/index.php` em um editor de texto.
1. Em qualquer lugar no `index.php`, defina valores para as variáveis semelhantes ao seguinte:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Salvar as alterações em `pub/index.php` e saia do editor de texto.
1. Prossiga para a próxima seção.

### Atualizar as configurações compartilhadas

Esta seção discute como obter todas as alterações feitas nos sistemas de desenvolvimento e criação, que atualizam as configurações compartilhadas (nome da loja e número IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifique as configurações no Administrador

Esta seção discute como você pode verificar as configurações no Administrador do sistema de produção.

**Para verificar as definições de configuração**:

1. Faça logon no Administrador do sistema de produção.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. Use o **Exibição da loja** no canto superior esquerdo para alternar para um site diferente.

   As opções de configuração compartilhada definidas no sistema de desenvolvimento são exibidas de forma semelhante às seguintes.

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
