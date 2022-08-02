---
title: Referência de caminhos de configuração de vendas
description: Consulte uma lista de valores de configuração de vendas.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 0%

---


# Referência de caminhos de configuração de vendas

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Vendas**.

O [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Como opção, para substituir qualquer configuração ou definir configurações confidenciais, consulte [Usar variáveis de ambiente para substituir configurações](override-config-settings.md#environment-variables). Este tópico faz _not_ lista [valores sensíveis e específicos do sistema](config-reference-sens.md).

## Caminhos de vendas

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Vendas**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ocultar IP do cliente | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotal | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desconto | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envio | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposto | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposto fixo sobre o produto | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total geral | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cartões de presentes | `sales/totals_sort/giftcardaccount` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Crédito da loja | `sales/totals_sort/customerbalance` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Reordenar | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para impressão de PDF (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para HTML Print View | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Endereço | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor Mínimo | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir Imposto para Quantia | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de descrição | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro para mostrar no carrinho de compras | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar cada endereço separadamente no check-out de vários endereços | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de descrição de vários endereços | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro de vários endereços para mostrar no carrinho de compras | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar dados agregados | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da Ordem de Pagamento Pendente (minutos) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensagens de presente no nível da ordem | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Mensagens de Presente para Itens de Ordem | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Quebra de Presente no Nível da Ordem | `sales/gift_options/wrapping_allow_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Quebra de Lixo para Itens de Ordem | `sales/gift_options/wrapping_allow_items` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Recebimento de Presente | `sales/gift_options/allow_gift_receipt` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir cartão impresso | `sales/gift_options/allow_printed_card` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Preço padrão do cartão impresso | `sales/gift_options/printed_card_price` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Habilitar MAPA | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preço Real | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de texto do pop-up padrão | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de texto padrão &quot;O que é isso&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar pedido por SKU em Minha conta na loja | `sales/product_sku/my_account_enable` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto do botão | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupos de clientes | `sales/product_sku/allowed_groups` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar arquivamento | `sales/magento_salesarchive/active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Arquivar pedidos comprados | `sales/magento_salesarchive/age` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Status do pedido a ser arquivado | `sales/magento_salesarchive/order_statuses` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar RMA na Loja | `sales/magento_rma/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar RMA no nível do produto | `sales/magento_rma/enabled_on_product` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Usar Endereço da Loja | `sales/magento_rma/use_store_address` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Caminhos de emails de vendas

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Emails de vendas**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Envio assíncrono | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email de Confirmação de Novo Pedido | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo modelo de confirmação de pedido | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo modelo de confirmação de pedido para convidado | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de Cópia de Email de Encomenda | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email do comentário do pedido | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário do Pedido | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário do Pedido para Convidado | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Comentários de Pedido - Método de Cópia de Correio Eletrônico | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email de fatura | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email da NFF | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de fatura para convidado | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Método de Cópia de Email da NFF | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email do Comentário da NFF | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário da NFF | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Comentário da NFF para Convidado | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Comentários da NFF Método de Cópia de Email | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email de Remessa | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Entrega | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Entrega para Convidado | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar método de cópia de email de remessa | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email do Comentário da Entrega | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário da Entrega | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário da Entrega para Convidado | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Comentários de Entrega Método de Cópia de Email | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email do Aviso de Crédito | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Aviso de Crédito | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Aviso de Crédito para o Convidado | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Método de Cópia de Email do Aviso de Crédito | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email do Comentário do Aviso de Crédito | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário do Aviso de Crédito | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email do Comentário do Aviso de Crédito para o Convidado | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentários do aviso de crédito Método de cópia de email | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sales_email/magento_rma/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email RMA | `sales_email/magento_rma/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de email RMA | `sales_email/magento_rma/template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de email RMA para convidado | `sales_email/magento_rma/guest_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de cópia de email RMA | `sales_email/magento_rma/copy_method` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `sales_email/magento_rma_auth/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email de autorização de RMA | `sales_email/magento_rma_auth/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Autorização RMA | `sales_email/magento_rma_auth/template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Autorização RMA para Convidado | `sales_email/magento_rma_auth/guest_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de cópia de email de autorização RMA | `sales_email/magento_rma_auth/copy_method` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `sales_email/magento_rma_comment/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email de comentário RMA | `sales_email/magento_rma_comment/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Comentário RMA | `sales_email/magento_rma_comment/template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de email de comentário RMA para convidado | `sales_email/magento_rma_comment/guest_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de cópia de email RMA | `sales_email/magento_rma_comment/copy_method` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativado | `sales_email/magento_rma_customer_comment/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email de comentário RMA | `sales_email/magento_rma_customer_comment/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Recipient de email de comentário RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Comentário RMA | `sales_email/magento_rma_customer_comment/template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de cópia de email RMA | `sales_email/magento_rma_customer_comment/copy_method` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir ID do pedido no cabeçalho | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir ID do pedido no cabeçalho | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir ID do pedido no cabeçalho | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos fiscais

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Imposto**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Classe de Imposto para Entrega | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe de Imposto para Opções de Presente | `tax/classes/wrapping_tax_class` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Classe de Imposto Padrão para Produto | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe de Imposto Padrão para Cliente | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método De Cálculo De Imposto Baseado Em | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo De Imposto Baseado Em | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preços do Catálogo | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preços da Entrega | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar imposto sobre o cliente | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar Desconto nos Preços | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar Imposto em | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar comércio transfronteiriço | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| País padrão | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estado padrão | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Código de postagem padrão | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços Do Produto No Catálogo | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços de Entrega | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Subtotal | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Quantia de Entrega | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços de Quebra de Presente | `tax/cart_display/gift_wrapping` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir preços do cartão impresso | `tax/cart_display/printed_card` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Incluir Imposto No Total Da Ordem | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Resumo de Imposto Completo | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Subtotal de Imposto Zero | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Subtotal | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Quantia de Entrega | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços de Quebra de Presente | `tax/sales_display/gift_wrapping` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir preços do cartão impresso | `tax/sales_display/printed_card` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Incluir Imposto No Total Da Ordem | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Resumo de Imposto Completo | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Subtotal de Imposto Zero | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços Em Listas De Produtos | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços Na Página Exibição Do Produto | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços Em Módulos De Vendas | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Preços Em Emails | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar Imposto a FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir FPT no Subtotal | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de check-out

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Check-out**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar o Check-out do Onepage | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Check-out de Convidado | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Endereço de Faturamento em | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar termos e condições | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da Cotação (dias) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Após adicionar um redirecionamento de produto ao carrinho de compras | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagem de produto agrupada | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagem configurável do produto | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da Cotação de Pré-visualização (minutos) | `checkout/cart/preview_quota_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir resumo do carrinho | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir barra lateral do carrinho de compras | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Itens Adicionados Recentemente | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de Email com Falha no Pagamento | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento com Falha no Receptor de Email | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Pagamento com Falha | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de Cópia de Email de Envio de Pagamento com Falha | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de configurações de remessa

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Configurações de envio**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Aplicar Política de Entrega Personalizada | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Política de remessa | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de configurações de multienvio

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Configurações de multienvio**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Permitir remessa para vários endereços | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantidade Máxima Permitida para Entrega para Vários Endereços | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de métodos de delivery

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Métodos de delivery**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativado | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome do método | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preço | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome do método | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor Mínimo da Ordem | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome do método | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condição | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir produtos virtuais no cálculo de preços | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportar | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importar | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para Check-out | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado para RMA | `carriers/ups/active_rma` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tipo de UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origem da Remessa | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL do gateway | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Taxas Negociadas | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Solicitação de Pacotes | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contêiner | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidade de peso | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de destino | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo do pacote (consulte a transportadora para obter o peso máximo suportado do envio) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de retirada | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso Mínimo do Pacote (Consulte a transportadora para obter o peso mínimo de envio suportado) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manuseio Aplicado | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Livre | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Limite de Entrega Livre | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de Quantia de Entrega Livre | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para Check-out | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado para RMA | `carriers/usps/active_rma` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Solicitação de Pacotes | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contêiner | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Length | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largura | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Namorada | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Computador | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo do pacote (consulte a transportadora para obter o peso máximo suportado do envio) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manuseio Aplicado | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Livre | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Limite de Entrega Livre | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de Quantia de Entrega Livre | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para Check-out | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado para RMA | `carriers/fedex/active_rma` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de serviços da Web (Produção) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de serviços da Web (sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Solicitação de Pacotes | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Embalagem | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Queda | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidade de peso | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo do pacote (consulte a transportadora para obter o peso máximo suportado do envio) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manuseio Aplicado | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrega Residencial | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID do Hub | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Livre | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Limite de Entrega Livre | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de Quantia de Entrega Livre | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para Check-out | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado para RMA | `carriers/dhl/active_rma` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de conteúdo | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular taxa de tratamento | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manuseio Aplicado | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxa de Manipulação | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dividir peso da ordem | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidade de peso | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidade | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largura | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de preparação | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensagem de erro exibida | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Livre | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Livre | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Limite de Entrega Livre | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de Quantia de Entrega Livre | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para os países aplicáveis | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar para países específicos | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método se não for aplicável | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem de classificação | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos da API do Google

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **API do Google**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Habilitar | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de conta | `google/analytics/type` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar experimentos de conteúdo | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Propriedade List da página de catálogo | `google/analytics/catalog_page_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Propriedade List para o bloco de venda cruzada | `google/analytics/crosssell_block_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Propriedade de lista para o bloco de venda adicional | `google/analytics/upsell_block_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Propriedade de lista para o bloco de produtos relacionados | `google/analytics/related_block_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Propriedade List da página de resultados da pesquisa | `google/analytics/search_page_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| ’Promoções internas’ para o campo de promoções &quot;Rótulo&quot;. | `google/analytics/promotions_list_value` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Habilitar | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de conversão | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Idioma de conversão | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de conversão | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cor da conversão | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rótulo de conversão | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de valor de conversão | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor de conversão | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de cartões-presente

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Vendas** > **Cartões de presentes**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Remetente de email de notificação de cartão de presente | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de notificação do cartão-presente | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reembolsáveis | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração (dias) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensagem de presente | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho máximo da mensagem de presente | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar Conta de Cartão de Presente quando o Item de Pedido for | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email do cartão-presente | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Cartão-presente | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho do código | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefixo de código | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo de código | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Traçar Cada X Caracteres | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novo Tamanho do Pool | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite do Pool de Códigos Baixo | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
