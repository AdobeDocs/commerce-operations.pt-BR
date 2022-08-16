---
title: Caminhos sensíveis e específicos do sistema
description: Consulte uma lista de valores de configuração confidenciais e específicos do sistema.
source-git-commit: 019d638403f2dc3e170a56842335da203126d8a6
workflow-type: tm+mt
source-wordcount: '3711'
ht-degree: 0%

---


# Configurações sensíveis e específicas do sistema

Este tópico lista os caminhos de configuração para configurações confidenciais e específicas do sistema:

- O [`magento app:config:dump` comando](../cli/export-configuration.md) grava configurações específicas do sistema no arquivo de configuração específico do sistema, `app/etc/env.php`, que _not_ estar no controle de origem. Ele também grava a configuração compartilhada para todas as instâncias do Commerce no `app/etc/config.php`, este arquivo _should_ estar no controle de origem.
- O [`magento config:sensitive:set` comando](../cli/set-configuration-values.md) grava configurações confidenciais em `app/etc/env.php`.

   Você também pode definir valores confidenciais usando variáveis de configuração, como discutido em [Usar variáveis de ambiente para substituir configurações](../reference/override-config-settings.md#environment-variables).

Para obter uma lista de outros caminhos de configuração, consulte:

- [Todos os caminhos de configuração, exceto pagamentos](../reference/config-reference-general.md)
- [Caminhos de configuração de pagamento](../reference/config-reference-payment.md).

>[!INFO]
>
>Todos os caminhos de configuração listados neste tópico são confidenciais. O `System-specific?` mostra quais valores também são específicos do sistema.

## Caminhos gerais sensíveis à categoria e específicos do sistema

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Geral**.

### Caminhos da Web sensíveis e caminhos específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Web**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL básica | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do link básico | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL base para arquivos de visualização estática | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL base para arquivos de mídia do usuário | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL de base segura | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do Link Base Seguro | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL de base segura para arquivos de visualização estática | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL de base segura para arquivos de mídia do usuário | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL da Web padrão | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL padrão sem rota | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Caminho do cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Domínio do cookie | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Duração do cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Usar somente HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de restrição de cookie | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Configuração de moeda sensível e caminhos específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Configuração de moeda**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Recipient de email com erro | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Armazenar caminhos sensíveis e específicos do sistema para o endereço de email

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração de email** > **Geral** > **Armazenar endereços de email**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do remetente | `trans_email/ident_general/name` |  |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do remetente | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do remetente | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do remetente | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do remetente | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do remetente | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do remetente | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis aos contatos e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Contatos**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar Emails para | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Remetente de email | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modelo de email | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Novo Relic reportando caminhos sensíveis e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Novo relatório de relance**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nova ID de Conta Relic | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo ID de Aplicativo Relic | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nova Chave da API Relic | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API do Insights | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo URL da API Relic | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL da API do Insights | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Os clientes distinguem as categorias e os caminhos específicos do sistema

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Clientes**.

### Configuração do cliente sensível e caminhos específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Configuração do cliente**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Domínio de email padrão | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## Categoria do catálogo

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Catálogo**.

### Caminhos sensíveis ao catálogo e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Recipient de email com erro | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API do YouTube | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do host do servidor Solr | `catalog/search/solr_server_hostname` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do servidor Solr | `catalog/search/solr_server_port` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome de usuário do servidor Solr | `catalog/search/solr_server_username` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha do servidor Solr | `catalog/search/solr_server_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho do servidor Solr | `catalog/search/solr_server_path` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do host do servidor Elasticsearch | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta do Servidor Elasticsearch | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Prefixo de Índice de Elasticsearch | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Habilitar Autenticação HTTP do Elasticsearch | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Nome de usuário HTTP do Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha HTTP do Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Tempo limite do servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis ao inventário e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Inventário**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chave da API do Google | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis e específicos do sistema do mapa de site XML

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Mapa do Site XML**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Recipient de email com erro | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoria de vendas

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Vendas**.

### Configurações de envio sensíveis e caminhos específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Configurações de envio**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| País | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Região/Estado | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| CEP/Código postal | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cidade | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Rua Linha 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Conta ao vivo | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Emails de vendas são caminhos sensíveis e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de vendas**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar Cópia de Email de Pedido para | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email do Comentário do Pedido para | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de E-mail da fatura para | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email do Comentário da NFF para | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Remessa para | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email do Comentário de Entrega para | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email do Aviso de Crédito para | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email do Comentário do Aviso de Crédito para | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email pronta para seleção para | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Fazer check-out de caminhos sensíveis e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Check-out**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar Cópia de Correio Eletrônico com Falha ao Enviar Pagamento para | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis à API do Google e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **API do Google**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID do contêiner | `google/analytics/container_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Métodos de delivery caminhos sensíveis e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de delivery**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL do gateway | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL do gateway seguro | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Título | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de usuário | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de usuário | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número da licença de acesso | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Rastreamento do URL XML | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL XML do gateway | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número do remetente | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID da conta | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Número do Medidor | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de acesso | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número da conta | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL do gateway | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis às vendas e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Vendas**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do contato | `sales/magento_rma/store_name` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `sales/magento_rma/address` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Endereço | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cidade | `sales/magento_rma/city` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Estado/Província | `sales/magento_rma/region_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| CEP/Código postal | `sales/magento_rma/zip` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| País | `sales/magento_rma/country_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia de email RMA para | `sales_email/magento_rma/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Autorização RMA para | `sales_email/magento_rma_auth/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Comentário RMA para | `sales_email/magento_rma_comment/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Comentário RMA para | `sales_email/magento_rma_customer_comment/copy_to` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos da API do Google

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **API do Google**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Número da conta | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoria avançada

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Avançado**.

### Caminhos sensíveis ao administrador e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Administrador**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de administrador personalizado | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho de administração personalizado | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis ao sistema e específicos ao sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Recipient de email com erro | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Lista de acesso | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Remetente de email de erro | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis ao desenvolvedor e específicos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IPs permitidos (separados por vírgulas) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoria avançada

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Avançado**.

### Caminhos do sistema

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host back-end | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta de backend | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos do desenvolvedor

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registrar erros de JS na chave de armazenamento de sessão | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## Caminhos sensíveis ao pagamento e específicos do sistema

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Vendas** > **Pagamento**.

### Variável geral

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| País Merchant | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

>[!INFO]
>
>Sua escolha para essa variável determina qual [Caminhos internacionais](#international-paths) você pode usar.

### Caminhos sensíveis do PayPal e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Email associado à conta de merchant paga (opcional) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de conta do comerciante | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Publisher ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Logon | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Nome do host do ponto de extremidade personalizado ou endereço IP | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payflow Pro caminhos sensíveis e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Caminho personalizado | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Usuário | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Parceiro | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host Proxy | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta de Proxy | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de depuração | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Configurações do cartão de crédito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis e específicos do sistema do Link de fluxo de pagamento do PayPal

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Usar proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Host Proxy | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Porta de Proxy | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Método de URL para Cancelar URL e Retornar URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Pagamentos PayPal Pro caminhos sensíveis e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome de usuário da API | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Assinatura da API | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Certificado de API | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Host Proxy | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta de Proxy | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Pagamentos PayPal Pro Caminhos confidenciais e específicos do sistema hospedados

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modo de depuração | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos sensíveis a Braintree e específicos do sistema

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de Merchant | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave pública | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de privacidade | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de conta do comerciante | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Substituir Nome do Comerciante | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Telefone | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos de cheque/ordem monetária

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar verificação para | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Caminhos internacionais

| Nome | Caminho de configuração | Somente comércio? | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chave da transação | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_au/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_au/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_au/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_au/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_au/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_au/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de sandbox | `payment_au/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_au/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_au/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_au/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_au/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_au/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_au/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_es/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_es/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_es/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_es/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_es/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_es/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_es/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `payment_es/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_es/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_es/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_es/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_es/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_es/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_es/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_es/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_nz/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_nz/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_nz/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_nz/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_nz/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_nz/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_nz/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_nz/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_nz/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Host Proxy | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Porta de Proxy | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de depuração | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Método de URL para Cancelar URL e Retornar URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_us/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_us/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_us/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_us/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_us/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_us/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_us/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_us/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_us/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_us/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_us/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_gb/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_gb/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_gb/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_gb/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_gb/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_gb/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_gb/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_gb/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_gb/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_de/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_de/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_de/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_de/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da transação | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de Resposta de Pagamento | `payment_de/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_de/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Depurar | `payment_de/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_de/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_de/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_de/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_de/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_de/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_de/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_de/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL do gateway | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da transação | `payment_other/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_other/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_other/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_other/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_other/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_other/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_other/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_other/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_other/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_other/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_other/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_other/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_other/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_other/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_other/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_ca/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_ca/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_ca/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_ca/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de teste | `payment_ca/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_ca/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de autorização de administrador remoto | `payment_ca/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_ca/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_ca/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_ca/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_ca/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_ca/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_ca/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_ca/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_ca/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_hk/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_hk/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_hk/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de Resposta de Pagamento | `payment_hk/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_hk/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_hk/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API ao vivo | `payment_hk/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_hk/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_hk/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_hk/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_hk/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_hk/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_jp/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_jp/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_jp/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_jp/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de teste | `payment_jp/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_jp/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_jp/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_jp/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_jp/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_jp/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_jp/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_jp/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_jp/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_jp/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_jp/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_fr/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_fr/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_fr/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_fr/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_fr/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_fr/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_fr/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_fr/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_fr/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_fr/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_fr/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_fr/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_fr/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| URL do gateway | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL de Detalhes da Transação | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_it/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_it/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_it/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/cybersource/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Senha de Resposta de Pagamento | `payment_it/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_it/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Modo de teste | `payment_it/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Modo de sandbox | `payment_it/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) |
| Chave da API ao vivo | `payment_it/eway/live_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API ao vivo | `payment_it/eway/live_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente ativo | `payment_it/eway/live_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API de sandbox | `payment_it/eway/sandbox_api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha da API do Sandbox | `payment_it/eway/sandbox_api_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de criptografia do lado do cliente do Sandbox | `payment_it/eway/sandbox_encryption_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da API | `fraud_protection/signifyd/api_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| URL da API | `fraud_protection/signifyd/api_url` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  | ![Específico do Sys](/help/assets/configuration/cloud-env.png) | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_au/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_au/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_es/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_es/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_es/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP |
| Credenciais SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_nz/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_nz/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_nz/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_nz/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_nz/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_nz/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de Resposta de Pagamento | `payment_nz/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_nz/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_nz/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_nz/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_us/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_us/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_us/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_us/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de Resposta de Pagamento | `payment_us/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_us/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_us/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_us/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_gb/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_gb/cybersource/transaction_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_gb/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave de acesso | `payment_gb/cybersource/access_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave secreta | `payment_gb/cybersource/secret_key` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Chave da transação | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_gb/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de Resposta de Pagamento | `payment_gb/worldpay/response_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_gb/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Senha de autorização de administrador remoto | `payment_gb/worldpay/auth_password` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_de/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_de/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_de/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID de instalação remota do administrador | `payment_de/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_de/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_other/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_other/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_other/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_other/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_other/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Novo status do pedido | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_ca/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_ca/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_ca/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_ca/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_ca/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_hk/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_hk/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_hk/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_hk/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_hk/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_hk/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_jp/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_jp/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_jp/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID de instalação remota do administrador | `payment_jp/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_jp/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_jp/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_fr/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_fr/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_fr/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_fr/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_fr/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Campos de assinatura | `payment_fr/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Tornar o cheque a pagar para | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar verificação para | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de logon da API | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Cliente de email | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Email do comerciante | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de Merchant | `payment_it/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID do perfil | `payment_it/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação | `payment_it/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| ID de instalação remota do administrador | `payment_it/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Segredo MD5 para transações | `payment_it/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}
