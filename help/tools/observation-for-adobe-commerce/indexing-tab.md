---
title: A variável [!UICONTROL Indexing] guia
description: Saiba mais sobre o [!UICONTROL Indexing] guia de [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# A variável [!UICONTROL Indexing] guia

A variável **[!UICONTROL Indexing]** A guia tenta explicar problemas com a indexação e identificar possíveis causas.

## [!UICONTROL Core index invalidated]

![Índice principal invalidado](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

A variável **[!UICONTROL Core index invalidated]** O quadro do verifica a invalidação de indexação em um período selecionado. Se a indexação estiver ocorrendo ao mesmo tempo que outras [!DNL crons], isso colocará uma grande carga nos recursos do site.

* `%Catalog Product Rule indexer has been invalidated%`) como `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) como `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) como `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) como `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) como `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) como `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) como `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) como `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) como `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) como `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) como `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) como `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) como `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Recriações do índice principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

A variável **[!UICONTROL Core index rebuilds]** O quadro do verifica as reconstruções do índice principal em um período selecionado. Estas são as cadeias de caracteres analisadas dos logs para indicar a conclusão da reconstrução do índice.

* `%Catalog Product Rule index has been rebuilt%`) como `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) como `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) como `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) como `category_products_idx`
* `%Customer Grid index has been rebuilt%`) como `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) como `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) como `product_categories_idx`
* `%Product EAV index has been rebuilt%`) como `product_eav_idx`
* `%Product Price index has been rebuilt%`) como `product_price_idx`
* `%Stock index has been rebuilt%`) como `stock_idx`
* `%Inventory index has been rebuilt successfully%`) como `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) como `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) como `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![tabela(s) de índice catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

A variável **[!UICONTROL catalogsearch index table(s)]** o quadro verifica as tabelas de índice catalogsearch em um período selecionado. Esta consulta analisa a duração de quaisquer operações de armazenamento de dados em relação a tabelas com `%catalogsearch%` no nome da tabela.

## [!UICONTROL product index table(s)]

![tabela(s) de índice de produto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

A variável **[!UICONTROL product index table(s)]** O quadro do verifica as tabelas de índice de produto em um período selecionado. Esta consulta analisa a duração de quaisquer operações de armazenamento de dados em relação a tabelas com `%product%` no nome da tabela.
