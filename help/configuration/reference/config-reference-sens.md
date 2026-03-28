---
title: Caminhos sensíveis e específicos do sistema
description: Saiba mais sobre os caminhos de configuração confidenciais e específicos do sistema para o Adobe Commerce. Descubra a configuração segura e o gerenciamento de variáveis de ambiente.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# Configurações sensíveis e específicas do sistema

Este tópico lista os caminhos de configuração para configurações confidenciais e específicas do sistema:

- O comando [`magento app:config:dump` ](../cli/export-configuration.md) grava configurações específicas do sistema no arquivo de configuração específico do sistema, `app/etc/env.php`, que deve _não_ estar no controle de origem. Também grava a configuração compartilhada de todas as instâncias do Commerce em `app/etc/config.php`. Este arquivo _deve_ estar no controle de origem.
- O comando [`magento config:sensitive:set` ](../cli/set-configuration-values.md) grava configurações confidenciais em `app/etc/env.php`.

  Você também pode definir valores confidenciais usando variáveis de configuração, conforme discutido em [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables).

Para obter uma lista de outros caminhos de configuração, consulte:

- [Todos os caminhos de configuração exceto pagamentos](../reference/config-reference-general.md)
- [Caminhos de configuração de pagamento](../reference/config-reference-payment.md).

>[!INFO]
>
>Todos os caminhos de configuração listados neste tópico são confidenciais. A coluna `System-specific?` mostra quais valores também são específicos do sistema.

## Caminhos gerais sensíveis à categoria e específicos do sistema

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Geral**.

### Caminhos da Web sensíveis e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Web**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL base | `web/unsecure/base_url` |  | | Específico do sistema | |
| URL base do link | `web/unsecure/base_link_url` |  | | Específico do sistema | |
| URL base para arquivos de visualização estáticos | `web/unsecure/base_static_url` |  | | Específico do sistema | |
| URL base dos arquivos de mídia do usuário | `web/unsecure/base_media_url` |  | | Específico do sistema | |
| URL de base segura | `web/secure/base_url` |  | | Específico do sistema | |
| URL do Link de base seguro | `web/secure/base_link_url` |  | | Específico do sistema | |
| URL de base segura para arquivos de visualização estática | `web/secure/base_static_url` |  | | Específico do sistema | |
| URL de base segura para arquivos de mídia do usuário | `web/secure/base_media_url` |  | | Específico do sistema | |
| URL padrão da Web | `web/default/front` |  | | Específico do sistema | |
| URL padrão sem rota | `web/default/no_route` |  | | Específico do sistema | |
| Caminho do cookie | `web/cookie/cookie_path` |  | | Específico do sistema | |
| Domínio do cookie | `web/cookie/cookie_domain` |  | | Específico do sistema | |
| Duração do cookie | `web/cookie/cookie_lifetime` |  | | Específico do sistema | |
| Usar somente HTTP | `web/cookie/cookie_httponly` |  | | Específico do sistema | |
| Modo de restrição de cookies | `web/cookie/cookie_restriction` |  | | Específico do sistema | |

{style="table-layout:auto"}

### Caminhos sensíveis à configuração de moeda e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Configuração de moeda**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
| --- | --- | --- | --- | --- | --- |
| Destinatário de email de erro | `currency/import/error_email` |  | | | Sensível |

{style="table-layout:auto"}

### Armazenar caminhos sensíveis ao endereço de email e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração de Email** > **Geral** > **Armazenar Endereços de Email**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do remetente | `trans_email/ident_general/name` | | | | Sensível |
| E-mail do remetente | `trans_email/ident_general/email` |  | | | Sensível |
| Nome do remetente | `trans_email/ident_sales/name` |  | | | Sensível |
| E-mail do remetente | `trans_email/ident_sales/email` |  | | | Sensível |
| Nome do remetente | `trans_email/ident_support/name` |  | | | Sensível |
| E-mail do remetente | `trans_email/ident_support/email` |  | | | Sensível |
| Nome do remetente | `trans_email/ident_custom1/name` |  | | | Sensível |
| E-mail do remetente | `trans_email/ident_custom1/email` |  | | | Sensível |
| Nome do remetente | `trans_email/ident_custom2/name` |  | | | Sensível |
| E-mail do remetente | `trans_email/ident_custom2/email` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis ao contato e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Contatos**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar Emails Para | `contact/email/recipient_email` |  | | | Sensível |
| Remetente do email | `contact/email/sender_email_identity` |  | | | Sensível |
| Modelo de e-mail | `contact/email/email_template` |  | | | Sensível |

