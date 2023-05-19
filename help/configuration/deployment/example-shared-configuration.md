---
title: Exemplo usando uma configuração compartilhada
description: Veja um exemplo de como alterar configurações em um sistema de desenvolvimento com um arquivo de configuração compartilhado.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Exemplo usando uma configuração compartilhada

Este exemplo mostra como alterar as seguintes configurações no sistema de desenvolvimento, atualizar o arquivo de configuração compartilhado, `config.php`, no sistema de compilação, e implemente as mesmas configurações no sistema de produção:

- Fuso horário
- Unidade de peso

Essas configurações estão disponíveis no Administrador do **Lojas** > Configurações > **Configuração** > Geral > **Geral**.

Você pode usar o mesmo procedimento para definir configurações não confidenciais e não específicas do sistema nas seguintes referências:

- [Referência a outros caminhos de configuração](../reference/config-reference-general.md)
- [Referência de caminhos de configuração de pagamento](../reference/config-reference-payment.md)
- [Referência de caminhos de configuração da extensão B2B do Commerce Enterprise](../reference/config-reference-b2b.md)

## Antes de começar

Antes de começar, configure as permissões e a propriedade do sistema de arquivos conforme discutido em [Pré-requisitos para sistemas de desenvolvimento, compilação e produção](../deployment/prerequisites.md).

## Suposições

Este tópico fornece um exemplo de modificação da configuração do sistema de produção. Se desejar, você poderá escolher diferentes opções de configuração.

Para os fins deste exemplo, pressupomos o seguinte:

- Você usa o controle de origem do Git
- O sistema de desenvolvimento está disponível em um repositório remoto Git chamado `mconfig`
- Sua ramificação de trabalho Git é chamada de `m2.2_deploy`

## Etapa 1: definir a configuração no sistema de desenvolvimento

Para definir o fuso horário e as unidades de peso no sistema de desenvolvimento:

1. Faça logon no Administrador.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. No painel direito, expanda **Opções de localidade**.

   A figura a seguir mostra um exemplo.

   ![Definir opções de localidade no sistema de desenvolvimento](../../assets/configuration/split-deploy-set-locale.png)

1. No **Fuso horário** clique em **GMT+00:00 (UTC)**.
1. Limpe a **Usar valor do sistema** ao lado da caixa de seleção **Unidade de Peso** campo.
1. No **Unidade de Peso** clique em **kgs**.
1. Clique em **Salvar configuração**.
1. Se solicitado, limpe o cache.

## Etapa 2: atualizar a configuração compartilhada

Gerar o arquivo de configuração compartilhado, `app/etc/config.php`, no sistema de desenvolvimento e transfira-o usando o controle do código-fonte para o sistema de build, conforme discutido nesta seção.

{{$include /help/_includes/config-save-config.md}}

## Etapa 3: atualizar o sistema de compilação e gerar arquivos

Agora que você confirmou as alterações na configuração compartilhada para o controle de origem, é possível obter essas alterações no sistema de compilação, compilar o código e gerar arquivos estáticos. A última etapa é transferir essas alterações para o sistema de produção. Como resultado, a configuração do seu sistema de produção corresponderá ao seu sistema de desenvolvimento.

{{$include /help/_includes/config-update-build-system.md}}

## Etapa 4: atualizar o sistema de produção

A última etapa do processo é atualizar o sistema de produção do controle do código-fonte. Isso extrai todas as alterações feitas em seus sistemas de desenvolvimento e compilação, o que significa que seu sistema de produção está completamente atualizado.

{{$include /help/_includes/config-update-prod-system.md}}

### Verifique as alterações no Admin

**Para verificar se essas configurações não são editáveis no Admin**:

1. Faça logon no Administrador.
1. Clique em **Lojas** > Configurações > **Configuração** > Geral > **Geral**.
1. No painel direito, expanda **Opções de localidade**.

   As opções que você acabou de definir são exibidas da seguinte maneira:

   ![Opções de configuração não editáveis no Admin](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Para alterar uma configuração que está bloqueada no Administrador, use o [`magento config:set --lock` comando](../cli/set-configuration-values.md).
