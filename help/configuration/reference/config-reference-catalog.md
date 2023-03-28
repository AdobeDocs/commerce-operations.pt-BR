---
title: Referência de caminhos de configuração do catálogo
description: Consulte uma lista de valores de configuração de catálogo.
source-git-commit: e4b7ea70b96143629b245409537459ad259393e0
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---


# Referência de caminhos de configuração do catálogo

Esta seção lista os nomes das variáveis e os caminhos de configuração disponíveis para as opções em Admin em **Lojas** > Configurações > **Configuração** > **Catálogo**.

O [`magento app:config:dump` comando](../cli/export-configuration.md) grava esses valores no arquivo de configuração compartilhado, `app/etc/config.php`, que deve estar no controle de origem. Como opção, para substituir qualquer configuração ou definir configurações confidenciais, consulte [Usar variáveis de ambiente para substituir configurações](override-config-settings.md#environment-variables). Este tópico faz _not_ lista [valores sensíveis e específicos do sistema](config-reference-sens.md).

## Caminhos do catálogo

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Máscara para SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para Título Meta | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mascarar palavras-chave Meta | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para Meta-Descrição | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de lista | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página em valores permitidos na grade | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página no valor padrão da grade | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página na lista de valores permitidos | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos por página na lista Valor padrão | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listagem do Produto Classificar por | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir todos os produtos por página | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar categoria de catálogo simples | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar produto de catálogo simples | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Amostras por produto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir que convidados gravem revisões | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alerta quando o preço do produto for alterado | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Alerta de Preço | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alerta quando o produto voltar ao estoque | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Alerta de Estoque | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email de alerta | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequência | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de início | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remetente de email de erro | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Erro | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar para Atual | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contagem de Produtos Visualizados Recentemente Padrão | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contagem de Produtos Comparados Recentemente Padrão | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Iniciar automaticamente o vídeo base | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar vídeo relacionado | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reiniciar o vídeo automaticamente | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Escopo do Preço do Catálogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Preço padrão do produto | `catalog/price/default_product_price` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir contagem de produtos | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo da Etapa de Navegação de Preço | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etapa de Navegação de Preço Padrão | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Intervalo de Preço como Um Preço | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número Máximo de Intervalos de Preço | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite da Divisão de Intervalo | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidade máxima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho mínimo da consulta | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho máximo da consulta | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mecanismo de pesquisa | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo limite do servidor Solr | `catalog/search/solr_server_timeout` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de indexação | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar sugestões de pesquisa | `catalog/search/search_suggestion_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Contagem de Sugestões de Pesquisa | `catalog/search/search_suggestion_count` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar contagem de resultados para cada sugestão | `catalog/search/search_suggestion_count_results_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar o Search Recommendations | `catalog/search/search_recommendations_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Contagem de Recommendations de Pesquisa | `catalog/search/search_recommendations_count` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar contagem de resultados para cada recomendação | `catalog/search/search_recommendations_count_results_enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mínimo de termos para correspondência | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerar substituições de URL de &quot;categoria/produto&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Termos de pesquisa popular | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo do URL do produto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufixo de URL da categoria | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar caminho de categorias para URLs de produto | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Criar redirecionamento permanente para URLs se a chave do URL for alterada | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separador de título da página | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Meta Tag De Link Canônico Para Categorias | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Meta Tag Canonical Link Para Produtos | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar | `catalog/magento_catalogpermissions/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir Categoria de Navegação | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Página de aterrissagem | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Exibir preços do produto | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Permitir adição ao carrinho | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Não permitir pesquisa no catálogo por | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Solicite o status do item para habilitar downloads | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo padrão de downloads | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartilhável | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de exemplo padrão | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título do link padrão | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abrir links em nova janela | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar disposição de conteúdo | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desative o check-out de convidado se o carrinho contiver itens baixáveis | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar calendário do JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordem dos campos de data | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de hora | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo de Ano | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar a funcionalidade Eventos de catálogo | `catalog/magento_catalogevent/enabled` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ativar o widget de evento de catálogo na loja | `catalog/magento_catalogevent/lister_output` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Número de eventos a serem exibidos no widget controle deslizante do evento | `catalog/magento_catalogevent/lister_widget_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Eventos a serem rolados por clique no widget controle deslizante do evento | `catalog/magento_catalogevent/lister_widget_scroll` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos relacionados | `catalog/magento_targetrule/related_position_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos relacionados | `catalog/magento_targetrule/related_position_behavior` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos relacionados | `catalog/magento_targetrule/related_rotation_mode` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos de venda cruzada | `catalog/magento_targetrule/crosssell_position_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos de venda cruzada | `catalog/magento_targetrule/crosssell_position_behavior` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos de venda cruzada | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de produtos na lista de produtos de venda adicional | `catalog/magento_targetrule/upsell_position_limit` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Mostrar produtos de venda adicional | `catalog/magento_targetrule/upsell_position_behavior` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotação para produtos na lista de produtos de venda adicional | `catalog/magento_targetrule/upsell_rotation_mode` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos de inventário

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Inventário**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Diminuir estoque quando a ordem é feita | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Definir o status dos itens em estoque quando a ordem for cancelada | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir produtos fora de estoque | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite esquerdo de apenas X | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exibir Disponibilidade de Produtos em Estoque na Loja | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizar com Catálogo | `cataloginventory/options/synchronize_with_catalog` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Gerenciar estoque | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Backorders | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar atualização de estoque adiado | `cataloginventory/item_options/use_deferred_stock_update` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Quantidade máxima permitida no carrinho de compras | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite esgotado | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantidade mínima permitida no carrinho de compras | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificar para Quantidade Abaixo | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar incrementos de quantidade | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementos de Qtd | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Retornar Automaticamente Item de Aviso de Crédito para Estoque | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Executar de forma assíncrona | `cataloginventory/bulk_operations/async` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Tamanho assíncrono do lote | `cataloginventory/bulk_operations/batch_size` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Provedor | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo Computação | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de merchandising visual

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Comerciante visual**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Atributos visíveis para regras de categoria | `visualmerchandiser/options/smart_attributes` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Limite Mínimo de Estoque | `visualmerchandiser/options/minimum_stock_threshold` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Código de atributo de cor | `visualmerchandiser/options/color_attribute_code` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |
| Ordem de cor | `visualmerchandiser/options/color_order` | ![Somente comércio](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Caminhos do mapa de site XML

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Mapa do Site XML**.

| Nome | Caminho de configuração | Somente comércio? |
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
| Remetente de email de erro | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modelo de Email de Erro | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de URLs por arquivo | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamanho máximo de arquivo | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar envio para Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Caminhos de feeds RSS

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Feeds RSS**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativar RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ativar RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Novos produtos | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produtos especiais | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cupons/Descontos | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoria de nível superior | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificação de status do pedido do cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Enviar email para caminhos de amigos

Esses valores de configuração estão disponíveis no Administrador em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Enviar email para um amigo**.

| Nome | Caminho de configuração | Somente comércio? |
|--------------|--------------|--------------|
| Ativado | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Selecionar modelo de email | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir para convidados | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de recipients | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de produtos enviados em 1 hora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limitar envio por | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
