---
title: Referência de caminhos de configuração da extensão B2B
description: Consulte uma lista de valores de configuração relacionados a B2B.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Referência de caminhos de configuração da extensão B2B

_Isso está disponível para instâncias com B2B para Adobe Commerce instalado._

Este tópico lista os caminhos de configuração para a Extensão Commerce Enterprise B2B. O [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem.

>[!INFO]
>
>Esta lista de referência _only_ caminhos de configuração exclusivos ao B2B para Adobe Commerce. Essa extensão inclui todos os caminhos de configuração do Adobe Commerce.

Para esses caminhos de configuração, consulte:

- [Caminhos de configuração de pagamento](config-reference-payment.md)
- [Referência de caminhos de configuração sensíveis e específicos do sistema](config-reference-sens.md)

Como opção, para substituir qualquer configuração ou definir configurações confidenciais, consulte [Usar variáveis de ambiente para substituir configurações](override-config-settings.md#environment-variables).

## Categoria geral

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Caminhos de recursos B2B

Esses valores de configuração estão disponíveis no Administrador em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativar empresa | `btob/website_configuration/company_active` |  |  |  |
| Ativar Catálogo Compartilhado | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| Ativar Cotação B2B | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Habilitar Ordem Rápida | `btob/website_configuration/quickorder_active` |  |  |  |
| Ativar Lista de Requisições | `btob/website_configuration/requisition_list_active` |  |  |  |
| Métodos de pagamento aplicáveis | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Métodos de pagamento | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoria Clientes

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Caminhos de configuração da empresa

Esses valores de configuração estão disponíveis no Administrador em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|
| Permitir registro da empresa na loja | `company/general/allow_company_registration` |  |  |  |
| Recipient de email de registro da empresa | `company/email/company_registration` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Registro da Empresa para | `company/email/company_registration_copy` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar método de cópia de email | `company/email/company_copy_method` |  |  |  |
| Email de Registro da Empresa Padrão | `company/email/company_notify_admin_template` |  |  |  |
| Emails relacionados ao cliente | `company/email/heading_customer` |  |  |  |
| Email atribuído do representante de vendas padrão | `company/email/customer_sales_representative_template` |  |  |  |
| Atribuir empresa padrão ao email do cliente | `company/email/customer_company_customer_assign_template` |  |  |  |
| Atribuir Email de Administrador da Empresa Padrão | `company/email/customer_assign_super_user_template` |  |  |  |
| Email inativo do administrador da empresa padrão | `company/email/customer_inactivate_super_user_template` |  |  |  |
| Administrador Padrão Da Empresa Alterado Para Email Do Membro | `company/email/customer_remove_super_user_template` |  |  |  |
| Email Ativo do Status do Cliente Padrão | `company/email/customer_account_activated_template` |  |  |  |
| Email Inativo do Status do Cliente Padrão | `company/email/customer_account_locked_template` |  |  |  |
| Alteração do status da empresa | `company/email/heading_company_status` |  |  |  |
| Recipient de email de alteração de status da empresa | `company/email/company_status_change` |  |  |  |
| Enviar Cópia de Correio Eletrônico para Alteração do Estado da Empresa | `company/email/company_status_change_copy` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar método de cópia de email | `company/email/company_status_copy_method` |  |  |  |
| Alteração Padrão Do Status Da Empresa Para Email Ativo 1 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Alteração Padrão Do Status Da Empresa Para Email Ativo 2 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Alteração Padrão Do Status Da Empresa No Email Rejeitado | `company/email/company_status_rejected_template` |  |  |  |
| Alteração Padrão Do Status Da Empresa Para Email Bloqueado | `company/email/company_status_blocked_template` |  |  |  |
| Alteração Padrão Do Status Da Empresa Para Email De Aprovação Pendente | `company/email/company_status_pending_approval_template` |  |  |  |
| Crédito da Empresa | `company/email/heading_company_credit` |  |  |  |
| Remetente de email de alteração de crédito da empresa | `company/email/company_credit_change` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar Cópia de Email de Alteração de Crédito da Empresa para | `company/email/company_credit_change_copy` |  |  |  |
| Enviar método de cópia de email | `company/email/company_credit_copy_method` |  |  |  |
| Modelo de Email Alocado | `company/email/credit_allocated_email_template` |  |  |  |
| Modelo de email atualizado | `company/email/credit_updated_email_template` |  |  |  |
| Modelo de email reembolsado | `company/email/credit_reimbursed_email_template` |  |  |  |
| Modelo de Email Reembolsado | `company/email/credit_refunded_email_template` |  |  |  |
| Modelo de Email Revertido | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### A solicitação lista caminhos

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Listas de Requisições**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Número de Listas de Requisições | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoria de vendas

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Vendas**.

### Caminhos de Emails de Vendas

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de vendas**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativado | `sales_email/quote/enabled` |  |  |  |
| Modelo de cotação atualizado (para comprador) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Modelo de Cotação Recusada (para Comprador) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Novo Modelo de Cotação (para Vendedor) | `sales_email/quote/new_seller_template` |  |  |  |
| Modelo de Cotação Atualizado (para Vendedor) | `sales_email/quote/updated_seller_template` |  |  |  |
| Expiração da cotação (em 48 horas) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Expiração da cotação (em 24 horas) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Data de Expiração Redefinição | `sales_email/quote/expire_reset_template` |  |  |  |
| Enviar Cópia de Correio Eletrônico da Cotação para | `sales_email/quote/copy_to` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Método de Cópia de Correio Eletrônico Enviar Cotação | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Aspas caminhos

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Aspas**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Valor Mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensagem de Valor Mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de expiração padrão | `quote/general/default_expiration_period` |  |  |  |
| Formatos de arquivo para upload | `quote/attached_files/file_formats` |  |  |  |
| Tamanho máximo do arquivo | `quote/attached_files/maximum_file_size` |  |  |  |
| Valor Mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensagem de Valor Mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de expiração padrão | `quote/general/default_expiration_period` |  |  |  |
| Formatos de arquivo para upload | `quote/attached_files/file_formats` |  |  |  |
| Tamanho máximo do arquivo | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Caminhos do método de pagamento

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de pagamento**.

>[!INFO]
>
>Os caminhos disponíveis são determinados pela escolha do país Merchant.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativado | `payment/au/companycredit/active` |  |  |  |
| Título | `payment/au/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/au/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/au/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/au/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/au/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/au/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/au/companycredit/sort_order` |  |  |  |
| Ativado | `payment/es/companycredit/active` |  |  |  |
| Título | `payment/es/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/es/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/es/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/es/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/es/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/es/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/es/companycredit/sort_order` |  |  |  |
| Ativado | `payment/companycredit/active` |  |  |  |
| Título | `payment/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/companycredit/sort_order` |  |  |  |
| Ativado | `payment/nz/companycredit/active` |  |  |  |
| Título | `payment/nz/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/nz/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/nz/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/nz/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/nz/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/nz/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/nz/companycredit/sort_order` |  |  |  |
| Ativado | `payment/us/companycredit/active` |  |  |  |
| Título | `payment/us/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/us/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/us/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/us/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/us/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/us/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/us/companycredit/sort_order` |  |  |  |
| Ativado | `payment/gb/companycredit/active` |  |  |  |
| Título | `payment/gb/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/gb/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/gb/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/gb/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/gb/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/gb/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/gb/companycredit/sort_order` |  |  |  |
| Ativado | `payment/de/companycredit/active` |  |  |  |
| Título | `payment/de/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/de/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/de/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/de/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/de/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/de/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/de/companycredit/sort_order` |  |  |  |
| Ativado | `payment/other/companycredit/active` |  |  |  |
| Título | `payment/other/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/other/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/other/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/other/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/other/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/other/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/other/companycredit/sort_order` |  |  |  |
| Ativado | `payment/ca/companycredit/active` |  |  |  |
| Título | `payment/ca/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/ca/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/ca/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/ca/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/ca/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/ca/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/ca/companycredit/sort_order` |  |  |  |
| Ativado | `payment/hk/companycredit/active` |  |  |  |
| Título | `payment/hk/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/hk/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/hk/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/hk/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/hk/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/hk/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/hk/companycredit/sort_order` |  |  |  |
| Ativado | `payment/jp/companycredit/active` |  |  |  |
| Título | `payment/jp/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/jp/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/jp/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/jp/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/jp/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/jp/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/jp/companycredit/sort_order` |  |  |  |
| Ativado | `payment/fr/companycredit/active` |  |  |  |
| Título | `payment/fr/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/fr/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/fr/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/fr/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/fr/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/fr/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/fr/companycredit/sort_order` |  |  |  |
| Ativado | `payment/it/companycredit/active` |  |  |  |
| Título | `payment/it/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/it/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/it/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/it/companycredit/specificcountry` |  |  |  |
| Total Mínimo da Ordem | `payment/it/companycredit/min_order_total` |  |  |  |
| Total do Pedido Máximo | `payment/it/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
