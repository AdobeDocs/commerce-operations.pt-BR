---
title: Referência de caminhos de configuração de clientes
description: Saiba mais sobre os caminhos e valores da configuração do cliente nas configurações de administração do Adobe Commerce. Conheça informativos, gerenciamento de contas e opções de atendimento ao cliente.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Referência de caminhos de configuração de clientes

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes**.

O comando [`magento app:config:dump` ](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir definições de configuração](override-config-settings.md#environment-variables). Este tópico _não_ lista [valores confidenciais e específicos do sistema](config-reference-sens.md).

## Caminhos do informativo

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Informativo**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Permitir Assinatura de Convidado | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| É necessário confirmar | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do e-mail de confirmação | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail de confirmação | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do email de sucesso | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail de sucesso | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cancelar assinatura do remetente de email | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de cancelamento de assinatura | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de configuração do cliente

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Configuração do Cliente**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Intervalo de Minutos Online | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartilhar contas de clientes | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Atribuição Automática ao Grupo de Clientes | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo de Imposto Baseado em | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo padrão | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA válida - Doméstico | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA válida - IntraUnion | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA inválida | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo de erros de validação | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar em Cada Transação | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor Padrão para Desabilitar Alterações Automáticas do Grupo com Base na ID de IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número IVA na vitrine eletrônica | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de boas-vindas padrão | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email De Boas-Vindas Padrão Sem Senha | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do email | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exigir confirmação de e-mails | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail do link de confirmação | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de boas-vindas | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar ID do cliente compatível com humanos | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Proteção contra Redefinição de Senha | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de solicitações de redefinição de senha | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo Mínimo Entre Solicitações De Redefinição De Senha | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esqueceu o modelo de e-mail | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lembrar Modelo de Email | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redefinir modelo de senha | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email do modelo de senha | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração do link de recuperação (horas) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar preenchimento automático em formulários de senha de logon/esquecimento | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de classes de caracteres necessárias | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Falhas de Logon para Bloquear Conta | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Comprimento mínimo da senha | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo de Bloqueio (minutos) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de linhas em um endereço | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar prefixo | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opções da lista suspensa Prefixo | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar nome do meio (inicial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Sufixo | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opções da lista suspensa Sufixo | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar data de nascimento | `customer/address/dob_show`<br>Ao manter as práticas recomendadas atuais de segurança e privacidade, verifique se você está ciente de possíveis riscos legais e de segurança associados ao armazenamento da data de nascimento completa do cliente (mês, dia, ano) juntamente com outros identificadores pessoais, como nome completo, antes de coletar ou processar esses dados. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Número de Imposto/IVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Sexo | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar a Funcionalidade de Crédito da Loja | `customer/magento_customerbalance/is_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar Histórico de Crédito da Loja para Clientes | `customer/magento_customerbalance/show_history` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Reembolsar Crédito da Loja Automaticamente | `customer/magento_customerbalance/refund_automatically` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Remetente de Email de Atualização de Crédito da Loja | `customer/magento_customerbalance/email_identity` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modelo de email de atualização de crédito da loja | `customer/magento_customerbalance/email_template` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Redirecionar cliente para o painel da conta após fazer logon | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto em uma linha | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar a funcionalidade de segmento do cliente | `customer/magento_customersegment/is_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar CAPTCHA na loja | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fonte | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de exibição | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de tentativas de logon malsucedidas | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo Limite de CAPTCHA (minutos) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos usados em CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diferenciação de maiúsculas e minúsculas | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos da lista de desejos

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Lista de desejos**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativado | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar várias listas de desejos | `wishlist/general/multiple_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número de várias listas de desejos | `wishlist/general/multiple_wishlist_number` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Remetente do email | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de emails permitidos para envio | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de comprimento do texto do email | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir resumo das listas de desejos | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos dos convites

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Convites**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativar a funcionalidade de convites | `magento_invitation/general/enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar Convites na Loja | `magento_invitation/general/enabled_on_front` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupo de Clientes Referenciado | `magento_invitation/general/registration_use_inviter_group` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Registro de novas contas | `magento_invitation/general/registration_required_invitation` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir que os clientes adicionem uma mensagem personalizada ao email de convite | `magento_invitation/general/allow_customer_message` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de convites permitidos para envio único | `magento_invitation/general/max_invitation_amount_per_send` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Remetente do Email de Convite do Cliente | `magento_invitation/email/identity` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modelo de e-mail de convite do cliente | `magento_invitation/email/template` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos de pontos de premiação

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Pontos de recompensa**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativar a funcionalidade de pontos de recompensa | `magento_reward/general/is_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Ativar a funcionalidade de pontos de recompensa na loja | `magento_reward/general/is_enabled_on_front` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Clientes podem ver o histórico de pontos de recompensa | `magento_reward/general/publish_history` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite de Resgate de Saldo de Pontos de Recompensa | `magento_reward/general/min_points_balance` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limitar Saldo De Pontos De Recompensa Em | `magento_reward/general/max_points_balance` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Pontos de premiação expiram em (dias) | `magento_reward/general/expiration_days` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Cálculo da expiração dos pontos de premiação | `magento_reward/general/expiry_calculation` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Reembolsar pontos de recompensa automaticamente | `magento_reward/general/refund_automatically` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Deduzir automaticamente os pontos de premiação do valor do reembolso | `magento_reward/general/deduct_automatically` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Landing Page | `magento_reward/general/landing_page` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Comprar | `magento_reward/points/order` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Registro | `magento_reward/points/register` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Inscrição no informativo | `magento_reward/points/newsletter` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Convertendo convite para cliente | `magento_reward/points/invitation_customer` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite de Quantidade de Conversões de Convite para Cliente | `magento_reward/points/invitation_customer_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Convertendo convite em pedido | `magento_reward/points/invitation_order` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite de Quantidade de Conversões de Convite para Ordem | `magento_reward/points/invitation_order_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Conversão de convite para recompensa de pedido | `magento_reward/points/invitation_order_frequency` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Revisar envio | `magento_reward/points/review` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite de Quantidade de Envio de Revisões Premiadas | `magento_reward/points/review_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Remetente do email | `magento_reward/notification/email_sender` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Assinar Clientes por Padrão | `magento_reward/notification/subscribe_by_default` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| E-mail de atualização de saldo | `magento_reward/notification/balance_update_template` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Email de aviso de expiração de pontos de premiação | `magento_reward/notification/expiry_warning_template` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Aviso de Expiração Antes de (dias) | `magento_reward/notification/expiry_day_before` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos de promoções

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Promoções**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativar emails de lembrete | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Interval | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto da hora | `promo/magento_reminder/minutes` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Hora de início | `promo/magento_reminder/time` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Máximo de emails por execução | `promo/magento_reminder/limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite de falha de envio de email | `promo/magento_reminder/threshold` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Lembrete de remetente de email | `promo/magento_reminder/identity` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Comprimento do código | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato do código | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefixo do código | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo do código | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Traço a cada X caracteres | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos do Registro de presentes

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Registro de presentes**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativar Registro de presentes | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de inscritos | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do email | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do email | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite máximo de emails enviados | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do email | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos do carrinho de compras persistentes

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Clientes** > **Carrinho de Compras Persistente**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativar persistência | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da persistência (segundos) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar &quot;Lembre-se de mim&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor padrão &quot;Lembre-se de mim&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpar Persistência ao Sair | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir carrinho de compras | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lista de desejos persistente | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter itens solicitados recentemente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir Produtos Atualmente Comparados | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Histórico de Comparação de Persistência | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Manter produtos visualizados recentemente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistência da associação e da segmentação do grupo do cliente | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
