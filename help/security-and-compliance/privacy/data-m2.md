---
title: Referência de informações pessoais do cliente (versão 2.x)
description: Saiba mais sobre diagramas de fluxo de dados e mapeamentos de entidade de banco de dados para informações pessoais do cliente no Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Referência de informações pessoais do cliente (versão 2.x)

>[!NOTE]
>
>Este é um tópico de uma série para ajudar os comerciantes e desenvolvedores da Adobe Commerce a se preparar para a conformidade com as regulamentações de privacidade. Consulte seu advogado para determinar se e como sua empresa deve cumprir quaisquer obrigações legais.

Use os seguintes diagramas de fluxo de dados e mapeamentos de entidade de banco de dados para referência ao desenvolver programas de conformidade para regulamentos de privacidade, como:

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## Diagramas de fluxo de dados

Os diagramas de fluxo de dados mostram os tipos de dados que clientes e administradores podem inserir e recuperar da loja e do administrador.

### Pontos de entrada de dados de front-end

Um usuário pode inserir informações de cliente, endereço e pagamento ao se registrar em uma conta, durante a finalização da compra e eventos semelhantes.

![Pontos de entrada de dados de front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Pontos de acesso de dados de front-end

O Adobe Commerce carrega as informações do cliente quando ele faz logon e visualiza várias páginas diferentes ou faz check-out.

![Pontos de acesso de dados de front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Pontos de entrada de dados de back-end

Um comerciante pode especificar informações do cliente, dados de endereço e dados de pagamento ao criar um cliente ou ordem do Administrador.

![Pontos de entrada de dados de back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Pontos de acesso de dados de back-end

O Adobe Commerce carrega informações do cliente quando um comerciante exibe vários tipos de grades, clica em uma grade para ver informações detalhadas e executa várias outras tarefas.

![Pontos de acesso de dados de back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entidades de banco de dados

A Adobe Commerce armazena principalmente informações específicas do cliente em tabelas de clientes, endereços, pedidos, cotas e pagamentos. Outras tabelas contêm referências à ID do cliente.

### Dados do cliente

O Adobe Commerce pode ser configurado para armazenar os seguintes atributos do cliente:

- Data de nascimento
- Email
- Nome
- Sexo
- Sobrenome
- Nome do meio/Inicial
- Prefixo do nome
- Sufixo do nome

>[!NOTE]
>
>Ao manter as práticas recomendadas atuais de segurança e privacidade, esteja ciente de possíveis riscos legais e de segurança associados ao armazenamento da data de nascimento completa do cliente (mês, dia, ano) juntamente com outros identificadores pessoais, como nome completo, antes de coletar ou processar esses dados.

#### `customer_entity` e referências de &quot;customer_entity&quot;

As seguintes colunas na `customer_entity` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | data |
| `gender` | smallint(5) |

Estas tabelas fazem referência a `customer_entity` e podem conter atributos personalizados do cliente:

| Tabela | Coluna | Tipo de dados |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | texto |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` tabela

As seguintes colunas na `customer_grid_flat` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| -------------------- | ------------ |
| `name` | texto |
| `email` | varchar(255) |
| `dob` | data |
| `gender` | int(11) |
| `shipping_full` | texto |
| `billing_full` | texto |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Dados de endereço

O Adobe Commerce armazena os seguintes atributos do cliente:

- Cidade
- Empresa
- País
- Fax
- Nome
- Sobrenome
- Nome do meio/Inicial
- Prefixo do nome
- Sufixo do nome
- Número de telefone
- Estado/Província
- ID de Estado/Província
- Endereço
- Número IVA
- CEP

#### `customer_address_entity` e `customer_address_entity` referências

As seguintes colunas na `customer_address_entity` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | texto |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Estas tabelas fazem referência a `customer_address_entity` e podem conter atributos personalizados do cliente:

| Tabela | Coluna | Tipo de dados |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | texto |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dados do pedido

A variável `sales_order` As tabelas relacionadas contêm o nome do cliente, os endereços de cobrança e de entrega e os dados relacionados.

#### `sales_order` tabela

As seguintes colunas na `sales_order` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` tabela

A variável `sales_order_address` A tabela contém o endereço do cliente.

| Coluna | Tipo de dados |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` tabela

As seguintes colunas na `sales_order_grid` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Dados da cotação

As cotações contêm o nome, email, endereço e informações relacionadas de um cliente.

#### `quote` tabela

As seguintes colunas na `quote` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` tabela

As seguintes colunas na `quote_address` A tabela contém informações do cliente:

| Coluna | Tipo de dados |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Dados de pagamento

A variável `sales_order_payment` A tabela inclui informações de cartão de crédito e outras informações transacionais.

| Coluna | Tipo de dados |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | texto |

### Dados do convite

O Adobe Commerce pode ser configurado para que os clientes possam enviar convites para vendas e eventos privados.

#### `magento_invitation` tabela

A variável `magento_invitation` A tabela contém a ID do cliente, o email e a ID de referência.

| Coluna | Tipo de dados |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` tabela

A variável `magento_invitation_track` A tabela também contém informações do cliente.

| Coluna | Tipo de dados |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Tabelas diversas que fazem referência ao cliente

As tabelas a seguir contêm um `customer_id` coluna:

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
