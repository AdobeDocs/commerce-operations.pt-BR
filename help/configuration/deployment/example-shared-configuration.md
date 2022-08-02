---
title: Exemplo usando uma configuração compartilhada
description: Veja um exemplo de como alterar as configurações em um sistema de desenvolvimento com um arquivo de configuração compartilhado.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Exemplo usando uma configuração compartilhada

Este exemplo mostra como alterar as seguintes configurações no sistema de desenvolvimento, atualizar o arquivo de configuração compartilhado, `config.php`, no sistema de build e implemente as mesmas configurações no sistema de produção:

- Fuso horário
- Unidade de peso

Essas configurações estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.

Você pode usar o mesmo procedimento para configurar qualquer configuração não sensível e não específica do sistema nas seguintes referências:

- [Referência de outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração da extensão do Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Antes de começar

Antes de começar, configure as permissões e a propriedade do sistema de arquivos, conforme descrito em [Pré-requisitos para sistemas de desenvolvimento, criação e produção](../deployment/prerequisites.md).

## Pressupostos

Este tópico fornece um exemplo de modificação da configuração do sistema de produção. Se desejar, é possível escolher opções de configuração diferentes.

Para os fins deste exemplo, assumimos o seguinte:

- Você usa o controle de origem Git
- O sistema de desenvolvimento está disponível em um repositório remoto do Git chamado `mconfig`
- Sua ramificação de trabalho do Git é chamada de `m2.2_deploy`

## Etapa 1: Defina a configuração no sistema de desenvolvimento

Para definir o fuso horário e as unidades de peso no sistema de desenvolvimento:

1. Faça logon em Admin.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. No painel direito, expanda **Opções de localidade**.

   A figura a seguir mostra um exemplo.

   ![Definir opções de local no sistema de desenvolvimento](../../assets/configuration/split-deploy-set-locale.png)

1. No **Fuso horário** listar, clique em **GMT+00:00 (UTC)**.
1. Limpe o **Usar valor do sistema** caixa de seleção ao lado da **Unidade de peso** campo.
1. No **Unidade de peso** listar, clique em **kgs**.
1. Clique em **Salvar configuração**.
1. Se solicitado, libere o cache.

## Etapa 2: Atualizar a configuração compartilhada

Gere o arquivo de configuração compartilhado, `app/etc/config.php`, no sistema de desenvolvimento e transfira-o usando o controle de origem para o sistema de build, conforme discutido nesta seção.

{{$include /help/_includes/config-save-config.md}}

## Etapa 3: Atualize seu sistema de build e gere arquivos

Depois de confirmar as alterações na configuração compartilhada com o controle de origem, você pode extrair essas alterações no sistema de compilação, compilar o código e gerar arquivos estáticos. A última etapa é transferir essas alterações para o sistema de produção. Como resultado, a configuração do seu sistema de produção corresponderá ao seu sistema de desenvolvimento.

{{$include /help/_includes/config-update-build-system.md}}

## Etapa 4: Atualizar o sistema de produção

A última etapa do processo é atualizar seu sistema de produção do controle de origem. Isso remove todas as alterações feitas em seus sistemas de desenvolvimento e criação, o que significa que o sistema de produção está totalmente atualizado.

{{$include /help/_includes/config-update-prod-system.md}}

### Verificar as alterações no Administrador

**Para verificar se essas configurações não são editáveis no Administrador**:

1. Faça logon em Admin.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. No painel direito, expanda **Opções de localidade**.

   As opções que você acabou de definir são exibidas da seguinte maneira:

   ![Opções de configuração não editáveis no Administrador](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Para alterar uma configuração bloqueada no Administrador, use a variável [`magento config:set --lock` comando](../cli/set-configuration-values.md).