{style="table-layout:auto"}

### Relatórios do New Relic sobre caminhos sigilosos e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Geral** > **Relatórios do New Relic**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID da conta do New Relic | `newrelicreporting/general/account_id` |  | | | Sensível |
| ID do aplicativo New Relic | `newrelicreporting/general/app_id` |  | | | Sensível |
| Chave da API do New Relic | `newrelicreporting/general/api` |  | Criptografado | | Sensível |
| Chave da API do Insights | `newrelicreporting/general/insights_insert_key` |  | Criptografado | | Sensível |
| URL da API New Relic | `newrelicreporting/general/api_url` |  | | Específico do sistema | Sensível |
| URL da API do Insights | `newrelicreporting/general/insights_api_url` |  | | Específico do sistema | Sensível |

{style="table-layout:auto"}

## Caminhos específicos do sistema e sensíveis à categoria dos clientes

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes**.

### Caminhos sensíveis à configuração do cliente e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Configuração do Cliente**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Domínio de email padrão | `customer/create_account/email_domain` |  | | Específico do sistema | |

{style="table-layout:auto"}

## Categoria do catálogo

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo**.

### Caminhos sensíveis ao catálogo e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `catalog/productalert_cron/error_email` |  | | | Sensível |
| Chave da API do YouTube | `catalog/product_video/youtube_api_key` |  | | | Sensível |
| Hostname do servidor Solr | `catalog/search/solr_server_hostname` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Porta do servidor Solr | `catalog/search/solr_server_port` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Nome de usuário do servidor Solr | `catalog/search/solr_server_username` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha do servidor Solr | `catalog/search/solr_server_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Caminho do servidor Solr | `catalog/search/solr_server_path` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Hostname do servidor Elasticsearch | `catalog/search/elasticsearch_server_hostname` |  | | Específico do sistema | Sensível |
| Porta do servidor do Elasticsearch | `catalog/search/elasticsearch_server_port` |  | | Específico do sistema | Sensível |
| Prefixo do índice Elasticsearch | `catalog/search/elasticsearch_index_prefix` |  | | Específico do sistema | Sensível |
| Ativar autenticação HTTP do Elasticsearch | `catalog/search/elasticsearch_enable_auth` |  | | Específico do sistema | |
| Nome de usuário HTTP do Elasticsearch | `catalog/search/elasticsearch_username` |  | | Específico do sistema | |
| Senha HTTP do Elasticsearch | `catalog/search/elasticsearch_password` |  | | Específico do sistema | |
| Tempo limite do servidor do Elasticsearch | `catalog/search/elasticsearch_server_timeout` |  | | Específico do sistema | |
| Nome de usuário HTTP do Elasticsearch | `catalog/search/elasticsearch_username` | | | Específico do sistema | |
| Senha HTTP do Elasticsearch | `catalog/search/elasticsearch_password` | | | Específico do sistema | |
| Tempo limite do servidor do Elasticsearch | `catalog/search/elasticsearch_server_timeout` | | | Específico do sistema | |
| Hostname do OpenSearch Server | `catalog/search/opensearch_server_hostname` | | | Específico do sistema | Sensível |
| Porta do OpenSearch Server | `catalog/search/opensearch_server_port` | | | Específico do sistema | Sensível |
| Prefixo de Índice OpenSearch | `catalog/search/opensearch_index_prefix` | | | Específico do sistema | Sensível |
| Habilitar Autenticação HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | | | Específico do sistema | |
| Nome de usuário HTTP do OpenSearch | `catalog/search/opensearch_username` | | | Específico do sistema | |
| Senha HTTP do OpenSearch | `catalog/search/opensearch_password` | | | Específico do sistema | |
| Tempo Limite do OpenSearch Server | `catalog/search/opensearch_server_timeout` | | | Específico do sistema | |

{style="table-layout:auto"}

>[!NOTE]
>
>As configurações do OpenSearch foram introduzidas no Adobe Commerce 2.4.6.

### Caminhos sensíveis ao inventário e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Inventário**.

Nome Caminho de configuração Suporte à versão do Commerce Criptografado? | Específico do sistema? Sensível? | |
|—|—|—|—|—|
| Chave da API do Google | `cataloginventory/source_selection_distance_based_google/api_key` | Criptografada | Sensível |

### Caminhos sensíveis ao mapa de site XML e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Mapa de Site XML**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `sitemap/generate/error_email` |  | | | Sensível |

{style="table-layout:auto"}

## Categoria de vendas

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas**.

### Caminhos sensíveis e específicos do sistema das configurações de envio

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Configurações de Remessa**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| País | `shipping/origin/country_id` |  | | | Sensível |
| Região/Estado | `shipping/origin/region_id` |  | | | Sensível |
| CEP | `shipping/origin/postcode` |  | | | Sensível |
| Cidade | `shipping/origin/city` |  | | | Sensível |
| Endereço | `shipping/origin/street_line1` |  | | | Sensível |
| Rua Endereço Linha 2 | `shipping/origin/street_line2` |  | | | Sensível |
| Conta online | `carriers/ups/is_account_live` |  | | Específico do sistema | |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema para emails de vendas

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de Vendas**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar cópia do e-mail do pedido para | `sales_email/order/copy_to` |  | | | Sensível |
| Enviar cópia do e-mail de comentário do pedido para | `sales_email/order_comment/copy_to` |  | | | Sensível |
| Enviar cópia de email de fatura para | `sales_email/invoice/copy_to` |  | | | Sensível |
| Enviar Comentário da Fatura por Email para | `sales_email/invoice_comment/copy_to` |  | | | Sensível |
| Enviar cópia do e-mail de remessa para | `sales_email/shipment/copy_to` |  | | | Sensível |
| Enviar cópia do e-mail de comentário da remessa para | `sales_email/shipment_comment/copy_to` |  | | | Sensível |
| Enviar Cópia de Email de Aviso de Crédito para | `sales_email/creditmemo/copy_to` |  | | | Sensível |
| Enviar cópia de email de comentário do memorando de crédito para | `sales_email/creditmemo_comment/copy_to` |  | | | Sensível |
| Enviar cópia de email pronta para retirada para | `sales_email/temando_pickup/copy_to` |  | | | Sensível |

{style="table-layout:auto"}

### Fazer check-out de caminhos confidenciais e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Check-out**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar pagamento com falha Enviar cópia do e-mail para | `checkout/payment_failed/copy_to` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis à API do Google e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **API Google**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID do contêiner | `google/analytics/container_id` | Somente Commerce Enterprise | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema para métodos de entrega

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de Entrega**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de gateway | `carriers/usps/gateway_url` |  | | | Sensível |
| URL do Secure Gateway | `carriers/usps/gateway_secure_url` |  | | | Sensível |
| Título | `carriers/usps/title` |  | | | |
| ID de usuário | `carriers/usps/userid` |  | Criptografado | | Sensível |
| Senha | `carriers/usps/password` |  | Criptografado | | Sensível |
| ID de usuário | `carriers/ups/username` |  | Criptografado | | Sensível |
| Senha | `carriers/ups/password` |  | Criptografado | | Sensível |
| Número da licença de acesso | `carriers/ups/access_license_number` |  | Criptografado | | Sensível |
| URL XML de rastreamento | `carriers/ups/tracking_xml_url` |  | | | Sensível |
| URL XML de Gateway | `carriers/ups/gateway_xml_url` |  | | | Sensível |
| Número do Remetente | `carriers/ups/shipper_number` |  | | | Sensível |
| Depurar | `carriers/ups/debug` |  | | | Sensível |
| ID da Conta | `carriers/fedex/account` |  | Criptografado | | Sensível |
| Chave | `carriers/fedex/key` |  | Criptografado | | Sensível |
| Número do Medidor | `carriers/fedex/meter_number` |  | Criptografado | | Sensível |
| Senha | `carriers/fedex/password` |  | Criptografado | | Sensível |
| ID de acesso | `carriers/dhl/id` |  | Criptografado | | Sensível |
| Senha | `carriers/dhl/password` |  | Criptografado | | Sensível |
| Depurar | `carriers/dhl/debug` |  | | | |
| Número da conta | `carriers/dhl/account` |  | | | Sensível |
| URL de gateway | `carriers/dhl/gateway_url` |  | | | Sensível |
| Modo de sandbox | `carriers/fedex/sandbox_mode` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis às vendas e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Vendas**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome do contato | `sales/magento_rma/store_name` | Somente Commerce Enterprise | | | Sensível |
| Endereço | `sales/magento_rma/address` | Somente Commerce Enterprise | | | Sensível |
| Endereço | `sales/magento_rma/address1` |  | | | Sensível |
| Cidade | `sales/magento_rma/city` | Somente Commerce Enterprise | | | Sensível |
| Estado/Província | `sales/magento_rma/region_id` | Somente Commerce Enterprise | | | Sensível |
| CEP | `sales/magento_rma/zip` | Somente Commerce Enterprise | | | Sensível |
| País | `sales/magento_rma/country_id` | Somente Commerce Enterprise | | | Sensível |
| Enviar cópia de email do RMA para | `sales_email/magento_rma/copy_to` | Somente Commerce Enterprise | | | Sensível |
| Enviar cópia de email de autorização RMA para | `sales_email/magento_rma_auth/copy_to` | Somente Commerce Enterprise | | | Sensível |
| Enviar cópia de email de comentário RMA para | `sales_email/magento_rma_comment/copy_to` | Somente Commerce Enterprise | | | Sensível |
| Enviar cópia de email de comentário RMA para | `sales_email/magento_rma_customer_comment/copy_to` | Somente Commerce Enterprise | | | Sensível |

{style="table-layout:auto"}

### Caminhos da API do Google

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **API Google**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Número da conta | `google/analytics/account` |  | | | Sensível |

{style="table-layout:auto"}

## Categoria avançada

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Avançadas**.

### Caminhos sensíveis ao administrador e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançadas** > **Administração**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de administração personalizada | `admin/url/custom` |  | | | Sensível |
| Caminho de administração personalizado | `admin/url/custom_path` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis ao sistema e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatário de email de erro | `system/magento_scheduled_import_export_log/error_email` |  | | | Sensível |
| Lista de acesso | `system/full_page_cache/varnish/access_list` |  |  | | Sensível |
| Erro de remetente de email | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis ao desenvolvedor e específicos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IPs permitidos (separados por vírgula) | `dev/restrict/allow_ips` |  | | Específico do sistema | Sensível |

{style="table-layout:auto"}

## Categoria avançada

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Avançadas**.

### Caminhos do sistema

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` |  | | Específico do sistema | Sensível |
| Porta (25) | `system/smtp/port` |  | | Específico do sistema | Sensível |
| Host de back-end | `system/full_page_cache/varnish/backend_host` |  | | Específico do sistema | Sensível |
| Porta de back-end | `system/full_page_cache/varnish/backend_port` |  | | Específico do sistema | Sensível |

