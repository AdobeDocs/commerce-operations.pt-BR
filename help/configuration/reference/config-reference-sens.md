---
title: Caminhos sensíveis e específicos do sistema
description: Consulte uma lista de valores de configuração confidenciais e específicos do sistema.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 5a8e52d8eee1619697db40accb9775b92b4e8a9d
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---

# Configurações sensíveis e específicas do sistema

Este tópico lista os caminhos de configuração para configurações confidenciais e específicas do sistema:

- A variável [`magento app:config:dump` comando](../cli/export-configuration.md) grava configurações específicas do sistema no arquivo de configuração específico do sistema, `app/etc/env.php`, que deve _não_ estar no controle de origem. Também grava a configuração compartilhada de todas as instâncias do Commerce para `app/etc/config.php`, este arquivo _deve_ estar no controle de origem.
- A variável [`magento config:sensitive:set` comando](../cli/set-configuration-values.md) grava configurações confidenciais em `app/etc/env.php`.

  Você também pode definir valores confidenciais usando variáveis de configuração, conforme discutido em [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables).

Para obter uma lista de outros caminhos de configuração, consulte:

- [Todos os caminhos de configuração exceto pagamentos](../reference/config-reference-general.md)
- [Caminhos de configuração de pagamento](../reference/config-reference-payment.md).

>[!INFO]
>
>Todos os caminhos de configuração listados neste tópico são confidenciais. A variável `System-specific?` mostra quais valores também são específicos do sistema.

## Caminhos gerais sensíveis à categoria e específicos do sistema

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Geral**.

### Caminhos da Web sensíveis e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Web**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL base | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL base do link | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL base para arquivos de visualização estáticos | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL base dos arquivos de mídia do usuário | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de base segura | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL do Link de base seguro | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de base segura para arquivos de visualização estática | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de base segura para arquivos de mídia do usuário | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL padrão da Web | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL padrão sem rota | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Caminho do cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Domínio do cookie | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Duração do cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Usar somente HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de restrição de cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Caminhos sensíveis à configuração de moeda e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Configuração de moeda**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Armazenar caminhos sensíveis ao endereço de email e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração de email** > **Geral** > **Armazenar endereços de email**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do remetente | `trans_email/ident_general/name` | | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| E-mail do remetente | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| E-mail do remetente | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| E-mail do remetente | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| E-mail do remetente | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| E-mail do remetente | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis ao contato e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Contatos**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar Emails Para | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Remetente do email | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modelo de e-mail | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Relatórios do New Relic sobre caminhos sigilosos e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Relatórios do New Relic**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID da conta do New Relic | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do aplicativo New Relic | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API do New Relic | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API do Insights | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL da API New Relic | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL da API do Insights | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Caminhos específicos do sistema e sensíveis à categoria dos clientes

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Clientes**.

### Caminhos sensíveis à configuração do cliente e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Clientes** > **Configuração do cliente**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Domínio de email padrão | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Categoria do catálogo

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Catálogo**.

### Caminhos sensíveis ao catálogo e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API do YouTube | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Hostname do servidor Solr | `catalog/search/solr_server_hostname` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do servidor Solr | `catalog/search/solr_server_port` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome de usuário do servidor Solr | `catalog/search/solr_server_username` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha do servidor Solr | `catalog/search/solr_server_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho do servidor Solr | `catalog/search/solr_server_path` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome de host do servidor Elasticsearch | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do servidor Elasticsearch | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Prefixo de índice Elasticsearch | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Habilitar autenticação HTTP do Elasticsearch | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Nome de usuário HTTP do Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha HTTP do Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Tempo limite do servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Nome de usuário HTTP do Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Senha HTTP do Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Tempo limite do servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Hostname do OpenSearch Server | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do OpenSearch Server | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Prefixo de Índice OpenSearch | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Habilitar Autenticação HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Nome de usuário HTTP do OpenSearch | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Senha HTTP do OpenSearch | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Tempo Limite do OpenSearch Server | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>As configurações do OpenSearch foram introduzidas no Adobe Commerce 2.4.6.

### Caminhos sensíveis ao inventário e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Catálogo** > **Inventário**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chave da API do Google | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis ao mapa de site XML e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Catálogo** > **Mapa do site XML**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria de vendas

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Vendas**.

