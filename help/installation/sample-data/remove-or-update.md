---
title: Remover ou atualizar módulos de dados de amostra
description: Siga estas etapas para gerenciar módulos de dados de amostra do Adobe Commerce.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%
---
# Remover ou atualizar módulos de dados de amostra

Este tópico discute como:

* [Remover módulos de dados de exemplo](#remove-sample-data-modules) de uma instalação do Adobe Commerce `composer.json`. Esta opção *não* remove dados de amostra do banco de dados.

* [Prepare-se para atualizar dados de amostra](#prepare-to-update-sample-data) (por exemplo, antes de atualizar o aplicativo Magento).

## Remover módulos de dados de amostra

Digite o seguinte comando:

```shell
bin/magento sampledata:remove
```

A lista completa de módulos de dados de exemplo é a seguinte:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

## Preparação para atualizar dados de amostra

Esse comando permite atualizar dados de amostra antes de atualizar o Adobe Commerce.

Para preparar dados de amostra para atualização, insira o seguinte comando:

```shell
bin/magento sampledata:reset
```

Depois disso, [atualize o aplicativo](../tutorials/uninstall.md#update-the-application).
