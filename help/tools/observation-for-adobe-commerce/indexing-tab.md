---
title: '"O [!UICONTROL Indexing] tab"'
description: Saiba mais sobre o [!UICONTROL Indexing] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# O [!UICONTROL Indexing] guia

O **[!UICONTROL Indexing]** A guia tenta explicar problemas com indexação e identificar possíveis causas.

## [!UICONTROL Core index invalidated]

![Índice principal invalidado](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

O **[!UICONTROL Core index invalidated]** O quadro observa a invalidação de indexação em um período selecionado. Se a indexação estiver acontecendo ao mesmo tempo que outros crons com muitos recursos, ela colocará uma carga pesada nos recursos do site.

* &#39;%Indexador de Regra de Produto do Catálogo foi invalidado%&#39;) como &#39;catalog_product_rule_idx_reset&#39;
* &#39;%Indexador de Produto de Regra de Catálogo foi invalidado%&#39;) como &#39;catalog_rule_product_idx_reset&#39;
* &#39;%Indexador de Pesquisa de Catálogo foi invalidado%&#39;) como &#39;catalog_search_idx_reset&#39;
* &#39;%O indexador de Produtos de Categoria foi invalidado%&#39;) como &#39;category_products_idx_reset&#39;
* &#39;%O indexador de Grade de Cliente foi invalidado%&#39;) como &#39;customer_grid_idx_reset&#39;
* &#39;%O indexador da Grade de Configuração de Design foi invalidado%&#39;) como &#39;design_config_grid_idx_
* &#39;%O indexador de Categorias de Produto foi invalidado%&#39;) como &#39;product_categories_idx_reset&#39;
* &#39;%O indexador EAV do produto foi invalidado%&#39;) como &#39;product_eav_idx_reset&#39;
* &#39;%O indexador de Preço do Produto foi invalidado%&#39;) como &#39;product_price_idx_reset&#39;
* &#39;%O indexador de estoque foi invalidado%&#39;) como &#39;stock_idx_reset&#39;
* &#39;%O indexador de inventário foi invalidado%&#39;) como &#39;inventory_idx_reset&#39;
* &#39;%O indexador de inventário foi invalidado%&#39;) como &#39;inventory_idx_reset&#39;
* &#39;%O indexador da Regra de Vendas foi invalidado%&#39;) como &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Recriações do índice principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

O **[!UICONTROL Core index rebuilds]** O quadro observa as recriações do índice principal em um período selecionado. Estas são as cadeias de caracteres analisadas dos logs para indicar a conclusão da reconstrução do índice.

* &#39;%O índice da Regra de Produto do Catálogo foi reconstruído%&#39;) como &#39;catalog_product_rule_idx&#39;
* &#39;%Catalog Rule Product index foi reconstruído%&#39;) como &#39;catalog_rule_product_idx&#39;
* &#39;%Índice de Pesquisa de Catálogo recriado%&#39;) como &#39;catalog_search_idx&#39;
* &#39;%O índice de Produtos de Categoria foi reconstruído com êxito%&#39;) como &#39;category_products_idx&#39;
* &#39;%Índice de Grade de Cliente foi reconstruído%&#39;) como &#39;customer_grid_idx&#39;
* &#39;%O índice da Grade de Configuração de Design foi reconstruído%&#39;) como &#39;design_config_grid_idx&#39;
* &#39;%O índice de Categorias de Produto foi reconstruído%&#39;) como &#39;product_categories_idx&#39;
* &#39;%O índice EAV do Produto foi reconstruído%&#39;) como &#39;product_eav_idx&#39;
* &#39;%Product Price index has rebuild%&#39;) como &#39;product_price_idx&#39;
* &#39;%Stock index foi reconstruído%&#39;) como &#39;stock_idx&#39;
* &#39;%O índice de inventário foi reconstruído com êxito%&#39;) como &#39;inventory_idx&#39;
* %O índice de Regra de Produto/Destino foi recriado com êxito%&#39;) como &#39;prod_target_rule_idx&#39;
* &#39;%O índice da Regra de Vendas foi reconstruído com êxito%&#39;) como &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![tabela(s) de índice catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

O **[!UICONTROL catalogsearch index table(s)]** o frame procura as tabelas de índice do catalogsearch em um período selecionado. Esta consulta está analisando a duração de quaisquer operações do armazenamento de dados em relação a tabelas com &quot;%catalogsearch%&quot; no nome da tabela.

## [!UICONTROL product index table(s)]

![tabela(s) de índice de produto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

O **[!UICONTROL product index table(s)]** O frame procura as tabelas do índice do produto em um período selecionado. Esta consulta está analisando a duração de quaisquer operações do armazenamento de dados em relação a tabelas com &quot;%product%&quot; no nome da tabela.
