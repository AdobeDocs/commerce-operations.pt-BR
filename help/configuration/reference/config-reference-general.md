---
title: Referência de caminhos de configuração geral
description: Consulte uma lista de valores de configuração gerais e avançados.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Referência de caminhos de configuração gerais e avançados

Este tópico lista caminhos de configuração gerais e avançados e _não_ [valores confidenciais e específicos do sistema](config-reference-sens.md). A variável [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem.

Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir as definições de configuração](override-config-settings.md#environment-variables).

## Categoria geral

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Geral**.

### Caminhos gerais

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > Geral > **Geral**.

| Nome | Caminho de configuração | Somente comércio? | Sensível? |
|--------------|--------------|--------------|--------------|
| País Padrão | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Permitir países | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| O CEP é opcional para | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Países da União Europeia | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensível](/help/assets/configuration/cloud-sens.png) |
| Principais destinos | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| O estado é obrigatório para | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Escolher Estado se for Opcional para País | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Fuso horário | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Localidade | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Unidade de Peso | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Primeiro Dia da Semana | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Dias do fim de semana | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Restrição de acesso | `general/restriction/is_active` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |
| Modo de restrição | `general/restriction/mode` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |
| Página de inicialização | `general/restriction/http_redirect` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |
| Landing Page | `general/restriction/cms_page` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |
| Resposta HTTP | `general/restriction/http_status` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |  |
| Nome do armazenamento | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número de telefone da loja | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Armazenar horas de operação | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| País | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Região/Estado | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| CEP | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Cidade | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Endereço | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Rua Endereço Linha 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número IVA | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Ativar modo de armazenamento único | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### Caminhos da Web

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Web**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Adicionar código da loja a URLs | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirecionar automaticamente para o URL base | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar regravações do servidor da Web | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URLs Seguros na Loja | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URLs seguros no Admin | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Atualizar solicitações inseguras | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cabeçalho de descarregamento | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página inicial do CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página Sem Rota do CMS | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página Nenhum cookie do CMS | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar navegações estruturais para páginas CMS | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração do cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar somente HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de restrição de cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar SID na loja | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirecionar para página do CMS se os cookies estiverem desativados | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar aviso se o JavaScript estiver desativado | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar aviso se o armazenamento local estiver desativado | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos de configuração de moeda

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Configuração de moeda**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Moeda de base | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moeda de Exibição Padrão | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moedas permitidas | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| Tempo limite da conexão em segundos | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite da conexão em segundos | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite da conexão em segundos | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Serviço | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinatário de email de erro | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro de remetente de email | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro no modelo de e-mail | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos de contatos

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Contatos**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar Entre Em Contato Conosco | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Emails Para | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do e-mail | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de e-mail | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos de relatórios

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Relatórios**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Início do Acumulado no Ano | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mês Atual Começa | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos de gerenciamento de conteúdo

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Gestão de conteúdo**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar editor WYSIWYG | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URLs estáticos para conteúdo de mídia no WYSIWYG para catálogo | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar funcionalidade de hierarquia | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar metadados de hierarquia | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Layout padrão para o menu Hierarquia | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos de relatórios do New Relic

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Geral** > **Relatórios do New Relic**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Habilitar Integração com o New Relic | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome do aplicativo New Relic | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Categoria avançada

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador, em **Lojas** > Configurações > **Configuração** > **Avançado**.

### Caminhos de administração

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Admin**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Modelo de email de senha esquecida | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esqueceu e reinicializa o remetente de email | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de notificação do usuário | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página de inicialização | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URL de administração personalizada | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar caminho de administração personalizado | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartilhamento de conta de administrador | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de Proteção contra Redefinição de Senha | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de expiração do link de recuperação (horas) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de solicitações de redefinição de senha | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo Mínimo Entre Solicitações De Redefinição De Senha | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adicionar chave secreta aos URLs | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| O logon diferencia maiúsculas de minúsculas | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da sessão do administrador (segundos) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Falhas de Logon para Bloquear Conta | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo de Bloqueio (minutos) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da senha (dias) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alteração de senha | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar Gráficos | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar CAPTCHA no administrador | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fonte | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de exibição | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de tentativas de logon malsucedidas | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo Limite de CAPTCHA (minutos) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos usados em CAPTCHA | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diferenciação de maiúsculas e minúsculas | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ações ativadas | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos do sistema

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Duração das mensagens de sucesso | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tentar novamente as mensagens em andamento após | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo de vida das mensagens com falha | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração de novas mensagens | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar Agendamentos a Cada | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agendar com antecedência para | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Perdido se Não Executado em | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpeza do Histórico a Cada | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vida útil do histórico de sucesso | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração do Histórico de Falhas | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Processo Separado | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar Agendamentos a Cada | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agendar com antecedência para | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Perdido se Não Executado em | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpeza do Histórico a Cada | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vida útil do histórico de sucesso | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração do Histórico de Falhas | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar Agendamentos a Cada | `system/cron/staging/schedule_generate_every` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Agendar com antecedência para | `system/cron/staging/schedule_ahead_for` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Perdido se Não Executado em | `system/cron/staging/schedule_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limpeza do Histórico a Cada | `system/cron/staging/history_cleanup_every` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Vida útil do histórico de sucesso | `system/cron/staging/history_success_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Duração do Histórico de Falhas | `system/cron/staging/history_failure_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Usar Processo Separado | `system/cron/staging/use_separate_process` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Gerar Agendamentos a Cada | `system/cron/catalog/event/schedule_generate_every` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Agendar com antecedência para | `system/cron/catalog/event/schedule_ahead_for` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Perdido se Não Executado em | `system/cron/catalog/event/schedule_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limpeza do Histórico a Cada | `system/cron/catalog/event/history_cleanup_every` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Vida útil do histórico de sucesso | `system/cron/catalog/event/history_success_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Duração do Histórico de Falhas | `system/cron/catalog/event/history_failure_lifetime` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Usar Processo Separado | `system/cron/catalog/event/use_separate_process` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Usar Processo Separado | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desabilitar Comunicações por Email | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Definir Return-Path | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Email de caminho de retorno | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moedas Instaladas | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar HTTPS para obter feed | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência de atualização | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Última atualização | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Backup Agendado | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de backup | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de manutenção | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duração da Entrada de Log, Dias | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência de Arquivamento de Log | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicativo de cache | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL para conteúdo público | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de carência | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportar configuração | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dias salvos no registro | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Armazenamento de mídia | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Selecionar banco de dados de mídia | `system/media_storage_configuration/media_database` (descontinuado no Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo de atualização do ambiente | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Salvar arquivos, dias | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Limpeza do Histórico de Arquivos Agendada | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro no modelo de e-mail | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Caminhos do desenvolvedor

Esses valores de configuração estão disponíveis no Admin do **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Tipo de fluxo de trabalho | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir links simbólicos | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reduzir Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar as dicas de caminho do modelo para a loja | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar as dicas de caminho do modelo para o administrador | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adicionar nomes de bloco às dicas | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrar no arquivo | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrar no syslog | `dev/syslog/syslog_logging` |  |
| Ativado para vitrine | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado para administrador | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mesclar arquivos JavaScript | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar agrupamento de JavaScript | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reduzir arquivos JavaScript | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estratégia de tradução | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrar erros de JS no armazenamento da sessão | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mesclar arquivos CSS | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reduzir arquivos CSS | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adaptador de imagem | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Assinar arquivos estáticos | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indexação assíncrona | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Armazenar Atributos Definidos pelo Usuário em Cache | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
