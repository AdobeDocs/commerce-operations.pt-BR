---
title: Consumidores de fila de mensagens
description: Saiba mais sobre os consumidores de fila de mensagens Adobe Commerce e Magento Open Source, incluindo os recursos e as configurações do sistema associadas a eles.
source-git-commit: f9db986510a3ec8e62b9d628da40fdfd9741479f
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---


# Consumidores de fila de mensagens

A tabela a seguir identifica todos os consumidores da fila de mensagens, descreve o que eles fazem e identifica as configurações do sistema administrativo associadas a eles:

| Consumidor e descrição | Adobe Commerce | Adobe Commerce com B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Cria mensagens para cada tarefa individual de um [operação em massa](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar ou exportar itens, alterar preços em escala de massa e atribuir produtos a um depósito. Obrigatório quando a variável [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) está definida como **[!UICONTROL Run asynchronously]**nas configurações do sistema de administração. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Gera cupons de forma assíncrona em segundo plano. Obrigatório para usar o [geração de cupom em lote](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) recurso. |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| Verifica se há eventos que foram registrados como prioridade em [Adobe I/O Events para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Impede limites de tempo de conexão durante a [exportar](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de dados (por exemplo, 200.000 produtos). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corrige de forma assíncrona o índice de estoque depois que um pedido é feito ou um produto é removido. Obrigatório quando a variável [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) está ativada nas configurações do Administrador. Consulte [Práticas recomendadas de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Exclui de forma assíncrona os itens de origem por SKU de produto quando um produto é removido. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) a opção de estoque está ativada nas configurações do sistema administrativo. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Processa de forma assíncrona itens de estoque herdados, atualiza itens de estoque herdados, atualiza itens de origem padrão e reindexa o inventário para SKUs de produtos específicos. Obrigatório quando a variável [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) a operação em massa é ativada nas configurações do sistema de administração. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Exclui de forma assíncrona as reservas por SKU de produto após a remoção de um produto. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) a opção de estoque está ativada nas configurações do sistema administrativo. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Atualiza de forma assíncrona as reservas por SKU de produto após a remoção de um produto. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) a opção de estoque está ativada nas configurações do sistema administrativo. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Atualiza de forma assíncrona a quantidade comercializável de cada produto atribuído a um estoque. Esse consumidor deve estar sempre ativo e em execução se você estiver usando [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa de forma assíncrona os itens de origem. Obrigatório quando a variável [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definida como &quot;[!UICONTROL asynchronous]&quot; nas configurações do sistema de administração. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Refaz de forma assíncrona o estoque. Obrigatório quando a variável [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definida como &quot;[!UICONTROL asynchronous]&quot; nas configurações do sistema de administração. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Cria uma tabela de banco de dados temporária, move cada [segmento de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) nela, o exclui todos os segmentos que correspondem à ID do segmento e os copia para os segmentos do cliente usando a ID do segmento como indicador. Isso é feito em uma transação para que, se algo falhar, ele reverta a transação para o que foi antes de ser executado. Após uma transação, o consumidor abandona a tabela temporária. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Garante que os links para a mídia atribuída para produtos, categorias, blocos CMS e páginas CMS sejam atribuídos corretamente ao ativo. Remove ativos antigos que não são mais usados. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Gera e valida caminhos de ativos de mídia. O caminho absoluto para um ativo é determinado pelo local em que ele fica no servidor de dentro do diretório de mídia. As imagens são redimensionadas (se necessário) e copiadas para o diretório de mídia dentro do caminho gerado. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Importa arquivos de imagem para o `media_gallery_asset` tabela de banco de dados. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Assíncrono [redimensionamento](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) imagens de catálogo. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Atualiza os preços das cotações negociáveis. Obrigatório quando a variável [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Assíncrono [ordens de processos](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), que marca os pedidos como recebidos, os coloca na fila de mensagens e os processa em uma base de primeiro a sair. Considerado um [prática recomendada](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para melhorar o número de pedidos que podem ser processados porque os clientes não precisam aguardar a conclusão dos processos de back-end antes de verem uma mensagem de sucesso. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Grava de forma assíncrona alterações em atributos de produto no banco de dados depois de usar o Administrador em [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Grava de forma assíncrona alterações em atributos de produto para uma exibição de loja específica no banco de dados depois de usar o Administrador do para [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Envia emails de notificação para clientes sobre alterações de preço do produto e inventário. Obrigatório quando Obrigatório quando [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Converte a ordem de compra em [pedido](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Envia emails de pedido de compra. Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Valida a ordem de compra em relação ao relevante [regras de aprovação](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Impede que [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) onde os cupons de uso único podem ser usados várias vezes. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Atualiza categorias atribuídas a uma categoria de catálogo compartilhado. Obrigatório quando a variável [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Atualiza o preço de cada produto em um catálogo compartilhado. Obrigatório quando a variável [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Exclui aspas de preço inválidas ou inativas quando um produto é excluído do catálogo ou removido do carrinho. Obrigatório quando a variável [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está ativada nas configurações do sistema administrativo. |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Atualiza os carrinhos de compras ativos para refletir as alterações na regra de preço do carrinho. Necessário ao atualizar [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
