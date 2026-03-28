---
title: Referência de caminhos de configuração de pagamento
description: Saiba mais sobre caminhos de configuração de pagamento e valores de método no Adobe Commerce Admin. Descubra as opções de configuração do PayPal, cartão de crédito e gateway de pagamento.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# Referência de caminhos de configuração de pagamento

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de Pagamento**.

O comando [`magento app:config:dump` ](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir definições de configuração](override-config-settings.md#environment-variables). Este tópico _Alerta_ lista [valores confidenciais e específicos do sistema](config-reference-sens.md).

As configurações são organizadas ainda mais por método de pagamento.

## Caminhos do PayPal

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativar esta solução | `payment/payflowpro/active` | Todos |
| Habilitar experiência de check-out no contexto | `payment/paypal_express/in_context` | Todos |
| Habilitar Crédito do PayPal | `payment/payflow_express_bml/active` | Todos |
| Habilitar Crédito do PayPal | `payment/paypal_express_bml/active` | Todos |
| Exibir | `payment/paypal_express_bml/homepage_display` | Todos |
| Position | `payment/paypal_express_bml/homepage_position` | Todos |
| Tamanho | `payment/paypal_express_bml/homepage_size` | Todos |
| Exibir | `payment/paypal_express_bml/categorypage_display` | Todos |
| Position | `payment/paypal_express_bml/categorypage_position` | Todos |
| Tamanho | `payment/paypal_express_bml/categorypage_size` | Todos |
| Exibir | `payment/paypal_express_bml/productpage_display` | Todos |
| Position | `payment/paypal_express_bml/productpage_position` | Todos |
| Tamanho | `payment/paypal_express_bml/productpage_size` | Todos |
| Exibir | `payment/paypal_express_bml/checkout_display` | Todos |
| Position | `payment/paypal_express_bml/checkout_position` | Todos |
| Tamanho | `payment/paypal_express_bml/checkout_size` | Todos |
| Exibir na página de detalhes do produto | `payment/payflow_express/visible_on_product` | Todos |
| Exibir no carrinho de compras | `payment/payflow_express/visible_on_cart` | Todos |
| Pagamento Aplicável a Partir de | `payment/payflow_express/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/payflow_express/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/payflow_express/verify_peer` | Todos |
| Transferir itens de linha do carrinho | `payment/payflow_express/line_items_enabled` | Todos |
| Etapa de revisão do pedido ignorado | `payment/paypal_express/skip_order_review_step` | Todos |
| Transferir itens de linha do carrinho | `payment/paypal_express/line_items_enabled` | Todos |
| Opções de envio de transferência | `payment/paypal_express/transfer_shipping_options` | Todos |
| Tipo de Botões de Atalho | `paypal/wpp/button_flavor` | Todos |
| Habilitar Check-out de Convidado do PayPal | `payment/paypal_express/solution_type` | Todos |
| Exigir endereço de cobrança do cliente | `payment/paypal_express/require_billing_address` | Todos |
| Assinatura do Contrato de Cobrança | `payment/paypal_express/allow_ba_signup` | Todos |
| Ativado | `payment/paypal_billing_agreement/active` | Todos |
| Título | `payment/paypal_billing_agreement/title` | Todos |
| Ordem de classificação | `payment/paypal_billing_agreement/sort_order` | Todos |
| Ação de pagamento | `payment/paypal_billing_agreement/payment_action` | Todos |
| Pagamento Aplicável a Partir de | `payment/paypal_billing_agreement/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/paypal_billing_agreement/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/paypal_billing_agreement/verify_peer` | Todos |
| Transferir itens de linha do carrinho | `payment/paypal_billing_agreement/line_items_enabled` | Todos |
| Permitir no Assistente de Contrato de Cobrança | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | Todos |
| Ativar busca automática | `paypal/fetch_reports/active` | Todos |
| Cronograma | `paypal/fetch_reports/schedule` | Todos |
| Hora do dia | `paypal/fetch_reports/time` | Todos |
| Logotipo do produto PayPal | `paypal/style/logo` | Todos |
| Estilo de página | `paypal/style/page_style` | Todos |
| URL da imagem do cabeçalho | `paypal/style/paypal_hdrimg` | Todos |
| Cor do plano de fundo do cabeçalho | `paypal/style/paypal_hdrbackcolor` | Todos |
| Cor da borda do cabeçalho | `paypal/style/paypal_hdrbordercolor` | Todos |
| Cor do plano de fundo da página | `paypal/style/paypal_payflowcolor` | Todos |
| Ativar esta solução | `payment/paypal_express/active` | Todos |
| Ordem de classificação Crédito do PayPal | `payment/paypal_express_bml/sort_order` | Todos |
| Título | `payment/paypal_express/title` | Todos |
| Ordem de classificação | `payment/paypal_express/sort_order` | Todos |
| Ação de pagamento | `payment/paypal_express/payment_action` | Todos |
| Exibir na página de detalhes do produto | `payment/paypal_express/visible_on_product` | Todos |
| Período de Alerta de Autorização (dias) | `payment/paypal_express/authorization_hoAllr_period` | Todos |
| Período válido do pedido (dias) | `payment/paypal_express/order_valid_period` | Todos |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | Todos |
| Exibir no carrinho de compras | `payment/paypal_express/visible_on_cart` | Todos |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | Todos |
| Pagamento Aplicável a Partir de | `payment/paypal_express/allowspecific` | Todos |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/paypal_express/specificcountry` | Todos |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | Todos |
| Habilitar verificação SSL | `payment/paypal_express/verify_peer` | Todos |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | Todos |
| Busca programada | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |

{style="table-layout:auto"}

## PayPal Payments Pro

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Métodos de autenticação de API | `paypal/wpp/api_authentication` | Todos |
| API usa proxy | `paypal/wpp/use_proxy` | Todos |
| Busca programada | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Reino Unido)

Estas opções só estarão disponíveis se você escolher o Reino Unido como [país comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativar esta solução | `payment/hosted_pro/active` | Todos |
| Título | `payment/hosted_pro/title` | Todos |
| Ordem de classificação | `payment/hosted_pro/sort_order` | Todos |
| Ação de pagamento | `payment/hosted_pro/payment_action` | Todos |
| Exibir Finalização Expressa na etapa Informações de Pagamento | `payment/hosted_pro/display_ec` | Todos |
| Pagamento Aplicável a Partir de | `payment/hosted_pro/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/hosted_pro/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/hosted_pro/verify_peer` | Todos |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Cofre Habilitado | `payment/payflowpro_cc_vault/active` | Todos |
| Título | `payment/payflowpro/title` | Todos |
| Título do Vault | `payment/payflowpro_cc_vault/title` | Todos |
| Ordem de classificação | `payment/payflowpro/sort_order` | Todos |
| Ação de pagamento | `payment/payflowpro/payment_action` | Todos |
| Tipos de cartão de crédito permitidos | `payment/payflowpro/cctypes` | Todos |
| Pagamento Aplicável a Partir de | `payment/payflowpro/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/payflowpro/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/payflowpro/verify_peer` | Todos |
| Exigir entrada de CVV | `payment/payflowpro/useccv` | Todos |
| Rejeitar Transação se: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Rua AVS Corresponde a Alerta | `payment/payflowpro/avs_street` | Todos |
| O CEP AVS não corresponde | `payment/payflowpro/avs_zip` | Todos |
| Indicador AVS Internacional Corresponde | `payment/payflowpro/avs_international` | Todos |
| O código de segurança do cartão não corresponde | `payment/payflowpro/avs_security_code` | Todos |
| Fornecedor | `payment/payflowpro/vendor` | Todos |
| Usar proxy | `payment/payflowpro/use_proxy` | Todos |
| Título | `payment/payflow_express/title` | Todos |
| Ordem de classificação | `payment/payflow_express/sort_order` | Todos |
| Ação de pagamento | `payment/payflow_express/payment_action` | Todos |
| Busca programada | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todos |
| Parceiro | `payment/payflow_advanced/partner` | Todos |
| Fornecedor | `payment/payflow_advanced/vendor` | Todos |
| Usar proxy | `payment/payflow_advanced/use_proxy` | Todos |
| Ativar esta solução | `payment/payflow_advanced/active` | Todos |
| Título | `payment/payflow_advanced/title` | Todos |
| Ordem de classificação | `payment/payflow_advanced/sort_order` | Todos |
| Ação de pagamento | `payment/payflow_advanced/payment_action` | Todos |
| Pagamento Aplicável a Partir de | `payment/payflow_advanced/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/payflow_advanced/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/payflow_advanced/verify_peer` | Todos |
| A entrada do CVV é editável | `payment/payflow_advanced/csc_editable` | Todos |
| Exigir entrada de CVV | `payment/payflow_advanced/csc_required` | Todos |
| Enviar confirmação de email | `payment/payflow_advanced/email_confirmation` | Todos |

{style="table-layout:auto"}

## Link do fluxo de pagamento do PayPal

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Parceiro | `payment/payflow_link/partner` | Todos |
| Fornecedor | `payment/payflow_link/vendor` | Todos |
| Habilitar Link de Fluxo de Pagamento | `payment/payflow_link/active` | Todos |
| Habilitar Check-out Expresso | `payment/payflow_express/active` | Todos |
| Ordem de classificação Crédito do PayPal | `payment/payflow_express_bml/sort_order` | Todos |
| Pagamento Aplicável a Partir de | `payment/payflow_link/allowspecific` | Todos |
| Países Pagamento Aplicável a Partir de | `payment/payflow_link/specificcountry` | Todos |
| Habilitar verificação SSL | `payment/payflow_link/verify_peer` | Todos |
| A entrada do CVV é editável | `payment/payflow_link/csc_editable` | Todos |
| Exigir entrada de CVV | `payment/payflow_link/csc_required` | Todos |
| Enviar confirmação de email | `payment/payflow_link/email_confirmation` | Todos |
| Busca programada | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todos |
| Título | `payment/payflow_link/title` | Todos |
| Ordem de classificação | `payment/payflow_link/sort_order` | Todos |
| Ação de pagamento | `payment/payflow_link/payment_action` | Todos |

{style="table-layout:auto"}

## Caminhos de check-out com subtotal zero

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativado | `payment/free/active` | Todos |
| Título | `payment/free/title` | Todos |
| Novo status do pedido | `payment/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment/free/specificcountry` | Todos |
| Ordem de classificação | `payment/free/sort_order` | Todos |

{style="table-layout:auto"}

## Caminhos de pagamento de caixa na entrega

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativado | `payment/cashondelivery/active` | Todos |
| Título | `payment/cashondelivery/title` | Todos |
| Novo status do pedido | `payment/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment/cashondelivery/specificcountry` | Todos |
| Instruções | `payment/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment/cashondelivery/sort_order` | Todos |

{style="table-layout:auto"}

## Caminhos de Pagamento de Transferência Bancária

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativado | `payment/banktransfer/active` | Todos |
| Título | `payment/banktransfer/title` | Todos |
| Novo status do pedido | `payment/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment/banktransfer/specificcountry` | Todos |
| Instruções | `payment/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment/banktransfer/sort_order` | Todos |

{style="table-layout:auto"}

## Caminhos de Cheque ou Ordem de Pagamento

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativado | `payment/checkmo/active` | Todos |
| Título | `payment/checkmo/title` | Todos |
| Novo status do pedido | `payment/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment/checkmo/payable_to` | Todos |
| Total mínimo de pedidos | `payment/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment/checkmo/sort_order` | Todos |

{style="table-layout:auto"}

## Caminhos da Ordem de Compra

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Ativado | `payment/purchaseorder/active` | Todos |
| Título | `payment/purchaseorder/title` | Todos |
| Novo status do pedido | `payment/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment/purchaseorder/sort_order` | Todos |

{style="table-layout:auto"}

## Caminhos internacionais

>[!INFO]
>
>Os caminhos disponíveis são determinados pela sua escolha de [País do comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Caminho de configuração | Suporte à versão do Commerce? |
|--------------|--------------|--------------|
| Credenciais SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | Todos |
| Busca programada | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativar esta solução | `payment/wps_express/active` | Todos |
| Busca programada | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Configurações de cartão de crédito | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Ativado | `payment_nz/free/active` | Todos |
| Título | `payment_nz/free/title` | Todos |
| Novo status do pedido | `payment_nz/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_nz/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/free/specificcountry` | Todos |
| Ordem de classificação | `payment_nz/free/sort_order` | Todos |
| Ativado | `payment_nz/cashondelivery/active` | Todos |
| Título | `payment_nz/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_nz/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_nz/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_nz/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_nz/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_nz/cashondelivery/sort_order` | Todos |
| Ativado | `payment_nz/banktransfer/active` | Todos |
| Título | `payment_nz/banktransfer/title` | Todos |
| Novo status do pedido | `payment_nz/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/banktransfer/specificcountry` | Todos |
| Instruções | `payment_nz/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_nz/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_nz/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_nz/banktransfer/sort_order` | Todos |
| Ativado | `payment_nz/checkmo/active` | Todos |
| Título | `payment_nz/checkmo/title` | Todos |
| Novo status do pedido | `payment_nz/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment_nz/checkmo/payable_to` | Todos |
| Enviar verificação para | `payment_nz/checkmo/mailing_address` | Todos |
| Total mínimo de pedidos | `payment_nz/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_nz/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_nz/checkmo/sort_order` | Todos |
| Ativado | `payment_nz/purchaseorder/active` | Todos |
| Título | `payment_nz/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_nz/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_nz/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_nz/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_nz/purchaseorder/sort_order` | Todos |
| Ativado | `payment_nz/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_nz/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_nz/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_nz/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_nz/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_nz/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_nz/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_nz/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_nz/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_nz/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_nz/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_nz/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_nz/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_nz/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_nz/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_nz/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_nz/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_nz/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_nz/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_nz/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_nz/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_nz/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_nz/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_nz/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_nz/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_nz/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_nz/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_nz/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_nz/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_nz/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_nz/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_nz/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_nz/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_nz/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_nz/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_nz/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_nz/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_nz/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_nz/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_nz/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_nz/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_nz/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_nz/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_nz/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_nz/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_nz/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_hk/free/active` | Todos |
| Título | `payment_hk/free/title` | Todos |
| Novo status do pedido | `payment_hk/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_hk/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/free/specificcountry` | Todos |
| Ordem de classificação | `payment_hk/free/sort_order` | Todos |
| Ativado | `payment_hk/cashondelivery/active` | Todos |
| Título | `payment_hk/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_hk/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_hk/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_hk/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_hk/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_hk/cashondelivery/sort_order` | Todos |
| Ativado | `payment_hk/banktransfer/active` | Todos |
| Título | `payment_hk/banktransfer/title` | Todos |
| Novo status do pedido | `payment_hk/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/banktransfer/specificcountry` | Todos |
| Instruções | `payment_hk/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_hk/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_hk/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_hk/banktransfer/sort_order` | Todos |
| Ativado | `payment_hk/checkmo/active` | Todos |
| Título | `payment_hk/checkmo/title` | Todos |
| Novo status do pedido | `payment_hk/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_hk/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_hk/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_hk/checkmo/sort_order` | Todos |
| Ativado | `payment_hk/purchaseorder/active` | Todos |
| Título | `payment_hk/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_hk/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_hk/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_hk/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_hk/purchaseorder/sort_order` | Todos |
| Ativado | `payment_hk/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_hk/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_hk/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_hk/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_hk/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_hk/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_hk/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_hk/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_hk/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_hk/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_hk/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_hk/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_hk/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_hk/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_hk/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_hk/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_hk/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_hk/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_hk/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_hk/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_hk/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_hk/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_hk/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_hk/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_hk/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_hk/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_hk/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_hk/worldpay/hide_contact` | Somente Commerce Enterprise |
| Depurar | `payment_hk/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_hk/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_hk/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_hk/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_hk/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_hk/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_hk/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_hk/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_hk/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_hk/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_hk/eway/title` | Somente Commerce Enterprise |
| Modo de sandbox | `payment_hk/eway/sandbox_flag` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_hk/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_hk/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_hk/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_hk/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_hk/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_hk/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_es/free/active` | Todos |
| Título | `payment_es/free/title` | Todos |
| Novo status do pedido | `payment_es/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_es/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_es/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/free/specificcountry` | Todos |
| Ordem de classificação | `payment_es/free/sort_order` | Todos |
| Ativado | `payment_es/cashondelivery/active` | Todos |
| Título | `payment_es/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_es/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_es/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_es/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_es/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_es/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_es/cashondelivery/sort_order` | Todos |
| Ativado | `payment_es/banktransfer/active` | Todos |
| Título | `payment_es/banktransfer/title` | Todos |
| Novo status do pedido | `payment_es/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_es/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/banktransfer/specificcountry` | Todos |
| Instruções | `payment_es/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_es/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_es/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_es/banktransfer/sort_order` | Todos |
| Ativado | `payment_es/checkmo/active` | Todos |
| Título | `payment_es/checkmo/title` | Todos |
| Novo status do pedido | `payment_es/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_es/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment_es/checkmo/payable_to` | Todos |
| Total mínimo de pedidos | `payment_es/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_es/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_es/checkmo/sort_order` | Todos |
| Ativado | `payment_es/purchaseorder/active` | Todos |
| Título | `payment_es/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_es/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_es/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_es/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_es/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_es/purchaseorder/sort_order` | Todos |
| Ativado | `payment_es/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_es/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_es/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_es/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_es/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_es/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_es/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_es/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_es/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_es/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_es/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_es/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_es/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_es/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_es/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_es/cybersource/title` | Somente Commerce Enterprise |
| ID do perfil | `payment_es/cybersource/profile_id` | Somente Commerce Enterprise\| ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| Novo status do pedido | `payment_es/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_es/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_es/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_es/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_es/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_es/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_es/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_es/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_es/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_es/worldpay/title` | Somente Commerce Enterprise |
| ID da instalação | `payment_es/worldpay/installation_id` | Somente Commerce Enterprise |
| ID da Instalação do Administrador Remoto | `payment_es/worldpay/admin_installation_id` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_es/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_es/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_es/worldpay/signature_fields` | Somente Commerce Enterprise |
| Modo de teste | `payment_es/worldpay/sandbox_flag` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_es/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_es/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_es/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_es/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_es/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_es/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_es/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_es/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_es/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_es/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_es/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_es/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_es/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_es/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_es/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_es/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_it/free/active` | Todos |
| Título | `payment_it/free/title` | Todos |
| Novo status do pedido | `payment_it/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_it/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_it/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/free/specificcountry` | Todos |
| Ordem de classificação | `payment_it/free/sort_order` | Todos |
| Ativado | `payment_it/cashondelivery/active` | Todos |
| Título | `payment_it/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_it/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_it/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_it/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_it/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_it/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_it/cashondelivery/sort_order` | Todos |
| Ativado | `payment_it/banktransfer/active` | Todos |
| Título | `payment_it/banktransfer/title` | Todos |
| Novo status do pedido | `payment_it/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_it/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/banktransfer/specificcountry` | Todos |
| Instruções | `payment_it/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_it/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_it/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_it/banktransfer/sort_order` | Todos |
| Ativado | `payment_it/checkmo/active` | Todos |
| Título | `payment_it/checkmo/title` | Todos |
| Novo status do pedido | `payment_it/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_it/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_it/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_it/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_it/checkmo/sort_order` | Todos |
| Ativado | `payment_it/purchaseorder/active` | Todos |
| Título | `payment_it/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_it/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_it/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_it/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_it/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_it/purchaseorder/sort_order` | Todos |
| Ativado | `payment_it/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_it/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_it/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_it/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_it/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_it/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_it/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_it/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_it/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_it/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_it/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_it/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_it/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_it/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_it/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_it/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_it/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_it/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_it/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_it/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_it/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_it/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_it/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_it/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_it/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_it/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_it/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_it/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_it/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_it/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_it/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_it/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_it/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_it/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_it/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_it/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_it/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_it/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_it/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_it/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_it/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_it/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_it/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_it/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_it/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_it/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_fr/free/active` | Todos |
| Título | `payment_fr/free/title` | Todos |
| Novo status do pedido | `payment_fr/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_fr/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/free/specificcountry` | Todos |
| Ordem de classificação | `payment_fr/free/sort_order` | Todos |
| Ativado | `payment_fr/cashondelivery/active` | Todos |
| Título | `payment_fr/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_fr/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_fr/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_fr/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_fr/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_fr/cashondelivery/sort_order` | Todos |
| Ativado | `payment_fr/banktransfer/active` | Todos |
| Título | `payment_fr/banktransfer/title` | Todos |
| Novo status do pedido | `payment_fr/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/banktransfer/specificcountry` | Todos |
| Instruções | `payment_fr/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_fr/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_fr/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_fr/banktransfer/sort_order` | Todos |
| Ativado | `payment_fr/checkmo/active` | Todos |
| Título | `payment_fr/checkmo/title` | Todos |
| Novo status do pedido | `payment_fr/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_fr/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_fr/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_fr/checkmo/sort_order` | Todos |
| Ativado | `payment_fr/purchaseorder/active` | Todos |
| Título | `payment_fr/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_fr/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_fr/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_fr/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_fr/purchaseorder/sort_order` | Todos |
| Ativado | `payment_fr/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_fr/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_fr/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_fr/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_fr/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_fr/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_fr/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_fr/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_fr/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_fr/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_fr/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_fr/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_fr/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_fr/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_fr/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_fr/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_fr/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_fr/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_fr/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_fr/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_fr/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_fr/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_fr/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_fr/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_fr/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_fr/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_fr/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_fr/worldpay/hide_contact` | Somente Commerce Enterprise |
| Depurar | `payment_fr/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_fr/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_fr/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_fr/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_fr/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_fr/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_fr/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_fr/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_fr/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_fr/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_fr/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_fr/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_fr/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_fr/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_fr/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_fr/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_fr/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_jp/free/active` | Todos |
| Título | `payment_jp/free/title` | Todos |
| Novo status do pedido | `payment_jp/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_jp/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/free/specificcountry` | Todos |
| Ordem de classificação | `payment_jp/free/sort_order` | Todos |
| Ativado | `payment_jp/cashondelivery/active` | Todos |
| Título | `payment_jp/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_jp/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_jp/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_jp/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_jp/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_jp/cashondelivery/sort_order` | Todos |
| Ativado | `payment_jp/banktransfer/active` | Todos |
| Título | `payment_jp/banktransfer/title` | Todos |
| Novo status do pedido | `payment_jp/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/banktransfer/specificcountry` | Todos |
| Instruções | `payment_jp/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_jp/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_jp/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_jp/banktransfer/sort_order` | Todos |
| Ativado | `payment_jp/checkmo/active` | Todos |
| Título | `payment_jp/checkmo/title` | Todos |
| Novo status do pedido | `payment_jp/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_jp/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_jp/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_jp/checkmo/sort_order` | Todos |
| Ativado | `payment_jp/purchaseorder/active` | Todos |
| Título | `payment_jp/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_jp/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_jp/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_jp/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_jp/purchaseorder/sort_order` | Todos |
| Ativado | `payment_jp/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_jp/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_jp/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_jp/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_jp/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_jp/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_jp/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_jp/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_jp/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_jp/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_jp/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_jp/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_jp/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_jp/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_jp/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_jp/cybersource/title` | Somente Commerce Enterprise |
| Depurar | `payment_jp/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_jp/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_jp/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_jp/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_jp/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_jp/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_jp/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_jp/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_jp/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_jp/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_jp/worldpay/hide_contact` | Somente Commerce Enterprise |
| Depurar | `payment_jp/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_jp/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_jp/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_jp/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_jp/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_jp/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_jp/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_jp/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_jp/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_jp/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_jp/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_jp/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_jp/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_jp/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_jp/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_jp/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_jp/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Configurações de cartão de crédito | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Ativado | `payment_au/free/active` | Todos |
| Título | `payment_au/free/title` | Todos |
| Novo status do pedido | `payment_au/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_au/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_au/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/free/specificcountry` | Todos |
| Ordem de classificação | `payment_au/free/sort_order` | Todos |
| Ativado | `payment_au/cashondelivery/active` | Todos |
| Título | `payment_au/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_au/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_au/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_au/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_au/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_au/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_au/cashondelivery/sort_order` | Todos |
| Ativado | `payment_au/banktransfer/active` | Todos |
| Título | `payment_au/banktransfer/title` | Todos |
| Novo status do pedido | `payment_au/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_au/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/banktransfer/specificcountry` | Todos |
| Instruções | `payment_au/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_au/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_au/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_au/banktransfer/sort_order` | Todos |
| Ativado | `payment_au/checkmo/active` | Todos |
| Título | `payment_au/checkmo/title` | Todos |
| Novo status do pedido | `payment_au/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_au/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment_au/checkmo/payable_to` | Todos |
| Enviar verificação para | `payment_au/checkmo/mailing_address` | Todos |
| Total mínimo de pedidos | `payment_au/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_au/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_au/checkmo/sort_order` | Todos |
| Ativado | `payment_au/purchaseorder/active` | Todos |
| Título | `payment_au/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_au/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_au/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_au/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_au/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_au/purchaseorder/sort_order` | Todos |
| Ativado | `payment_au/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_au/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_au/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_au/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_au/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_au/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_au/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_au/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_au/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_au/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_au/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_au/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_au/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_au/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_au/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_au/cybersource/title` | Somente Commerce Enterprise |
| ID do comerciante | `payment_au/cybersource/merchant_id` | Somente Commerce Enterprise \| ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| ID do perfil | `payment_au/cybersource/profile_id` | Somente Commerce Enterprise \| ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| Novo status do pedido | `payment_au/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_au/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_au/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_au/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_au/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_au/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_au/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_au/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_au/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_au/worldpay/title` | Somente Commerce Enterprise |
| ID da instalação | `payment_au/worldpay/installation_id` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_au/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_au/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_au/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_au/worldpay/debug` | Somente Commerce Enterprise |
| Modo de teste | `payment_au/worldpay/sandbox_flag` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_au/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_au/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_au/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_au/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_au/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_au/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_au/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_au/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_au/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_au/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_au/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_au/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_au/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_au/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_au/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_au/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativar esta solução | `payment/paypal_payment_pro/active` | Todos |
| Configurações de cartão de crédito | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Configurações de cartão de crédito | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Busca programada | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todos |
| Ativado | `payment_ca/free/active` | Todos |
| Título | `payment_ca/free/title` | Todos |
| Novo status do pedido | `payment_ca/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_ca/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/free/specificcountry` | Todos |
| Ordem de classificação | `payment_ca/free/sort_order` | Todos |
| Ativado | `payment_ca/cashondelivery/active` | Todos |
| Título | `payment_ca/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_ca/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_ca/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_ca/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_ca/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_ca/cashondelivery/sort_order` | Todos |
| Ativado | `payment_ca/banktransfer/active` | Todos |
| Título | `payment_ca/banktransfer/title` | Todos |
| Novo status do pedido | `payment_ca/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/banktransfer/specificcountry` | Todos |
| Instruções | `payment_ca/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_ca/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_ca/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_ca/banktransfer/sort_order` | Todos |
| Ativado | `payment_ca/checkmo/active` | Todos |
| Título | `payment_ca/checkmo/title` | Todos |
| Novo status do pedido | `payment_ca/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_ca/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_ca/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_ca/checkmo/sort_order` | Todos |
| Ativado | `payment_ca/purchaseorder/active` | Todos |
| Título | `payment_ca/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_ca/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_ca/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_ca/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_ca/purchaseorder/sort_order` | Todos |
| Ativado | `payment_ca/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_ca/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_ca/authorizenet_directpost/title` | Todos |
| Moeda aceita | `payment_ca/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_ca/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_ca/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_ca/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_ca/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_ca/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_ca/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_ca/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_ca/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_ca/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_ca/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_ca/cybersource/title` | Somente Commerce Enterprise |
| Depurar | `payment_ca/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_ca/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_ca/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_ca/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_ca/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_ca/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_ca/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_ca/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_ca/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_ca/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_ca/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_ca/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_ca/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_ca/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_ca/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_ca/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_ca/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_ca/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_ca/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_ca/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_ca/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_ca/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_ca/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_ca/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_ca/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_ca/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_ca/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_ca/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_ca/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_other/free/active` | Todos |
| Título | `payment_other/free/title` | Todos |
| Novo status do pedido | `payment_other/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_other/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_other/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/free/specificcountry` | Todos |
| Ordem de classificação | `payment_other/free/sort_order` | Todos |
| Ativado | `payment_other/cashondelivery/active` | Todos |
| Título | `payment_other/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_other/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_other/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_other/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_other/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_other/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_other/cashondelivery/sort_order` | Todos |
| Ativado | `payment_other/banktransfer/active` | Todos |
| Título | `payment_other/banktransfer/title` | Todos |
| Novo status do pedido | `payment_other/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_other/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/banktransfer/specificcountry` | Todos |
| Instruções | `payment_other/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_other/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_other/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_other/banktransfer/sort_order` | Todos |
| Ativado | `payment_other/checkmo/active` | Todos |
| Título | `payment_other/checkmo/title` | Todos |
| Novo status do pedido | `payment_other/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_other/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_other/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_other/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_other/checkmo/sort_order` | Todos |
| Ativado | `payment_other/purchaseorder/active` | Todos |
| Título | `payment_other/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_other/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_other/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_other/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_other/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_other/purchaseorder/sort_order` | Todos |
| Ativado | `payment_other/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_other/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_other/authorizenet_directpost/title` | Todos |
| Moeda aceita | `payment_other/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_other/authorizenet_directpost/debug` | Todos |
| Enviar email para o cliente | `payment_other/authorizenet_directpost/email_customer` | Todos |
| Tipos de cartão de crédito | `payment_other/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_other/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_other/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_other/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_other/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_other/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_other/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_other/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_other/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_other/cybersource/title` | Somente Commerce Enterprise |
| Depurar | `payment_other/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_other/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_other/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_other/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_other/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_other/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_other/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_other/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_other/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_other/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_other/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_other/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_other/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_other/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_other/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_other/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_other/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_other/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_other/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_other/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_other/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_other/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_other/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_other/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_other/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_other/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_other/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_other/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_other/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_de/checkmo/active` | Todos |
| Título | `payment_de/checkmo/title` | Todos |
| Novo status do pedido | `payment_de/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_de/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/checkmo/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_de/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_de/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_de/checkmo/sort_order` | Todos |
| Ativado | `payment_de/banktransfer/active` | Todos |
| Título | `payment_de/banktransfer/title` | Todos |
| Novo status do pedido | `payment_de/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_de/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/banktransfer/specificcountry` | Todos |
| Instruções | `payment_de/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_de/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_de/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_de/banktransfer/sort_order` | Todos |
| Ativado | `payment_de/cashondelivery/active` | Todos |
| Título | `payment_de/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_de/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_de/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_de/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_de/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_de/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_de/cashondelivery/sort_order` | Todos |
| Ativado | `payment_de/free/active` | Todos |
| Título | `payment_de/free/title` | Todos |
| Novo status do pedido | `payment_de/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_de/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_de/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/free/specificcountry` | Todos |
| Ordem de classificação | `payment_de/free/sort_order` | Todos |
| Ativado | `payment_de/purchaseorder/active` | Todos |
| Título | `payment_de/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_de/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_de/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_de/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_de/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_de/purchaseorder/sort_order` | Todos |
| Ativado | `payment_de/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_de/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_de/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_de/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_de/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_de/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_de/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_de/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_de/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_de/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_de/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_de/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_de/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_de/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_de/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_de/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_de/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_de/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_de/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_de/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_de/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_de/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_de/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_de/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_de/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_de/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_de/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_de/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_de/worldpay/signature_fields` | Somente Commerce Enterprise |
| Modo de teste | `payment_de/worldpay/sandbox_flag` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_de/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_de/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_de/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_de/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_de/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_de/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_de/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_de/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_de/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_de/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_de/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_de/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_de/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_de/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_de/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_de/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | Todos |
| Busca programada | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Ativado | `payment_gb/checkmo/active` | Todos |
| Título | `payment_gb/checkmo/title` | Todos |
| Novo status do pedido | `payment_gb/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment_gb/checkmo/payable_to` | Todos |
| Total mínimo de pedidos | `payment_gb/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_gb/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_gb/checkmo/sort_order` | Todos |
| Ativado | `payment_gb/banktransfer/active` | Todos |
| Título | `payment_gb/banktransfer/title` | Todos |
| Novo status do pedido | `payment_gb/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/banktransfer/specificcountry` | Todos |
| Instruções | `payment_gb/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_gb/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_gb/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_gb/banktransfer/sort_order` | Todos |
| Ativado | `payment_gb/cashondelivery/active` | Todos |
| Título | `payment_gb/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_gb/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_gb/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_gb/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_gb/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_gb/cashondelivery/sort_order` | Todos |
| Ativado | `payment_gb/free/active` | Todos |
| Título | `payment_gb/free/title` | Todos |
| Novo status do pedido | `payment_gb/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_gb/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/free/specificcountry` | Todos |
| Ordem de classificação | `payment_gb/free/sort_order` | Todos |
| Ativado | `payment_gb/purchaseorder/active` | Todos |
| Título | `payment_gb/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_gb/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_gb/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_gb/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_gb/purchaseorder/sort_order` | Todos |
| Ativado | `payment_gb/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_gb/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_gb/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_gb/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_gb/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_gb/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_gb/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_gb/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_gb/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_gb/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_gb/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_gb/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_gb/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_gb/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_gb/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_gb/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_gb/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_gb/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_gb/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_gb/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_gb/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_gb/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_gb/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_gb/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_gb/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_gb/worldpay/title` | Somente Commerce Enterprise |
| Segredo MD5 para Transações | `payment_gb/worldpay/md5_secret` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_gb/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_gb/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_gb/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_gb/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_gb/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_gb/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_gb/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_gb/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_gb/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_gb/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_gb/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_gb/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_gb/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_gb/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_gb/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_gb/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_gb/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_gb/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_gb/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_gb/eway/sort_order` | Somente Commerce Enterprise |
| Busca programada | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Busca programada | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | Todos |
| Configurações de cartão de crédito | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Todos |
| Habilitar Crédito do PayPal | `payment/wps_express_bml/active` | Todos |
| Busca programada | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todos |
| Configurações de cartão de crédito | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | Todos |
| Rejeitar Transação se: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todos |
| Busca programada | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Todos |
| Busca programada | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todos |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todos |
| Ativado | `payment_us/free/active` | Todos |
| Título | `payment_us/free/title` | Todos |
| Novo status do pedido | `payment_us/free/order_status` | Todos |
| Faturar Todos os Itens Automaticamente | `payment_us/free/payment_action` | Todos |
| Pagamento dos países aplicáveis | `payment_us/free/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/free/specificcountry` | Todos |
| Ordem de classificação | `payment_us/free/sort_order` | Todos |
| Ativado | `payment_us/cashondelivery/active` | Todos |
| Título | `payment_us/cashondelivery/title` | Todos |
| Novo status do pedido | `payment_us/cashondelivery/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_us/cashondelivery/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/cashondelivery/specificcountry` | Todos |
| Instruções | `payment_us/cashondelivery/instructions` | Todos |
| Total mínimo de pedidos | `payment_us/cashondelivery/min_order_total` | Todos |
| Total máximo de pedidos | `payment_us/cashondelivery/max_order_total` | Todos |
| Ordem de classificação | `payment_us/cashondelivery/sort_order` | Todos |
| Ativado | `payment_us/banktransfer/active` | Todos |
| Título | `payment_us/banktransfer/title` | Todos |
| Novo status do pedido | `payment_us/banktransfer/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_us/banktransfer/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/banktransfer/specificcountry` | Todos |
| Instruções | `payment_us/banktransfer/instructions` | Todos |
| Total mínimo de pedidos | `payment_us/banktransfer/min_order_total` | Todos |
| Total máximo de pedidos | `payment_us/banktransfer/max_order_total` | Todos |
| Ordem de classificação | `payment_us/banktransfer/sort_order` | Todos |
| Ativado | `payment_us/checkmo/active` | Todos |
| Título | `payment_us/checkmo/title` | Todos |
| Novo status do pedido | `payment_us/checkmo/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_us/checkmo/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/checkmo/specificcountry` | Todos |
| Tornar cheque pagável a | `payment_us/checkmo/payable_to` | Todos |
| Total mínimo de pedidos | `payment_us/checkmo/min_order_total` | Todos |
| Total máximo de pedidos | `payment_us/checkmo/max_order_total` | Todos |
| Ordem de classificação | `payment_us/checkmo/sort_order` | Todos |
| Ativado | `payment_us/purchaseorder/active` | Todos |
| Título | `payment_us/purchaseorder/title` | Todos |
| Novo status do pedido | `payment_us/purchaseorder/order_status` | Todos |
| Pagamento dos países aplicáveis | `payment_us/purchaseorder/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/purchaseorder/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_us/purchaseorder/min_order_total` | Todos |
| Total máximo de pedidos | `payment_us/purchaseorder/max_order_total` | Todos |
| Ordem de classificação | `payment_us/purchaseorder/sort_order` | Todos |
| Ativado | `payment_us/authorizenet_directpost/active` | Todos |
| Ação de pagamento | `payment_us/authorizenet_directpost/payment_action` | Todos |
| Título | `payment_us/authorizenet_directpost/title` | Todos |
| Novo status do pedido | `payment_us/authorizenet_directpost/order_status` | Todos |
| Moeda aceita | `payment_us/authorizenet_directpost/currency` | Todos |
| Depurar | `payment_us/authorizenet_directpost/debug` | Todos |
| Tipos de cartão de crédito | `payment_us/authorizenet_directpost/cctypes` | Todos |
| Verificação de cartão de crédito | `payment_us/authorizenet_directpost/useccv` | Todos |
| Pagamento dos países aplicáveis | `payment_us/authorizenet_directpost/allowspecific` | Todos |
| Pagamento de países específicos | `payment_us/authorizenet_directpost/specificcountry` | Todos |
| Total mínimo de pedidos | `payment_us/authorizenet_directpost/min_order_total` | Todos |
| Total máximo de pedidos | `payment_us/authorizenet_directpost/max_order_total` | Todos |
| Ordem de classificação | `payment_us/authorizenet_directpost/sort_order` | Todos |
| Ativado | `payment_us/cybersource/active` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_us/cybersource/payment_action` | Somente Commerce Enterprise |
| Título | `payment_us/cybersource/title` | Somente Commerce Enterprise |
| Novo status do pedido | `payment_us/cybersource/order_status` | Somente Commerce Enterprise |
| Depurar | `payment_us/cybersource/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_us/cybersource/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_us/cybersource/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_us/cybersource/specificcountry` | Somente Commerce Enterprise |
| Total mínimo de pedidos | `payment_us/cybersource/min_order_total` | Somente Commerce Enterprise |
| Total máximo de pedidos | `payment_us/cybersource/max_order_total` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_us/cybersource/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_us/worldpay/active` | Somente Commerce Enterprise |
| Título | `payment_us/worldpay/title` | Somente Commerce Enterprise |
| Permitir Edição De Informações De Contato | `payment_us/worldpay/fix_contact` | Somente Commerce Enterprise |
| Ocultar Informações de Contato | `payment_us/worldpay/hide_contact` | Somente Commerce Enterprise |
| Campos de assinatura | `payment_us/worldpay/signature_fields` | Somente Commerce Enterprise |
| Depurar | `payment_us/worldpay/debug` | Somente Commerce Enterprise |
| Ação de pagamento para teste | `payment_us/worldpay/test_action` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_us/worldpay/payment_action` | Somente Commerce Enterprise |
| Pagamento Dos Países Aplicáveis | `payment_us/worldpay/allowspecific` | Somente Commerce Enterprise |
| Pagamento De Países Específicos | `payment_us/worldpay/specificcountry` | Somente Commerce Enterprise |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_us/worldpay/cvv_fraud_case` | Somente Commerce Enterprise |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_us/worldpay/avs_fraud_case` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_us/worldpay/sort_order` | Somente Commerce Enterprise |
| Ativado | `payment_us/eway/active` | Somente Commerce Enterprise |
| Tipo de conexão | `payment_us/eway/connection_type` | Somente Commerce Enterprise |
| Título | `payment_us/eway/title` | Somente Commerce Enterprise |
| Ação de pagamento | `payment_us/eway/payment_action` | Somente Commerce Enterprise |
| Depurar | `payment_us/eway/debug` | Somente Commerce Enterprise |
| Tipos de cartão de crédito | `payment_us/eway/cctypes` | Somente Commerce Enterprise |
| Pagamento dos países aplicáveis | `payment_us/eway/allowspecific` | Somente Commerce Enterprise |
| Pagamento de países específicos | `payment_us/eway/specificcountry` | Somente Commerce Enterprise |
| Ordem de classificação | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