{style="table-layout:auto"}

### Caminhos do desenvolvedor

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registrar Erros JS na Chave de Armazenamento da Sessão | `dev/js/session_storage_key` | ![Não somente Commerce](/help/assets/configuration/red-x.png) | | Específico do sistema | |

{style="table-layout:auto"}

## Caminhos sensíveis ao pagamento e específicos do sistema

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Pagamento**.

### Variável geral

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? |
|--------------|--------------|--------------|--------------|
| País do comerciante | `paypal/general/merchant_country` |  | Sensível |

{style="table-layout:auto"}

>[!INFO]
>
>Sua escolha para esta variável determina quais [Caminhos internacionais](#international-paths) você pode usar.

### Caminhos sensíveis ao PayPal e específicos do sistema

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Email associado à conta de comerciante do PayPal (opcional) | `paypal/general/business_account` |  | | | Sensível |
| ID da Conta do Comerciante | `payment/paypal_express/merchant_id` |  | | | Sensível |
| ID do editor | `payment/paypal_express_bml/publisher_id` |  | | | Sensível |
| Senha | `paypal/fetch_reports/ftp_password` |  | Criptografado | | Sensível |
| Logon | `paypal/fetch_reports/ftp_login` |  | Criptografado | | Sensível |
| Nome de host ou endereço IP do ponto de extremidade personalizado | `paypal/fetch_reports/ftp_ip` |  | | Específico do sistema | Sensível |
| Modo de sandbox | `paypal/fetch_reports/ftp_sandbox` |  | | Específico do sistema | |
| Modo de depuração | `payment/paypal_express/debug` |  | | Específico do sistema | |
| Modo de depuração | `payment/paypal_billing_agreement/debug` |  | | Específico do sistema | |
| Credenciais SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payflow Pro

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_advanced/user` |  | Criptografado | | Sensível |
| Senha | `payment/payflow_advanced/pwd` |  | Criptografado | | Sensível |
| Caminho personalizado | `paypal/fetch_reports/ftp_path` |  | | Específico do sistema | Sensível |
| Usuário | `payment/payflowpro/user` |  | Criptografado | | Sensível |
| Senha | `payment/payflowpro/pwd` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment/payflowpro/sandbox_flag` |  | | Específico do sistema | |
| Parceiro | `payment/payflowpro/partner` |  | | | Sensível |
| Host do proxy | `payment/payflowpro/proxy_host` |  | | Específico do sistema | Sensível |
| Porta do proxy | `payment/payflowpro/proxy_port` |  | | Específico do sistema | Sensível |
| Modo de depuração | `payment/payflowpro/debug` |  | | Específico do sistema | |
| Credenciais SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | Específico do sistema | |
| Configurações de cartão de crédito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payflow Link

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuário | `payment/payflow_link/user` |  | Criptografado | | Sensível |
| Senha | `payment/payflow_link/pwd` |  | Criptografado | | Sensível |
| Modo de teste | `payment/payflow_link/sandbox_flag` |  | | Específico do sistema | |
| Usar proxy | `payment/payflow_link/use_proxy` |  | | Específico do sistema | |
| Host do proxy | `payment/payflow_link/proxy_host` |  | | Específico do sistema | |
| Porta do proxy | `payment/payflow_link/proxy_port` |  |  | Específico do sistema | |
| Modo de depuração | `payment/payflow_link/debug` |  | | Específico do sistema | |
| Método de URL para URL de retorno e URL de cancelamento | `payment/payflow_link/url_method` |  | | Específico do sistema | |
| Modo de depuração | `payment/payflow_express/debug` |  | | Específico do sistema | |
| Credenciais SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis e específicos do sistema do PayPal Payments Pro

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome de usuário da API | `paypal/wpp/api_username` |  | Criptografado | | Sensível |
| Senha da API | `paypal/wpp/api_password` |  | Criptografado | | Sensível |
| Assinatura da API | `paypal/wpp/api_signature` |  | Criptografado | | Sensível |
| Certificado de API | `paypal/wpp/api_cert` |  | | | Sensível |
| Host do proxy | `paypal/wpp/proxy_host` |  | | Específico do sistema | Sensível |
| Porta do proxy | `paypal/wpp/proxy_port` |  | | Específico do sistema | Sensível |
| Modo de sandbox | `paypal/wpp/sandbox_flag` |  | | Específico do sistema | |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |

{style="table-layout:auto"}

### PayPal Payments Pro Hospedou caminhos confidenciais e específicos do sistema

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modo de depuração | `payment/hosted_pro/debug` |  | | Específico do sistema | |
| Credenciais SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos sensíveis ao Braintree e específicos do sistema

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID do comerciante | `payment/braintree/merchant_id` |  | | | Sensível |
| Chave pública | `payment/braintree/public_key` |  | Criptografado | | Sensível |
| Chave privada | `payment/braintree/private_key` |  | Criptografado | | Sensível |
| ID da Conta do Comerciante | `payment/braintree/merchant_account_id` |  | | | Sensível |
| ID de Comerciante Kount | `payment/braintree/kount_id` |  | | | Sensível |
| Substituir Nome do Comerciante | `payment/braintree_paypal/merchant_name_override` |  | | | Sensível |
| Telefone | `payment/braintree/descriptor_phone` |  | | | Sensível |
| URL | `payment/braintree/descriptor_url` |  | | Específico do sistema | |

{style="table-layout:auto"}

### Caminhos de Cheque/Ordem de Pagamento

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar verificação para | `payment/checkmo/mailing_address` |  | | | Sensível |
| Enviar verificação para | `payment_us/checkmo/mailing_address` |  | | | Sensível |

{style="table-layout:auto"}

### Caminhos internacionais

| Nome | Caminho de configuração | Suporte à versão do Commerce | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chave da transação | `payment_au/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_au/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_au/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_au/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_au/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_au/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_au/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_au/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_au/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_au/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de sandbox | `payment_au/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_au/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_au/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_au/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_au/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_au/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_au/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_es/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_es/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_es/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_es/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_es/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_es/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_es/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_es/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_es/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_es/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Segredo MD5 para Transações | `payment_es/worldpay/md5_secret` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Depurar | `payment_es/worldpay/debug` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_es/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_es/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_es/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_es/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_es/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_es/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_es/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_nz/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_nz/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_nz/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Modo de teste | `payment_nz/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de teste | `payment_nz/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_nz/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_nz/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_nz/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_nz/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_nz/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Senha da API de sandbox | `payment_nz/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_nz/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment/payflow_advanced/sandbox_flag` |  | | Específico do sistema | |
| Host do proxy | `payment/payflow_advanced/proxy_host` |  | | Específico do sistema | Sensível |
| Porta do proxy | `payment/payflow_advanced/proxy_port` |  | | Específico do sistema | |
| Modo de depuração | `payment/payflow_advanced/debug` |  | | Específico do sistema | |
| Método de URL para URL de retorno e URL de cancelamento | `payment/payflow_advanced/url_method` |  | | Específico do sistema | |
| Modo de teste | `payment_us/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_us/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_us/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave de acesso | `payment_us/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_us/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_us/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de teste | `payment_us/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_us/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_us/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_us/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_us/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_us/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_us/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_us/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | |
| Modo de teste | `payment_gb/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de teste | `payment_gb/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_gb/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Modo de teste | `payment_gb/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_gb/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_gb/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_gb/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_gb/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_gb/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_gb/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_gb/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_de/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_de/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_de/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_de/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave da transação | `payment_de/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_de/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_de/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_de/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Senha de resposta de pagamento | `payment_de/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_de/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Depurar | `payment_de/worldpay/debug` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_de/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_de/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_de/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_de/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_de/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_de/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_de/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_other/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_other/authorizenet_directpost/test` |  | | Específico do sistema | Sensível |
| URL de gateway | `payment_other/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_other/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | |
| Chave da transação | `payment_other/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_other/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_other/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Novo status do pedido | `payment_other/cybersource/order_status` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de teste | `payment_other/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_other/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_other/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_other/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_other/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_other/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_other/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_other/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_other/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_other/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_other/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_ca/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_ca/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_ca/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_ca/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_ca/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_ca/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Novo status do pedido | `payment_ca/cybersource/order_status` | Somente Commerce Enterprise | | | |
| Modo de teste | `payment_ca/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_ca/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de autorização do administrador remoto | `payment_ca/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_ca/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_ca/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_ca/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_ca/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_ca/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_ca/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Senha da API de sandbox | `payment_ca/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_ca/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_hk/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_hk/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_hk/authorizenet_directpost/cgi_url` |  | | | Sensível |
| URL de Detalhes da Transação | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_hk/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_hk/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_hk/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_hk/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de resposta de pagamento | `payment_hk/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_hk/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_hk/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Chave de API dinâmica | `payment_hk/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Senha da API dinâmica | `payment_hk/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_hk/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_hk/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_hk/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_hk/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_jp/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_jp/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_jp/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_jp/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_jp/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_jp/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Novo status do pedido | `payment_jp/cybersource/order_status` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de teste | `payment_jp/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_jp/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_jp/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_jp/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_jp/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_jp/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_jp/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_jp/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_jp/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_jp/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_jp/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_fr/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_fr/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_fr/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_fr/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_fr/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_fr/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_fr/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_fr/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_fr/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_fr/worldpay/sandbox_flag` | Somente Commerce Enterprise |  | Específico do sistema | |
| Modo de sandbox | `payment_fr/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_fr/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_fr/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_fr/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_fr/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_fr/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_fr/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da transação | `payment_it/authorizenet_directpost/trans_key` |  | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_it/authorizenet_directpost/test` |  | | Específico do sistema | |
| URL de gateway | `payment_it/authorizenet_directpost/cgi_url` |  | | Específico do sistema | Sensível |
| URL de Detalhes da Transação | `payment_it/authorizenet_directpost/cgi_url_td` |  | | Específico do sistema | Sensível |
| Chave da transação | `payment_it/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de acesso | `payment_it/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave secreta | `payment_it/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Modo de teste | `payment_it/cybersource/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Senha de resposta de pagamento | `payment_it/worldpay/response_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Senha de autorização do administrador remoto | `payment_it/worldpay/auth_password` | Somente Commerce Enterprise | | Específico do sistema | Sensível |
| Modo de teste | `payment_it/worldpay/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Modo de sandbox | `payment_it/eway/sandbox_flag` | Somente Commerce Enterprise | | Específico do sistema | |
| Chave de API dinâmica | `payment_it/eway/live_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API dinâmica | `payment_it/eway/live_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia ativa do lado do cliente | `payment_it/eway/live_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave da API de sandbox | `payment_it/eway/sandbox_api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Senha da API de sandbox | `payment_it/eway/sandbox_api_password` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de criptografia do lado do cliente de sandbox | `payment_it/eway/sandbox_encryption_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| Chave de API | `fraud_protection/signifyd/api_key` | Somente Commerce Enterprise | Criptografado | Específico do sistema | Sensível |
| URL da API | `fraud_protection/signifyd/api_url` | Somente Commerce Enterprise |  | Específico do sistema | Sensível |
| Credenciais SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| ID de logon da API | `payment_au/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_au/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_au/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_au/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_au/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_au/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Enviar verificação para | `payment_es/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_es/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_es/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_es/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_es/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_es/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_es/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_es/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | | | | | |
| Credenciais SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| ID de logon da API | `payment_nz/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_nz/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_nz/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_nz/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_nz/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave da transação | `payment_nz/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_nz/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave de acesso | `payment_nz/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave secreta | `payment_nz/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_nz/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de resposta de pagamento | `payment_nz/worldpay/response_password` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_nz/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de autorização do administrador remoto | `payment_nz/worldpay/auth_password` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_nz/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensível |
| ID de logon da API | `payment_us/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| Chave da transação | `payment_us/authorizenet_directpost/trans_key` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_us/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_us/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_us/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_us/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave da transação | `payment_us/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_us/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_us/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de resposta de pagamento | `payment_us/worldpay/response_password` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_us/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de autorização do administrador remoto | `payment_us/worldpay/auth_password` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_us/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensível |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Enviar verificação para | `payment_gb/checkmo/mailing_address` |  | | | Sensível |
| ID do comerciante | `payment_gb/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave da transação | `payment_gb/cybersource/transaction_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_gb/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave de acesso | `payment_gb/cybersource/access_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| Chave secreta | `payment_gb/cybersource/secret_key` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID de logon da API | `payment_gb/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| Chave da transação | `payment_gb/authorizenet_directpost/trans_key` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_gb/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_gb/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | Sensível |
| ID da instalação | `payment_gb/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de resposta de pagamento | `payment_gb/worldpay/response_password` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_gb/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Senha de autorização do administrador remoto | `payment_gb/worldpay/auth_password` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_de/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_de/checkmo/mailing_address` |  | | | Sensível |
| ID do comerciante | `payment_de/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_de/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID de logon da API | `payment_de/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_de/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_de/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_de/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID da instalação | `payment_de/worldpay/installation_id` | Somente Commerce Enterprise | | | |
| ID da Instalação do Administrador Remoto | `payment_de/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_de/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensível |
| Credenciais SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_other/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_other/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_other/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_other/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Novo status do pedido | `payment_other/authorizenet_directpost/order_status` |  | | | Sensível |
| Email do comerciante | `payment_other/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_other/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_other/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_other/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_other/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_other/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_ca/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_ca/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_ca/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_ca/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Novo status do pedido | `payment_ca/authorizenet_directpost/order_status` |  | | | Sensível |
| Enviar email para o cliente | `payment_ca/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_ca/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_ca/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_ca/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_ca/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_ca/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_ca/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | Sensível |
| Credenciais SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_hk/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_hk/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_hk/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_hk/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_hk/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_hk/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_hk/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_hk/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_hk/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_hk/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_hk/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Campos de assinatura | `payment_hk/worldpay/signature_fields` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_jp/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_jp/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_jp/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_jp/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_jp/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_jp/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_jp/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_jp/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_jp/worldpay/installation_id` | Somente Commerce Enterprise | | | |
| ID da Instalação do Administrador Remoto | `payment_jp/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_jp/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Campos de assinatura | `payment_jp/worldpay/signature_fields` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_fr/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_fr/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_fr/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_fr/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_fr/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_fr/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_fr/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_fr/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_fr/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_fr/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_fr/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |
| Campos de assinatura | `payment_fr/worldpay/signature_fields` | Somente Commerce Enterprise | | | Sensível |
| Credenciais SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensível |
| Credenciais SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensível |
| Tornar cheque pagável a | `payment_it/checkmo/payable_to` |  | | | Sensível |
| Enviar verificação para | `payment_it/checkmo/mailing_address` |  | | | Sensível |
| ID de logon da API | `payment_it/authorizenet_directpost/login` |  | Criptografado | | Sensível |
| MD5 do comerciante | `payment_it/authorizenet_directpost/trans_md5` |  | Criptografado | | Sensível |
| Enviar email para o cliente | `payment_it/authorizenet_directpost/email_customer` |  | | | Sensível |
| Email do comerciante | `payment_it/authorizenet_directpost/merchant_email` |  | | | Sensível |
| ID do comerciante | `payment_it/cybersource/merchant_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID do perfil | `payment_it/cybersource/profile_id` | Somente Commerce Enterprise | Criptografado | | Sensível |
| ID da instalação | `payment_it/worldpay/installation_id` | Somente Commerce Enterprise | | | Sensível |
| ID da Instalação do Administrador Remoto | `payment_it/worldpay/admin_installation_id` | Somente Commerce Enterprise | | | Sensível |
| Segredo MD5 para Transações | `payment_it/worldpay/md5_secret` | Somente Commerce Enterprise | | | Sensível |

{style="table-layout:auto"}
