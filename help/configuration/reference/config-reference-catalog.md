---
title: Referência de caminhos de configuração de catálogo
description: Consulte uma lista de valores de configuração de catálogo.
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 47bda51cdcab964c37d9f652d467d69d795d8641
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# Referência de caminhos de configuração de catálogo

Esta seção lista nomes de variáveis e caminhos de configuração disponíveis para opções no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo**.

O comando [`magento app:config:dump` ](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Para substituir opcionalmente qualquer definição de configuração ou definir definições confidenciais, consulte [Usar variáveis de ambiente para substituir definições de configuração](override-config-settings.md#environment-variables). Este tópico _não_ lista [valores confidenciais e específicos do sistema](config-reference-sens.md).

## Caminhos do catálogo

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Máscara para SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para metatítulo | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para palavras-chave meta | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para descrição meta | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de lista | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valores Permitidos de Produtos por Página na Grade | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor Padrão de Produtos por Página na Grade | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página na lista de valores permitidos | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página no valor padrão da lista | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lista de produtos Classificar por | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir todos os produtos por página | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar categoria de catálogo simples | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar produto de catálogo simples | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Amostras por produto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir que os convidados escrevam comentários | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Alerta Quando O Preço Do Produto Mudar | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de alerta de preço | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alerta quando o produto retornar ao estoque | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de email de alerta do Stock | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente do e-mail de alerta | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro de remetente de email | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro no modelo de e-mail | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar para atual | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contagem padrão de produtos visualizados recentemente | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contagem Padrão de Produtos Recentemente Comparados | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Início automático do vídeo base | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar vídeo relacionado | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vídeo de reinicialização automática | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Escopo do Preço de Catálogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preço de Produto Padrão | `catalog/price/default_product_price` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Exibir Contagem de Produtos | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo da Etapa de Navegação de Preço | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etapa de Navegação de Preço Padrão | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Intervalo de Preço como Um Preço | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de intervalos de preço | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de Divisão de Intervalo | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidade máxima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Comprimento mínimo da consulta | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho máximo da consulta | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mecanismo de pesquisa | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite do servidor Solr | `catalog/search/solr_server_timeout` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de indexação | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Sugestões de Pesquisa | `catalog/search/search_suggestion_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Contagem de Sugestões de Pesquisa | `catalog/search/search_suggestion_count` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar a contagem de resultados para cada sugestão | `catalog/search/search_suggestion_count_results_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar recomendações de pesquisa | `catalog/search/search_recommendations_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Contagem de recomendações de pesquisa | `catalog/search/search_recommendations_count` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar Contagem de Resultados para Cada Recomendação | `catalog/search/search_recommendations_count_results_enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Termos mínimos para corresponder | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar regravações de URL de &quot;categoria/produto&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Termos de pesquisa populares | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo do URL do produto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo do URL da categoria | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar caminho de categorias para URLs de produtos | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Criar redirecionamento permanente para URLs se a chave do URL for alterada | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separador de título de página | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Meta Tag De Link Canônico Para Categorias | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar A Meta Tag Do Link Canônico Para Produtos | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar | `catalog/magento_catalogpermissions/enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir Categoria de Navegação | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de Clientes | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Landing Page | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Exibir preços do produto | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de Clientes | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir adição ao carrinho | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de Clientes | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Não permitir pesquisa no catálogo por | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Status do item do pedido para habilitar downloads | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo padrão de downloads | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartilhável | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de amostra padrão | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título do link padrão | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abrir links em nova janela | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar descarte de conteúdo | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desabilitar Check-out de Convidado se o carrinho contiver itens baixáveis | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar calendário do JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem dos campos de data | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de hora | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo de anos | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar a funcionalidade de eventos de catálogo | `catalog/magento_catalogevent/enabled` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar widget de evento do catálogo na loja | `catalog/magento_catalogevent/lister_output` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número de eventos a serem exibidos no Widget do controle deslizante do evento | `catalog/magento_catalogevent/lister_widget_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Eventos para rolar por clique no Widget de controle deslizante do evento | `catalog/magento_catalogevent/lister_widget_scroll` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos relacionados | `catalog/magento_targetrule/related_position_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos relacionados | `catalog/magento_targetrule/related_position_behavior` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos relacionados | `catalog/magento_targetrule/related_rotation_mode` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos de venda cruzada | `catalog/magento_targetrule/crosssell_position_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos de venda cruzada | `catalog/magento_targetrule/crosssell_position_behavior` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos de venda cruzada | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos de venda adicional | `catalog/magento_targetrule/upsell_position_limit` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos de venda adicional | `catalog/magento_targetrule/upsell_position_behavior` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos de venda adicional | `catalog/magento_targetrule/upsell_rotation_mode` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos de inventário

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Inventário**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Diminuir Estoque Quando o Pedido for Feito | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Definir status dos itens para em estoque quando o pedido for cancelado | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Produtos sem Estoque | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite esquerdo somente X | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir a disponibilidade dos produtos em estoque na loja | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizar com catálogo | `cataloginventory/options/synchronize_with_catalog` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Gerenciar estoque | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordens pendentes | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar atualização de estoque adiada | `cataloginventory/item_options/use_deferred_stock_update` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Quantidade Máxima Permitida no Carrinho de Compras | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de indisponibilidade | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantidade Mínima Permitida no Carrinho de Compras | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificar para Quantidade Inferior | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar incrementos de quantidade | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementos de Qtd. | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devolver automaticamente o item do aviso de crédito ao estoque | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Executar de forma assíncrona | `cataloginventory/bulk_operations/async` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Tamanho assíncrono do lote | `cataloginventory/bulk_operations/batch_size` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Provedor | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de cálculo | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos do Visual Merchandiser

[!BADGE Somente PaaS]{type=Informative url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplica-se somente a projetos do Adobe Commerce na nuvem (infraestrutura do PaaS gerenciada pela Adobe) e a projetos locais."}

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Merchandiser Visual**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Atributos Visíveis para Regras de Categoria | `visualmerchandiser/options/smart_attributes` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite Mínimo de Estoque | `visualmerchandiser/options/minimum_stock_threshold` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Código do atributo de cor | `visualmerchandiser/options/color_attribute_code` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordem das cores | `visualmerchandiser/options/color_order` | ![Somente Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos do mapa de site XML

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Mapa de Site XML**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Frequência | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridade | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridade | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adicionar imagens ao mapa do site | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridade | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativado | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro de remetente de email | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erro no modelo de e-mail | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de URLs por arquivo | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho máximo do arquivo | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar envio para Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de RSS Feeds

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **RSS Feeds**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Habilitar RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novos produtos | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos especiais | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cupons/Descontos | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoria de nível superior | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificação de status do pedido do cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Enviar email para um amigo caminhos

Estes valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Enviar email para um Amigo**.

| Nome | Caminho de configuração | Somente Commerce? |
|--------------|--------------|--------------|
| Ativado | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Selecionar modelo de e-mail | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir Convidados | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de destinatários | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de Produtos Enviados em 1 Hora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limitar envio por | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
