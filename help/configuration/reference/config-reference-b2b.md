---
title: Referência de caminhos de configuração da extensão B2B
description: Consulte uma lista de valores de configuração relacionados a B2B.
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Referência de caminhos de configuração da extensão B2B

_Isso está disponível para instâncias com B2B para Adobe Commerce instalado._

Este tópico lista os caminhos de configuração para a extensão B2B do Commerce Enterprise. A variável [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem.

>[!INFO]
>
>Esta referência lista _somente_ caminhos de configuração exclusivos para B2B para Adobe Commerce. Essa extensão inclui todos os caminhos de configuração para o Adobe Commerce.

Para esses caminhos de configuração, consulte:

- [Caminhos de configuração de pagamento](config-reference-payment.md)
- [Referência de caminhos de configuração sensíveis e específicos do sistema](config-reference-sens.md)

Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir as definições de configuração](override-config-settings.md#environment-variables).

## Categoria geral

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para opções no Administrador, em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Caminhos de recursos B2B

Esses valores de configuração estão disponíveis no Admin do **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativar empresa | `btob/website_configuration/company_active` |  |  |  |
| Ativar catálogo compartilhado | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| Ativar cotação B2B | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Habilitar Pedido Rápido | `btob/website_configuration/quickorder_active` |  |  |  |
| Ativar Lista de Requisições | `btob/website_configuration/requisition_list_active` |  |  |  |
| Métodos de pagamento aplicáveis | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Métodos de pagamento | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style="table-layout:auto"}

## Categoria de clientes

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Caminhos de configuração da empresa

Esses valores de configuração estão disponíveis no Admin do **[!UICONTROL Stores]** > Configurações > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
|--------------|--------------|--------------|--------------|--------------|
| Permitir Registro da Empresa pela Loja | `company/general/allow_company_registration` |  |  |  |
| Destinatário do e-mail de registro da empresa | `company/email/company_registration` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia do email de registro da empresa para | `company/email/company_registration_copy` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Método de cópia de email de envio | `company/email/company_copy_method` |  |  |  |
| Email de registro da empresa padrão | `company/email/company_notify_admin_template` |  |  |  |
| Emails relacionados ao cliente | `company/email/heading_customer` |  |  |  |
| E-mail padrão atribuído pelo representante de vendas | `company/email/customer_sales_representative_template` |  |  |  |
| Email padrão de atribuição da empresa ao cliente | `company/email/customer_company_customer_assign_template` |  |  |  |
| Email do administrador da empresa para atribuição padrão | `company/email/customer_assign_super_user_template` |  |  |  |
| Email Inativo do Administrador da Empresa Padrão | `company/email/customer_inactivate_super_user_template` |  |  |  |
| O Administrador Padrão Da Empresa Foi Alterado Para Email Do Membro | `company/email/customer_remove_super_user_template` |  |  |  |
| Email Ativo de Status de Cliente Padrão | `company/email/customer_account_activated_template` |  |  |  |
| Email de Status de Cliente Inativo Padrão | `company/email/customer_account_locked_template` |  |  |  |
| Alteração do status da empresa | `company/email/heading_company_status` |  |  |  |
| Destinatário de Email de Alteração de Status da Empresa | `company/email/company_status_change` |  |  |  |
| Enviar cópia do email de alteração do status da empresa para | `company/email/company_status_change_copy` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Método de cópia de email de envio | `company/email/company_status_copy_method` |  |  |  |
| O Status Padrão Da Empresa Mudou Para O Email 1 Ativo | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Alteração Do Status Da Empresa Padrão Para Email Ativo 2 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Alteração De Status Da Empresa Padrão Para Email Rejeitado | `company/email/company_status_rejected_template` |  |  |  |
| Alteração De Status Padrão Da Empresa Para Email Bloqueado | `company/email/company_status_blocked_template` |  |  |  |
| O Status Padrão Da Empresa Muda Para Email De Aprovação Pendente | `company/email/company_status_pending_approval_template` |  |  |  |
| Crédito da empresa | `company/email/heading_company_credit` |  |  |  |
| Remetente do Email de Alteração de Crédito da Empresa | `company/email/company_credit_change` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Enviar cópia do email de alteração de crédito da empresa para | `company/email/company_credit_change_copy` |  |  |  |
| Método de cópia de email de envio | `company/email/company_credit_copy_method` |  |  |  |
| Modelo de email alocado | `company/email/credit_allocated_email_template` |  |  |  |
| Modelo de e-mail atualizado | `company/email/credit_updated_email_template` |  |  |  |
| Modelo de email reembolsado | `company/email/credit_reimbursed_email_template` |  |  |  |
| Modelo de e-mail reembolsado | `company/email/credit_refunded_email_template` |  |  |  |
| Modelo de e-mail revertido | `company/email/credit_reverted_email_template` |  |  |  |

{style="table-layout:auto"}

### Caminhos de listas de requisição

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Clientes** > **Listas de Requisições**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Número de Listas de Requisições | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style="table-layout:auto"}

