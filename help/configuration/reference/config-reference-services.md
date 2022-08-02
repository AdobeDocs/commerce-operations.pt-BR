---
title: Referência de caminhos de configuração de serviços
description: Consulte uma lista de valores de configuração de serviços.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Referência de caminhos de configuração de serviços

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Serviços**.

O [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Como opção, para substituir qualquer configuração ou definir configurações confidenciais, consulte [Usar variáveis de ambiente para substituir configurações](override-config-settings.md#environment-variables). Este tópico faz _not_ lista [valores sensíveis e específicos do sistema](config-reference-sens.md).

## Caminhos de API da Web de comércio

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Serviços** > **API da Web**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Caractere de Resposta Padrão | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Acesso Anônimo de Convidado | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos OAuth

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Serviços** > **OAuth**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Duração do token do cliente (horas) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração do token de administrador (horas) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilidade de Limpeza | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credenciais do consumidor OAuth HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite da publicação HTTP das credenciais do consumidor do OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
