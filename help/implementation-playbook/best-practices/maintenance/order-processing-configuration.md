---
title: Práticas recomendadas de configuração para processamento de pedidos
description: Conheça as práticas recomendadas de configuração para melhorar o desempenho do processamento de check-out e pedidos.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%
---
# Práticas recomendadas de configuração para processamento de pedidos

À medida que o volume do pedido aumenta nos sites do Commerce, você pode otimizar o desempenho do check-out e o processamento de pedidos ativando as seguintes opções de configuração da loja:

- **[!UICONTROL Asynchronous indexing]**—Habilite esta opção para evitar bloqueios de banco de dados e processamento lento que podem ocorrer quando um grande número de pedidos é feito simultaneamente.
- **[!UICONTROL Asynchronous email notifications]**—Habilite esta opção para acelerar o desempenho do check-out enviando check-out e notificações de email de processamento de pedidos em intervalos designados, em vez de enviá-los imediatamente.
- **[!UICONTROL Enable Archiving]**—Habilite esta opção para melhorar o desempenho de pedidos, faturas, remessas e avisos de crédito, e manter seu espaço de trabalho livre de informações desnecessárias, para que você possa se concentrar nos negócios atuais. Consulte [Habilitar arquivamento](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Produtos e versões afetados

[Todas as versões &#x200B;](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Habilitar processamento assíncrono de pedidos

As etapas para habilitar o processamento assíncrono de pedidos dependem do modo de implantação:

- Para o Adobe Commerce na infraestrutura em nuvem e sites locais no modo de Produção, use o seguinte comando da CLI da Magento para habilitar a indexação assíncrona:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Para sites locais do Adobe Commerce no modo Padrão ou de Produção, habilite a indexação assíncrona atualizando a configuração de Configurações de Grade no Administrador.

  Consulte [Habilitar atualizações de grade agendadas e reindexação](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html?lang=pt-BR#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Sempre teste as alterações de configuração no ambiente de preparo antes de atualizar o ambiente de produção.

## Informações adicionais

- [Práticas recomendadas de configuração](../../../performance/configuration.md)
- [Referência de caminhos de configuração gerais e avançados](../../../configuration/reference/config-reference-general.md)
- [Processamento de pedidos com alto rendimento](../../../performance/high-throughput-order-processing.md)
