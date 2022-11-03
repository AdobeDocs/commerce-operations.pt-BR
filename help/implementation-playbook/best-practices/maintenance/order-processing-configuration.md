---
title: Práticas recomendadas de configuração para processamento de pedidos
description: Saiba mais sobre as práticas recomendadas de configuração para melhorar o desempenho do check-out e do processamento de pedidos.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Práticas recomendadas de configuração para processamento de pedidos

À medida que o volume do pedido aumenta em seus sites de Comércio, você pode otimizar o desempenho do check-out e o processamento de pedidos, habilitando as seguintes opções de configuração de loja:

- **[!UICONTROL Asynchronous indexing]**—Ative essa opção para impedir bloqueios de banco de dados e processamento lento que podem ocorrer quando grandes números de pedidos são colocados simultaneamente.
- **[!UICONTROL Asynchronous email notifications]**—Ative essa opção para acelerar o desempenho do check-out, enviando notificações por email de check-out e processamento de pedidos em intervalos designados, em vez de enviá-las imediatamente.
- **[!UICONTROL Enable Archiving]**—Ative essa opção para arquivar pedidos e liberar espaço em disco do banco de dados para processamento de pedidos mais rápido. Consulte [Ativar arquivamento](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Ativar processamento assíncrono de pedidos

As etapas para habilitar o processamento assíncrono de pedidos dependem do modo de implantação:

- Para o Adobe Commerce na infraestrutura de nuvem e sites locais no modo Produção, use o seguinte comando Magento CLI para habilitar a indexação assíncrona:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Para sites no local do Adobe Commerce no modo Padrão ou Produção, ative a indexação assíncrona atualizando a configuração Configurações de Grade no Administrador.

   Consulte [Ativar atualizações e reindexação de grade agendadas](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Sempre teste as alterações de configuração no ambiente de preparo antes de atualizar o ambiente de produção.

## Informações adicionais

- [Práticas recomendadas de configuração](../../../performance/configuration.md)
- [Referência de caminhos de configuração gerais e avançados](../../../configuration/reference/config-reference-general.md)
- [Processamento de pedidos com alta taxa de transferência](../../../performance/high-throughput-order-processing.md)
