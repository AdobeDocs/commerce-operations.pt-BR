---
title: Referência de informações pessoais do cliente (versão 1.x)
description: Saiba mais sobre os mapeamentos de entidade de banco de dados e fluxo de dados para informações pessoais do cliente no Magento 1.x.
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Referência de informações pessoais do cliente (versão 1.x)

>[!NOTE]
>
>Este é um tópico de uma série para ajudar os comerciantes e desenvolvedores da Adobe Commerce a se preparar para a conformidade com as regulamentações de privacidade. Consulte seu advogado para determinar se e como sua empresa deve cumprir quaisquer obrigações legais.

Use os seguintes diagramas de fluxo de dados e mapeamentos de entidade de banco de dados para referência ao desenvolver programas de conformidade para regulamentos de privacidade, como:

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## Diagramas de fluxo de dados

Os diagramas de fluxo de dados mostram os tipos de dados que clientes e administradores podem inserir e recuperar na loja e no Administrador.

### Pontos de entrada de dados de front-end

Um usuário pode inserir informações de cliente, endereço e pagamento ao se registrar em uma conta, durante a finalização da compra e eventos semelhantes.

![Pontos de entrada de dados de front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Pontos de acesso de dados de front-end

O Commerce carrega as informações do cliente quando ele faz logon e visualiza várias páginas diferentes ou faz check-out.

![Pontos de acesso de dados de front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Pontos de entrada de dados de back-end

Um comerciante pode especificar informações sobre cliente, endereço e pagamento a partir do Administrador para criar um cliente ou ordem.

![Pontos de entrada de dados back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Pontos de acesso de dados de back-end

O Commerce carrega informações do cliente quando um comerciante exibe vários tipos de grades, clica em uma grade para ver informações detalhadas e executa várias outras tarefas.

![Pontos de acesso a dados de back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entidades de banco de dados

O Magento 1 armazena informações do cliente em tabelas de clientes, vendas e outros bancos de dados.

### Dados do cliente

O Magento 1 armazena informações do cliente nas tabelas `customer_entity` e `customer_address_entity`. Ambas as tabelas têm várias tabelas de referência que podem conter atributos personalizados do cliente.

#### `customer_entity` e tabelas de referência

As seguintes colunas da tabela `customer_entity` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `email` | varchar(255) |

Estas tabelas fazem referência a `customer_entity` e podem conter atributos personalizados do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | texto |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` e tabelas de referência

As tabelas a seguir fazem referência a `customer_address_entity` e podem conter atributos personalizados do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | texto |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dados do pedido

O `sales_flat_order` e as tabelas relacionadas contêm o nome do cliente, os endereços de cobrança e de envio, e as informações relacionadas.

#### Tabela `sales_flat_order`

As seguintes colunas da tabela `sales_order` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### Tabela `sales_flat_order_address`

A tabela `sales_flat_order_address` contém o endereço do cliente.

| Coluna | Tipo de dados |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | texto |

#### Tabela `sales_flat_order_grid`

As seguintes colunas da tabela `sales_flat_order_grid` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### Tabela `sales_flat_order_payment`

As seguintes colunas da tabela `sales_flat_order_payment` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### Dados da cotação

As cotações contêm o nome, email, endereço e informações relacionadas de um cliente.

#### Tabela `sales_flat_quote`

As seguintes colunas da tabela `sales_flat_quote` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### Tabela `sales_flat_quote_address`

As seguintes colunas da tabela `sales_flat_quote_address` contêm informações do cliente:

| Coluna | Tipo de dados |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### Tabela `sales_flat_quote_payment`

A tabela `sales_flat_quote_payment` inclui informações de cartão de crédito e outras informações transacionais.

| Coluna | Tipo de dados |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### Arquivar dados

As tabelas e colunas a seguir contêm informações do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### Dados de vendas

As tabelas e colunas a seguir contêm informações do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### Dados de RMA

As tabelas e colunas de RMA a seguir contêm informações do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### Dados diversos

As tabelas e colunas a seguir contêm informações do cliente:

| Tabela | Coluna | Tipo de dados |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | texto |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | texto |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

Outras tabelas que fazem referência ao Cliente:

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
