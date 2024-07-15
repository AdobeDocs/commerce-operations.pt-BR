---
title: Consumidores da fila de mensagens
description: Saiba mais sobre os consumidores da fila de mensagens do Adobe Commerce, incluindo os recursos e as configurações do sistema associados a eles.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Consumidores da fila de mensagens

A tabela a seguir identifica todos os consumidores de fila de mensagens, descreve o que eles fazem e identifica as definições de configuração do sistema de administração associadas a eles:

| Consumidor e descrição | Adobe Commerce | Adobe Commerce com B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Cria mensagens para cada tarefa individual de uma [operação em massa](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar ou exportar itens, alterar preços em uma escala em massa e atribuir produtos a um depósito. Necessário quando a opção [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) está definida como **[!UICONTROL Run asynchronously]**nas definições de configuração do sistema de Administração. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Gera cupons de forma assíncrona em segundo plano. É necessário usar o recurso [geração de cupom em lote](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Verifica eventos que foram registrados como prioridade em [Adobe I/O Eventos para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Impede o tempo limite de conexão durante a [exportação](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de dados (por exemplo, 200.000 produtos). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de forma assíncrona o índice de estoque depois que um pedido é feito ou um produto é removido. Necessário quando a opção [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) está habilitada nas definições de configuração de Administração. Consulte [Práticas recomendadas de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Exclui de forma assíncrona os itens de origem por SKU de produto quando um produto é removido. Necessário quando a opção de estoque [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) está habilitada nas configurações do sistema de administração. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Processa de forma assíncrona itens de estoque herdados, atualiza itens de estoque herdados, atualiza itens de origem padrão e reindexa o estoque para SKUs de produtos específicos. Necessário quando a operação em massa [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) está habilitada nas configurações do sistema de administração. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Exclui de forma assíncrona as reservas por SKU de produto após a remoção de um produto. Necessário quando a opção de estoque [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) está habilitada nas configurações do sistema de administração. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Atualiza de forma assíncrona as reservas por SKU do produto depois que um produto é removido. Necessário quando a opção de estoque [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) está habilitada nas configurações do sistema de administração. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Atualiza de forma assíncrona a quantidade vendável de cada produto atribuído a um estoque. Este consumidor deve estar sempre ativo e em execução se você estiver usando o [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa itens de origem de forma assíncrona. Necessário quando o [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definido como &quot;[!UICONTROL asynchronous]&quot; nas definições de configuração do sistema de Administração. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Reindexa o estoque de forma assíncrona. Necessário quando o [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definido como &quot;[!UICONTROL asynchronous]&quot; nas definições de configuração do sistema de Administração. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Cria uma tabela de banco de dados temporária, move cada [segmento de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) para ela, exclui todos os segmentos que correspondem à ID de segmento e os copia para os segmentos de clientes usando a ID de segmento como indicador. Tudo isso é feito em uma transação para que, se algo falhar, ela reverta a transação para o que era antes de ser executada. Após uma transação, o consumidor descarta a tabela temporária. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garante que os links para mídia atribuída para produtos, categorias, blocos de CMS e páginas CMS sejam atribuídos corretamente ao ativo. Remove ativos antigos que não são mais usados. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Gera e valida caminhos de ativos de mídia. O caminho absoluto para um ativo é determinado pelo local no servidor dentro do diretório de mídia. As imagens são redimensionadas (se necessário) e copiadas para o diretório de mídia dentro do caminho gerado. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importa arquivos de imagem para a tabela de banco de dados `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [redimensiona](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) imagens do catálogo de maneira assíncrona. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Atualiza preços para cotações negociáveis. Necessário quando a opção [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| [processa pedidos](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) de forma assíncrona, que marca pedidos como recebidos, os coloca na fila de mensagens e os processa com base no &quot;primeiro a entrar, primeiro a sair&quot;. Considerada uma [prática recomendada](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para melhorar o número de pedidos que podem ser processados porque os clientes não precisam aguardar a conclusão dos processos de back-end antes de ver uma mensagem de sucesso. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Grava de forma assíncrona as alterações nos atributos do produto no banco de dados após usar o Administrador para [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Grava de forma assíncrona as alterações nos atributos do produto para uma exibição de loja específica no banco de dados após usar o Administrador para [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Envia emails de notificação para clientes sobre alterações de preço e estoque do produto. Necessário quando a opção Necessário quando a opção [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está habilitada nas configurações do sistema de Administração. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Converte a ordem de compra em [ordem](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Necessário quando a opção [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envia emails de ordem de compra. Necessário quando a opção [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valida a ordem de compra em relação às [regras de aprovação](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html) relevantes. Necessário quando a opção [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Salva de forma assíncrona as alterações na configuração do armazenamento, colocando trabalhos de salvamento em uma fila de mensagens, o que pode melhorar o desempenho em implantações que contêm um grande número de configurações no nível do armazenamento. É necessário usar o módulo [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Impede o [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) em que cupons de uso único podem ser usados várias vezes. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Atualiza categorias atribuídas a uma categoria de catálogo compartilhado. Necessário quando a opção [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Atualiza o preço de cada produto em um catálogo compartilhado. Necessário quando a opção [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Exclui cotações de preço inválidas ou inativas quando um produto é excluído do catálogo ou removido do carrinho. Necessário quando a opção [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está habilitada nas definições de configuração do sistema de Administração. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Atualiza os carrinhos de compras ativos para refletir as alterações na regra de preço do carrinho. Necessário ao atualizar [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
