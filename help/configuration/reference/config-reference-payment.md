---
title: Referência de caminhos de configuração de pagamento
description: Consulte uma lista de valores do método de pagamento configuráveis.
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Referência de caminhos de configuração de pagamento

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de pagamento**.

A variável [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir as definições de configuração](override-config-settings.md#environment-variables). Este tópico não _não_ lista [valores confidenciais e específicos do sistema](config-reference-sens.md).

As configurações são organizadas ainda mais por método de pagamento.

## Caminhos do PayPal

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativar esta solução | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar experiência de check-out no contexto | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Crédito do PayPal | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Crédito do PayPal | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir na página de detalhes do produto | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir no carrinho de compras | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir itens de linha do carrinho | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etapa de revisão do pedido ignorado | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir itens de linha do carrinho | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opções de envio de transferência | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Botões de Atalho | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Check-out de Convidado do PayPal | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exigir endereço de cobrança do cliente | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Assinatura do Contrato de Cobrança | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir itens de linha do carrinho | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir no Assistente de Contrato de Cobrança | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar busca automática | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agendar | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora do dia | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo do produto PayPal | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de página | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL da imagem do cabeçalho | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cor do plano de fundo do cabeçalho | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cor da borda do cabeçalho | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cor do plano de fundo da página | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar esta solução | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação Crédito do PayPal | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir na página de detalhes do produto | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de Autorização de Honra (dias) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período válido do pedido (dias) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de Autorizações Filho | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir no carrinho de compras | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Métodos de autenticação de API | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API usa proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Reino Unido)

