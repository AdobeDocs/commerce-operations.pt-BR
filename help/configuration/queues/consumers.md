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
| Cria mensagens para cada tarefa individual de um [operação em massa](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar ou exportar itens, alterar preços em uma escala em massa e atribuir produtos a um depósito. Obrigatório quando a variável [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) está definida como **[!UICONTROL Run asynchronously]**nas configurações do sistema Admin. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Gera cupons de forma assíncrona em segundo plano. Obrigatório para usar o [geração de cupom em lote](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) recurso. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Verifica eventos que foram registrados como prioridade em [Eventos Adobe I/O para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Evita tempos limite de conexão durante o [exportar](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de dados (por exemplo, 200.000 produtos). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de forma assíncrona o índice de estoque depois que um pedido é feito ou um produto é removido. Obrigatório quando a variável [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) está habilitada nas configurações de Admin. Consulte [Práticas recomendadas de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Exclui de forma assíncrona os itens de origem por SKU de produto quando um produto é removido. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) A opção de estoque está habilitada nas configurações do Admin System. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Processa de forma assíncrona itens de estoque herdados, atualiza itens de estoque herdados, atualiza itens de origem padrão e reindexa o estoque para SKUs de produtos específicos. Obrigatório quando a variável [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) a operação em massa está habilitada nas configurações do sistema de administração. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Exclui de forma assíncrona as reservas por SKU de produto após a remoção de um produto. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) A opção de estoque está habilitada nas configurações do Admin System. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Atualiza de forma assíncrona as reservas por SKU do produto depois que um produto é removido. Obrigatório quando a variável [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) A opção de estoque está habilitada nas configurações do Admin System. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Atualiza de forma assíncrona a quantidade vendável de cada produto atribuído a um estoque. Esse consumidor deve estar sempre ativo e em funcionamento se você estiver usando [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa itens de origem de forma assíncrona. Obrigatório quando a variável [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definido como &quot;[!UICONTROL asynchronous]&quot; nas configurações do sistema Admin. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Reindexa o estoque de forma assíncrona. Obrigatório quando a variável [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) está definido como &quot;[!UICONTROL asynchronous]&quot; nas configurações do sistema Admin. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Cria uma tabela de banco de dados temporária, move cada [segmento de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) nele, exclui todos os segmentos que correspondem à ID do segmento e os copia para os segmentos do cliente usando a ID do segmento como indicador. Tudo isso é feito em uma transação para que, se algo falhar, ela reverta a transação para o que era antes de ser executada. Após uma transação, o consumidor descarta a tabela temporária. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garante que os links para mídia atribuída para produtos, categorias, blocos de CMS e páginas CMS sejam atribuídos corretamente ao ativo. Remove ativos antigos que não são mais usados. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Gera e valida caminhos de ativos de mídia. O caminho absoluto para um ativo é determinado pelo local no servidor dentro do diretório de mídia. As imagens são redimensionadas (se necessário) e copiadas para o diretório de mídia dentro do caminho gerado. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importa arquivos de imagem para o `media_gallery_asset` tabela de banco de dados. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| De forma assíncrona [redimensiona](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) imagens do catálogo. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Atualiza preços para cotações negociáveis. Obrigatório quando a variável [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| De forma assíncrona [processa ordens](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)O, que marca os pedidos como recebidos, os coloca na fila de mensagens e os processa com base no &quot;primeiro a entrar, primeiro a sair&quot;. Considerado um [prática recomendada](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para melhorar o número de pedidos que podem ser processados porque os clientes não precisam aguardar a conclusão dos processos de backend antes de ver uma mensagem de sucesso. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Grava de forma assíncrona as alterações nos atributos do produto no banco de dados após usar o Administrador para [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Grava de forma assíncrona as alterações nos atributos do produto para uma exibição da loja específica no banco de dados após usar o Administrador para [fazer atualizações](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Envia emails de notificação para clientes sobre alterações de preço e estoque do produto. Obrigatório quando o campo Obrigatório quando a variável [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Converte a ordem de compra em [pedido](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envia emails de ordem de compra. Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valida a ordem de compra em relação aos itens relevantes [regras de aprovação](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obrigatório quando a variável [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Salva de forma assíncrona as alterações na configuração do armazenamento, colocando trabalhos de salvamento em uma fila de mensagens, o que pode melhorar o desempenho em implantações que contêm um grande número de configurações no nível do armazenamento. Obrigatório para usar o [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) módulo. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Impede que o [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) onde os cupons de uso único podem ser usados várias vezes. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Atualiza categorias atribuídas a uma categoria de catálogo compartilhado. Obrigatório quando a variável [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Atualiza o preço de cada produto em um catálogo compartilhado. Obrigatório quando a variável [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Exclui cotações de preço inválidas ou inativas quando um produto é excluído do catálogo ou removido do carrinho. Obrigatório quando a variável [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está habilitada nas configurações do Admin System. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Atualiza os carrinhos de compras ativos para refletir as alterações na regra de preço do carrinho. Obrigatório ao atualizar [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