### Caminhos sensíveis e específicos do sistema das configurações de envio

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Configurações de envio**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| País | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Região/Estado | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| CEP | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cidade | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Rua Endereço Linha 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Conta online | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema para emails de vendas

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de vendas**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar cópia do e-mail do pedido para | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia do e-mail de comentário do pedido para | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email de fatura para | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Comentário da Fatura por Email para | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia do e-mail de remessa para | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia do e-mail de comentário da remessa para | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Aviso de Crédito para | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email de comentário do memorando de crédito para | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email pronta para retirada para | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Fazer check-out de caminhos confidenciais e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Check-out**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar pagamento com falha Enviar cópia do e-mail para | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis à API do Google e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **API do Google**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID do contêiner | `google/analytics/container_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema para métodos de entrega

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de delivery**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de gateway | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL do Secure Gateway | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Título | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de usuário | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de usuário | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número da licença de acesso | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL XML de rastreamento | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL XML de Gateway | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número do Remetente | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Conta | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número do Medidor | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de acesso | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Número da conta | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de gateway | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis às vendas e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Vendas**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do contato | `sales/magento_rma/store_name` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `sales/magento_rma/address` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cidade | `sales/magento_rma/city` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Estado/Província | `sales/magento_rma/region_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| CEP | `sales/magento_rma/zip` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| País | `sales/magento_rma/country_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email do RMA para | `sales_email/magento_rma/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email de autorização RMA para | `sales_email/magento_rma_auth/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email de comentário RMA para | `sales_email/magento_rma_comment/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email de comentário RMA para | `sales_email/magento_rma_customer_comment/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos da API do Google

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **API do Google**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Número da conta | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria avançada

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Avançado**.

### Caminhos sensíveis ao administrador e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Admin**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de administração personalizada | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho de administração personalizado | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis ao sistema e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Lista de acesso | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Erro de remetente de email | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis ao desenvolvedor e específicos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IPs permitidos (separados por vírgula) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria avançada

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Avançado**.

### Caminhos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host de back-end | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta de back-end | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos do desenvolvedor

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registrar Erros JS na Chave de Armazenamento da Sessão | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Caminhos sensíveis ao pagamento e específicos do sistema

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Vendas** > **Pagamento**.

### Variável geral

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| País do comerciante | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>Sua escolha para essa variável determina qual [Caminhos internacionais](#international-paths) você pode usar.

### Caminhos sensíveis ao PayPal e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Email associado à conta de comerciante do PayPal (opcional) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Conta do Comerciante | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do editor | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Logon | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome de host ou endereço IP do ponto de extremidade personalizado | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payflow Pro

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho personalizado | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Usuário | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Parceiro | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host do proxy | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do proxy | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de depuração | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Configurações de cartão de crédito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payflow Link

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Usar proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Host do proxy | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Porta do proxy | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Método de URL para URL de retorno e URL de cancelamento | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payments Pro

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome de usuário da API | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Assinatura da API | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Certificado de API | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host do proxy | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do proxy | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro Hospedou caminhos confidenciais e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modo de depuração | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### caminhos sensíveis ao Braintree e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID do comerciante | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave pública | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave privada | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Conta do Comerciante | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Comerciante Kount | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Substituir Nome do Comerciante | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Telefone | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Caminhos de Cheque/Ordem de Pagamento

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar verificação para | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Caminhos internacionais

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chave da transação | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_au/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_au/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_au/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_au/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_au/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_au/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `payment_au/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_au/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_au/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_au/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_au/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_au/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_au/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_es/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_es/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_es/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_es/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_es/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_es/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_es/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `payment_es/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_es/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_es/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_es/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_es/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_es/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_es/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_es/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_nz/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_nz/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_nz/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_nz/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_nz/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_nz/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_nz/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_nz/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_nz/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Host do proxy | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do proxy | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Método de URL para URL de retorno e URL de cancelamento | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_us/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_us/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_us/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_us/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_us/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_us/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_us/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_us/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_us/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_us/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_us/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_gb/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_gb/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_gb/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_gb/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_gb/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_gb/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_gb/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_gb/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_gb/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_de/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_de/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_de/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_de/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave da transação | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de resposta de pagamento | `payment_de/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_de/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `payment_de/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_de/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_de/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_de/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_de/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_de/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_de/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_de/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de gateway | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave da transação | `payment_other/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_other/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_other/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_other/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_other/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_other/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_other/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_other/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_other/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_other/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_other/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_other/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_other/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_other/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_other/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_ca/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_ca/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_ca/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_ca/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de teste | `payment_ca/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_ca/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de autorização do administrador remoto | `payment_ca/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_ca/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_ca/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_ca/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_ca/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_ca/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_ca/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_ca/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_ca/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_hk/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_hk/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_hk/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de resposta de pagamento | `payment_hk/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_hk/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de API dinâmica | `payment_hk/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_hk/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_hk/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_hk/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_hk/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_hk/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_jp/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_jp/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_jp/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_jp/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_jp/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_jp/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_jp/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_jp/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_jp/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_jp/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_jp/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_jp/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_jp/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_jp/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_jp/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_fr/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_fr/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_fr/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_fr/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_fr/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_fr/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_fr/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_fr/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_fr/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_fr/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_fr/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_fr/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| URL de gateway | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_it/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_it/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_it/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Senha de resposta de pagamento | `payment_it/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_it/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_it/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | ![Específico do sistema](/help/assets/configuration/cloud-env.png) |
| Chave de API dinâmica | `payment_it/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API dinâmica | `payment_it/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia ativa do lado do cliente | `payment_it/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_it/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API de sandbox | `payment_it/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente de sandbox | `payment_it/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de API | `fraud_protection/signifyd/api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL da API | `fraud_protection/signifyd/api_url` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do sistema](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_au/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_au/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_es/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_es/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_es/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP |
| Credenciais SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_nz/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_nz/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_nz/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_nz/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_nz/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_nz/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de resposta de pagamento | `payment_nz/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_nz/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_nz/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_nz/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_us/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_us/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_us/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_us/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de resposta de pagamento | `payment_us/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_us/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_us/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_us/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_gb/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_gb/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_gb/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_gb/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_gb/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_gb/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de resposta de pagamento | `payment_gb/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_gb/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização do administrador remoto | `payment_gb/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_de/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_de/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_de/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID da Instalação do Administrador Remoto | `payment_de/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_de/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_other/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_other/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_other/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_other/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_other/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_ca/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_ca/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_ca/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_ca/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_ca/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_hk/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_hk/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_hk/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_hk/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_hk/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_hk/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_jp/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_jp/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_jp/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID da Instalação do Administrador Remoto | `payment_jp/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_jp/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_jp/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_fr/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_fr/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_fr/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_fr/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_fr/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_fr/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar cheque pagável a | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| MD5 do comerciante | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar email para o cliente | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do comerciante | `payment_it/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_it/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da instalação | `payment_it/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da Instalação do Administrador Remoto | `payment_it/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para Transações | `payment_it/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | | | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