Essas opções estarão disponíveis somente se você escolher o Reino Unido como [país comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativar esta solução | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Finalização Expressa na etapa Informações de Pagamento | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Cofre Habilitado | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título do Vault | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito permitidos | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exigir entrada de CVV | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rua AVS Não Corresponde | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| O CEP AVS não corresponde | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| O indicador AVS internacional não corresponde | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| O código de segurança do cartão não corresponde | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornecedor | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Parceiro | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornecedor | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar esta solução | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| A entrada do CVV é editável | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exigir entrada de CVV | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar confirmação de email | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Link do fluxo de pagamento do PayPal

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Parceiro | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornecedor | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Link de Fluxo de Pagamento | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Check-out Expresso | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação Crédito do PayPal | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento Aplicável a Partir de | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagamento Aplicável a Partir de | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificação SSL | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| A entrada do CVV é editável | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exigir entrada de CVV | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar confirmação de email | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de check-out com subtotal zero

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativado | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de pagamento de caixa na entrega

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativado | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de Pagamento de Transferência Bancária

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativado | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de Cheque ou Ordem de Pagamento

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativado | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos da Ordem de Compra

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Ativado | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos internacionais

>[!INFO]
>
>Os caminhos disponíveis são determinados pela sua escolha de [País comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Caminho de configuração | Somente comércio? | Criptografado? |
|--------------|--------------|--------------|--------------|
| Credenciais SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar esta solução | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar verificação para | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_nz/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_nz/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_nz/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_nz/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_nz/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_nz/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_nz/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_nz/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_nz/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_nz/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_nz/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_nz/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_nz/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_nz/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_nz/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_nz/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_nz/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_nz/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_nz/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_nz/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_nz/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_nz/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_nz/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_nz/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_nz/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_nz/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_nz/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_nz/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_nz/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_hk/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_hk/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_hk/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_hk/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_hk/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_hk/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_hk/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_hk/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_hk/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_hk/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_hk/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_hk/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_hk/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_hk/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_hk/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_hk/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_hk/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_hk/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_hk/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_hk/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_hk/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_hk/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de sandbox | `payment_hk/eway/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_hk/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_hk/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_hk/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_hk/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_hk/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_hk/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_es/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_es/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID do perfil | `payment_es/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| Novo status do pedido | `payment_es/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_es/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_es/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_es/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_es/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_es/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_es/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_es/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_es/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID da instalação | `payment_es/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID da Instalação do Administrador Remoto | `payment_es/worldpay/admin_installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_es/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_es/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_es/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de teste | `payment_es/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_es/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_es/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_es/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_es/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_es/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_es/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_es/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_es/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_es/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_es/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_es/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_es/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_es/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_es/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_es/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_it/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_it/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_it/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_it/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_it/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_it/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_it/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_it/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_it/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_it/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_it/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_it/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_it/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_it/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_it/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_it/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_it/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_it/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_it/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_it/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_it/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_it/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_it/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_it/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_it/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_it/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_it/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_it/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_it/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_it/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_fr/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_fr/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_fr/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_fr/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_fr/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_fr/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_fr/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_fr/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_fr/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_fr/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_fr/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_fr/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_fr/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_fr/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_fr/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_fr/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_fr/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_fr/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_fr/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_fr/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_fr/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_fr/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_fr/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_fr/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_fr/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_fr/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_fr/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_fr/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_jp/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_jp/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_jp/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_jp/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_jp/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_jp/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_jp/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_jp/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_jp/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_jp/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_jp/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_jp/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_jp/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_jp/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_jp/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_jp/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_jp/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_jp/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_jp/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_jp/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_jp/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_jp/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_jp/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_jp/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_jp/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_jp/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_jp/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar verificação para | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_au/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_au/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID do comerciante | `payment_au/cybersource/merchant_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| ID do perfil | `payment_au/cybersource/profile_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) | ![Criptografado](/help/assets/configuration/cloud-enc.png) |
| Novo status do pedido | `payment_au/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_au/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_au/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_au/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_au/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_au/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_au/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_au/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_au/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ID da instalação | `payment_au/worldpay/installation_id` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_au/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_au/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_au/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_au/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de teste | `payment_au/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_au/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_au/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_au/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_au/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_au/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_au/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_au/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_au/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_au/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_au/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_au/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_au/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_au/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_au/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_au/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar esta solução | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_ca/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_ca/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_ca/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_ca/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_ca/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_ca/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_ca/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_ca/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_ca/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_ca/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_ca/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_ca/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_ca/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_ca/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_ca/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_ca/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_ca/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_ca/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_ca/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_ca/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_ca/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_ca/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_ca/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_ca/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_ca/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_ca/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_ca/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_ca/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar email para o cliente | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_other/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_other/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_other/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_other/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_other/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_other/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_other/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_other/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_other/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_other/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_other/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_other/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_other/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_other/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_other/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_other/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_other/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_other/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_other/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_other/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_other/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_other/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_other/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_other/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_other/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_other/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_other/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_other/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_other/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_de/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_de/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_de/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_de/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_de/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_de/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_de/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_de/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_de/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_de/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_de/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_de/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_de/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de teste | `payment_de/worldpay/sandbox_flag` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_de/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_de/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_de/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_de/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_de/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_de/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_de/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_de/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_de/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_de/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_de/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_de/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_de/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_de/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_de/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_gb/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_gb/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_gb/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_gb/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_gb/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_gb/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_gb/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_gb/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_gb/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_gb/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Segredo MD5 para Transações | `payment_gb/worldpay/md5_secret` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_gb/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_gb/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_gb/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_gb/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_gb/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_gb/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_gb/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_gb/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_gb/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_gb/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_gb/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_gb/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_gb/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_gb/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_gb/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_gb/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_gb/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_gb/eway/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Busca programada | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Crédito do PayPal | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configurações de cartão de crédito | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeitar Transação se: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Busca programada | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de Páginas do Comerciante do PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Faturar Todos os Itens Automaticamente | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruções | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tornar cheque pagável a | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ação de pagamento | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo status do pedido | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda aceita | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de cartão de crédito | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificação de cartão de crédito | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dos países aplicáveis | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento de países específicos | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total mínimo de pedidos | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total máximo de pedidos | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `payment_us/cybersource/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_us/cybersource/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/cybersource/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo status do pedido | `payment_us/cybersource/order_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_us/cybersource/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_us/cybersource/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_us/cybersource/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_us/cybersource/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total mínimo de pedidos | `payment_us/cybersource/min_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Total máximo de pedidos | `payment_us/cybersource/max_order_total` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_us/cybersource/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_us/worldpay/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/worldpay/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Edição De Informações De Contato | `payment_us/worldpay/fix_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ocultar Informações de Contato | `payment_us/worldpay/hide_contact` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Campos de assinatura | `payment_us/worldpay/signature_fields` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_us/worldpay/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento para teste | `payment_us/worldpay/test_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_us/worldpay/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento Dos Países Aplicáveis | `payment_us/worldpay/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento De Países Específicos | `payment_us/worldpay/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Definir o status do pedido como suspeita de fraude para CVV | `payment_us/worldpay/cvv_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Defina o status do pedido como suspeita de fraude para AVS de código postal | `payment_us/worldpay/avs_fraud_case` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_us/worldpay/sort_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `payment_us/eway/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexão | `payment_us/eway/connection_type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/eway/title` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ação de pagamento | `payment_us/eway/payment_action` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Depurar | `payment_us/eway/debug` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipos de cartão de crédito | `payment_us/eway/cctypes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento dos países aplicáveis | `payment_us/eway/allowspecific` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pagamento de países específicos | `payment_us/eway/specificcountry` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de classificação | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
