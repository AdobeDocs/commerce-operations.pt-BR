---
title: Práticas recomendadas de configuração para processamento de pedidos
description: Conheça as práticas recomendadas de configuração para melhorar o desempenho do processamento de check-out e pedidos.
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Práticas recomendadas de configuração para processamento de pedidos

À medida que o volume de pedidos aumenta nos sites do Commerce, você pode otimizar o desempenho de finalização de compra e o processamento de pedidos, ativando as seguintes opções de configuração da loja:

- **[!UICONTROL Asynchronous indexing]**—Ative esta opção para evitar bloqueios de bancos de dados e processamento lento que podem ocorrer quando grandes números de pedidos são feitos simultaneamente.
- **[!UICONTROL Asynchronous email notifications]**—Ative essa opção para acelerar o desempenho do check-out enviando notificações por email de check-out e processamento de pedidos em intervalos designados, em vez de enviá-las imediatamente.
- **[!UICONTROL Enable Archiving]**—Ative esta opção para melhorar o desempenho de ordens, NFFs, entregas e avisos de crédito e manter seu espaço de trabalho livre de informações desnecessárias, para que você possa se concentrar nos negócios atuais. Consulte [Ativar arquivamento](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Habilitar processamento assíncrono de pedidos

As etapas para habilitar o processamento assíncrono de pedidos dependem do modo de implantação:

- Para o Adobe Commerce na infraestrutura em nuvem e sites locais no modo de produção, use o seguinte comando da CLI do Magento para habilitar a indexação assíncrona:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Para sites locais do Adobe Commerce no modo Padrão ou de Produção, habilite a indexação assíncrona atualizando a configuração de Configurações de Grade no Administrador.

   Consulte [Habilitar atualizações e reindexação de grade programadas](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Sempre teste as alterações de configuração no ambiente de preparo antes de atualizar o ambiente de produção.

## Informações adicionais

- [Práticas recomendadas de configuração](../../../performance/configuration.md)
- [Referência de caminhos de configuração gerais e avançados](../../../configuration/reference/config-reference-general.md)
- [Processamento de pedidos com alto rendimento](../../../performance/high-throughput-order-processing.md)
