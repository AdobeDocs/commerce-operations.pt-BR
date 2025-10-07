---
title: Referência de caminhos de configuração de serviços
description: Saiba mais sobre os caminhos e valores de configuração de serviços nas configurações de administração do Adobe Commerce. Descubra API da Web, OAuth e opções de configuração de integração de serviço.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Referência de caminhos de configuração de serviços

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Serviços**.

O comando [`magento app:config:dump` &#x200B;](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir definições de configuração](override-config-settings.md#environment-variables). Este tópico _não_ lista [valores confidenciais e específicos do sistema](config-reference-sens.md).

## Caminhos da API da Web do Commerce

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Serviços** > **API da Web**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Conjunto de caracteres de resposta padrão | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir acesso de convidado anônimo | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos OAuth

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Serviços** > **OAuth**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Duração do token do cliente (horas) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração do token do administrador (horas) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilidade de Limpeza | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maxredirects de HTTP de credenciais do consumidor OAuth | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite de postagem HTTP de credenciais do consumidor OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
