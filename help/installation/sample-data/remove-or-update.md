---
title: Remover ou atualizar módulos de dados de amostra
description: Siga estas etapas para gerenciar módulos de dados de amostra Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Remover ou atualizar módulos de dados de amostra

Este tópico discute como:

* [Remover módulos de dados de amostra](#remove-sample-data-modules) de uma instalação Adobe Commerce ou Magento Open Source `composer.json`. Essa opção faz *not* remover dados de amostra do banco de dados.

* [Preparar para atualizar os dados de amostra](#prepare-to-update-sample-data) (por exemplo, antes de atualizar o aplicativo Magento).

## Remover módulos de dados de amostra

Digite o seguinte comando:

```bash
bin/magento sampledata:remove
```

A lista completa de módulos de dados de amostra é a seguinte:

Adobe Commerce e Magento Open Source:

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

Somente Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Preparar para atualizar os dados de amostra

Esse comando permite atualizar os dados de amostra antes de atualizar o Adobe Commerce ou o Magento Open Source.

Para preparar dados de amostra para atualização, insira o seguinte comando:

```bash
bin/magento sampledata:reset
```

Depois disso, [atualizar o aplicativo](../tutorials/uninstall.md#update-the-application).