## Categoria de vendas

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Vendas**.

### Caminhos de emails de vendas

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de vendas**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativado | `sales_email/quote/enabled` |  |  |  |
| Modelo de Cotação Atualizado (para Comprador) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Modelo de Cotação Recusado (para o Comprador) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Novo Modelo de Cotação (para Vendedor) | `sales_email/quote/new_seller_template` |  |  |  |
| Modelo de Cotação Atualizado (para Vendedor) | `sales_email/quote/updated_seller_template` |  |  |  |
| Expiração da cotação (em 48 horas) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Expiração da cotação (em 24 horas) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Redefinição da data de expiração | `sales_email/quote/expire_reset_template` |  |  |  |
| Enviar cópia de e-mail da cotação para | `sales_email/quote/copy_to` |  |  | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Método de cópia de e-mail para enviar cotação | `sales_email/quote/copy_method` |  |  |  |

{style="table-layout:auto"}

### Caminhos de aspas

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Aspas**.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Valor mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensagem de Valor Mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de expiração padrão | `quote/general/default_expiration_period` |  |  |  |
| Formatos de arquivo para upload | `quote/attached_files/file_formats` |  |  |  |
| Tamanho máximo do arquivo | `quote/attached_files/maximum_file_size` |  |  |  |
| Valor mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensagem de Valor Mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de expiração padrão | `quote/general/default_expiration_period` |  |  |  |
| Formatos de arquivo para upload | `quote/attached_files/file_formats` |  |  |  |
| Tamanho máximo do arquivo | `quote/attached_files/maximum_file_size` |  |  |  |

{style="table-layout:auto"}

## Caminhos do método de pagamento

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de pagamento**.

>[!INFO]
>
>Os caminhos disponíveis são determinados pela sua escolha de país comerciante.

| Nome | Caminho de configuração | Criptografado? | Específico do sistema? | Sensível? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ativado | `payment/au/companycredit/active` |  |  |  |
| Título | `payment/au/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/au/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/au/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/au/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/au/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/au/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/au/companycredit/sort_order` |  |  |  |
| Ativado | `payment/es/companycredit/active` |  |  |  |
| Título | `payment/es/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/es/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/es/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/es/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/es/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/es/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/es/companycredit/sort_order` |  |  |  |
| Ativado | `payment/companycredit/active` |  |  |  |
| Título | `payment/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/companycredit/sort_order` |  |  |  |
| Ativado | `payment/nz/companycredit/active` |  |  |  |
| Título | `payment/nz/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/nz/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/nz/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/nz/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/nz/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/nz/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/nz/companycredit/sort_order` |  |  |  |
| Ativado | `payment/us/companycredit/active` |  |  |  |
| Título | `payment/us/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/us/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/us/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/us/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/us/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/us/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/us/companycredit/sort_order` |  |  |  |
| Ativado | `payment/gb/companycredit/active` |  |  |  |
| Título | `payment/gb/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/gb/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/gb/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/gb/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/gb/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/gb/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/gb/companycredit/sort_order` |  |  |  |
| Ativado | `payment/de/companycredit/active` |  |  |  |
| Título | `payment/de/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/de/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/de/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/de/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/de/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/de/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/de/companycredit/sort_order` |  |  |  |
| Ativado | `payment/other/companycredit/active` |  |  |  |
| Título | `payment/other/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/other/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/other/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/other/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/other/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/other/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/other/companycredit/sort_order` |  |  |  |
| Ativado | `payment/ca/companycredit/active` |  |  |  |
| Título | `payment/ca/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/ca/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/ca/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/ca/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/ca/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/ca/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/ca/companycredit/sort_order` |  |  |  |
| Ativado | `payment/hk/companycredit/active` |  |  |  |
| Título | `payment/hk/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/hk/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/hk/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/hk/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/hk/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/hk/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/hk/companycredit/sort_order` |  |  |  |
| Ativado | `payment/jp/companycredit/active` |  |  |  |
| Título | `payment/jp/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/jp/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/jp/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/jp/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/jp/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/jp/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/jp/companycredit/sort_order` |  |  |  |
| Ativado | `payment/fr/companycredit/active` |  |  |  |
| Título | `payment/fr/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/fr/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/fr/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/fr/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/fr/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/fr/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/fr/companycredit/sort_order` |  |  |  |
| Ativado | `payment/it/companycredit/active` |  |  |  |
| Título | `payment/it/companycredit/title` |  |  |  |
| Novo status do pedido | `payment/it/companycredit/order_status` |  |  |  |
| Pagamento dos países aplicáveis | `payment/it/companycredit/allowspecific` |  |  |  |
| Pagamento de países específicos | `payment/it/companycredit/specificcountry` |  |  |  |
| Total mínimo de pedidos | `payment/it/companycredit/min_order_total` |  |  |  |
| Total máximo de pedidos | `payment/it/companycredit/max_order_total` |  |  |  |
| Ordem de classificação | `payment/it/companycredit/sort_order` |  |  |  |

{style="table-layout:auto"}
