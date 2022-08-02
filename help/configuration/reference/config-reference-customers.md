---
title: Referência de caminhos de configuração de clientes
description: Consulte uma lista de valores de configuração de clientes.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Referência de caminhos de configuração de clientes

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Clientes**.

O [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Como opção, para substituir qualquer configuração ou definir configurações confidenciais, consulte [Usar variáveis de ambiente para substituir configurações](override-config-settings.md#environment-variables). Este tópico faz _not_ lista [valores sensíveis e específicos do sistema](config-reference-sens.md).

## Caminhos de boletim informativo

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Informativo**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Permitir assinatura de convidado | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precisa confirmar | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email de confirmação | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de confirmação | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email bem-sucedido | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email bem-sucedido | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email de cancelamento de assinatura | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cancelar assinatura do modelo de email | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de configuração do cliente

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Configuração do cliente**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Intervalo de Minutos Online | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartilhar contas de cliente | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Atribuição Automática ao Grupo de Clientes | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo De Imposto Baseado Em | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo padrão | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA Válido - Nacional | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA Válido - IntraUnião | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA Inválido | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo de Erros de Validação | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar em cada transação | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor Padrão para Desativar Alterações Automáticas de Grupo Baseadas em ID de IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Número de IVA na Loja | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de boas-vindas padrão | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de boas-vindas padrão sem senha | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solicitar confirmação de emails | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email do link de confirmação | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de boas-vindas | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar ID de cliente compatível com o ser humano | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Proteção de Redefinição de Senha | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número Máximo de Solicitações de Redefinição de Senha | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo Mínimo Entre Solicitações De Redefinição De Senha | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esqueceu o modelo de email | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lembrar modelo de email | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redefinir Modelo de Senha | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email do modelo de senha | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de Expiração do Link de Recuperação (horas) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Preenchimento Automático no login/Esqueceu os formulários de senha | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de classes de caracteres obrigatórias | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Falhas de Logon para Bloquear Conta | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho mínimo da senha | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo de Bloqueio (minutos) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de linhas em um endereço de rua | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar prefixo | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opções de lista suspensa de prefixos | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar nome do meio (inicial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar sufixo | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opções Suspensas de Sufixo | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar data de nascimento | `customer/address/dob_show`<br>Ao manter as práticas recomendadas atuais de segurança e privacidade, esteja ciente de possíveis riscos legais e de segurança associados ao armazenamento da data de nascimento completa dos clientes (mês, dia, ano) juntamente com outros identificadores pessoais, como o nome completo, antes de coletar ou processar esses dados. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número de imposto/IVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar gênero | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar funcionalidade de crédito de armazenamento | `customer/magento_customerbalance/is_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar Histórico de Crédito da Loja aos Clientes | `customer/magento_customerbalance/show_history` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Crédito do Repositório de Restituições Automaticamente | `customer/magento_customerbalance/refund_automatically` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de Email de Atualização de Crédito da Loja | `customer/magento_customerbalance/email_identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Atualização de Crédito da Loja | `customer/magento_customerbalance/email_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Redirecionar cliente para o painel de conta após fazer logon | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto Uma Linha | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar a funcionalidade de segmento do cliente | `customer/magento_customersegment/is_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar CAPTCHA na vitrine | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fonte | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de exibição | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de Tentativas de Logon sem Êxito | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite do CAPTCHA (minutos) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos usados em CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diferenciação de maiúsculas e minúsculas | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de lista de desejos

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Lista de desejos**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativado | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar várias listas de desejos | `wishlist/general/multiple_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Número de Várias Listas de Desejos | `wishlist/general/multiple_wishlist_number` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de emails permitidos para envio | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de comprimento do texto do email | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Resumo de Listas de Desejo | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de convites

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Convites**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar funcionalidade de convites | `magento_invitation/general/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar convites na vitrine | `magento_invitation/general/enabled_on_front` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Grupo de clientes referenciados | `magento_invitation/general/registration_use_inviter_group` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Novo Registro de Contas | `magento_invitation/general/registration_required_invitation` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir que os clientes adicionem mensagens personalizadas ao email de convite | `magento_invitation/general/allow_customer_message` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Máximo de convites permitidos para serem enviados ao mesmo tempo | `magento_invitation/general/max_invitation_amount_per_send` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email de convite do cliente | `magento_invitation/email/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modelo de Email de Convite do Cliente | `magento_invitation/email/template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Caminhos de pontos de redirecionamento

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Pontos de premiação**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar a funcionalidade de pontos de recompensa | `magento_reward/general/is_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar a funcionalidade de pontos de recompensa na vitrine | `magento_reward/general/is_enabled_on_front` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Os Clientes Podem Ver O Histórico De Pontos De Recompensa | `magento_reward/general/publish_history` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pontos de Recompensa Limite de Restituição de Saldo | `magento_reward/general/min_points_balance` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Equilíbrio de Pontos de Retorno de Cap a | `magento_reward/general/max_points_balance` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Pontos de recompensa expiram em (dias) | `magento_reward/general/expiration_days` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Cálculo de Expiração de Pontos de Recompensa | `magento_reward/general/expiry_calculation` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Reembolsar Pontos de Reembolso Automaticamente | `magento_reward/general/refund_automatically` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Deduzir Pontos de Recompensa da Quantia de Reembolso Automaticamente | `magento_reward/general/deduct_automatically` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Página de aterrissagem | `magento_reward/general/landing_page` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Compra | `magento_reward/points/order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Registro | `magento_reward/points/register` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Inscrição em boletim informativo | `magento_reward/points/newsletter` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Convertendo Convite para Cliente | `magento_reward/points/invitation_customer` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limite de Quantidade de Conversões de Convite para Cliente | `magento_reward/points/invitation_customer_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Convertendo Convite em Ordem | `magento_reward/points/invitation_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limite de Quantidade de Conversões de Convite para Ordem | `magento_reward/points/invitation_order_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Conversão de Convite para Reembolso de Pedidos | `magento_reward/points/invitation_order_frequency` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Rever Envio | `magento_reward/points/review` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Respostas Recomendadas Limite de Quantidade de Envio | `magento_reward/points/review_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email | `magento_reward/notification/email_sender` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Assinar clientes por padrão | `magento_reward/notification/subscribe_by_default` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Email de Atualização do Saldo | `magento_reward/notification/balance_update_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| E-mail de aviso de expiração de pontos de recompensa | `magento_reward/notification/expiry_warning_template` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Aviso de expiração antes (dias) | `magento_reward/notification/expiry_day_before` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Caminhos de promoções

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Promoções**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar Emails de Lembrete | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto da hora | `promo/magento_reminder/minutes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Hora de início | `promo/magento_reminder/time` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Máximo de Emails por Uma Execução | `promo/magento_reminder/limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limite de Falha de Envio de Email | `promo/magento_reminder/threshold` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Remetente de email do lembrete | `promo/magento_reminder/identity` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tamanho do código | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefixo de código | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo de código | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Traçar Cada X Caracteres | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos de registro de presente

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Registro do Presente**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Habilitar Registro de Presente | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Registros | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite máximo de emails enviados | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Caminhos persistentes do carrinho de compras

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Carrinho de compras persistente**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar persistência | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da persistência (segundos) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar &quot;Lembre-se de mim&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor padrão &quot;Lembrar-me&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpar persistência ao sair | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter carrinho de compras | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter Lista de Desejos | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter itens pedidos recentemente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir Produtos Comparados Atualmente | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Histórico de comparação persistente | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter produtos visualizados recentemente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir associação e segmentação do grupo de clientes | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
