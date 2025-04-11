---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '2906'
ht-degree: 0%

---
# Pacotes Adobe Commerce

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

O Adobe Commerce usa o Composer para gerenciar pacotes PHP.

O arquivo `composer.json` declara a lista de pacotes, enquanto o arquivo `composer.lock` armazena uma lista completa dos pacotes (uma versão completa de cada pacote e suas dependências) usados para criar uma instalação do Adobe Commerce.

A documentação de referência a seguir é gerada a partir do arquivo `composer.lock` e abrange os pacotes necessários incluídos no Adobe Commerce 2.4.8.

## Dependências

`magento/product-enterprise-edition 2.4.8` tem as seguintes dependências:

- adobe-commerce/extensions-metappackage: 2.0.1
- colinmollenhour/arquivo-back-end-cache: ^1.4
- colinmollenhour/cache-backend-redis: ^1,16
- colinmollenhour/credis: ^1.15
- colinmollenhour/php-redis-session-abstract: ^2,0
- compositor/compositor: ^2.0, !=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1,0
- elasticsearch/elasticsearch: ^8,15
- ext-bcmath: *
- tipo de texto: *
- ext-curl: *
- ext-dom: *
- ext-ftp: *
- ext-gd: *
- ext-hash: *
- ícone de texto: *
- ext-intl: *
- ext-mbstring: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- ext-soap: *
- Extrato-sódio: *
- ext-spl: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlpurifier: ^4,17
- guzzlehttp/guzzle: ^7,5
- laminas/laminas-captcha: ^2,18
- código laminas/laminas: ^4.13
- laminas/laminas-di: ^3,15
- laminas/laminas-escaper: ^2.13
- laminas/laminas-eventmanager: ^3,11
- laminas/laminas-feed: ^2,22
- laminas-filtro: ^2,33
- laminas/laminas-http: ^2,15
- laminas/laminas-i18n: ^2,17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3,6
- laminas/laminas-permissions-acl: ^2,10
- laminas/laminas-servicemanager: ^3,16
- laminas/laminas-soap: ^2,10
- laminas/laminas-stdlib: ^3,11
- laminas/laminas-uri: ^2,9
- validador de laminas/laminas: ^2,23
- league/flysystem: ^3,0
- league/flysystem-aws-s3-v3: ^3,0
- lib-libxml: *
- magento/composer: ^1.10.1-beta1
- magento/composer-dependency-version-audit-plugin: ^0.1
- magento/framework-foreign-key: 100.4.7
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3,21
- magento/magento2-ee-base: 2.4.8
- [magento/module-admin-gws](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws/): 100.4.8
- [magento/module-admin-gws-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-configurable-product/): 100.4.5
- [magento/module-admin-gws-staging](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-staging/): 100.4.5
- [magento/module-advanced-catalog](https://developer.adobe.com/commerce/php/module-reference/module-advanced-catalog/): 100.4.5
- [magento/module-advanced-checkout](https://developer.adobe.com/commerce/php/module-reference/module-advanced-checkout/): 100.4.8
- [magento/module-advanced-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-rule/): 100.4.5
- [magento/module-advanced-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-sales-rule/): 100.4.5
- [magento/module-application-server](https://developer.adobe.com/commerce/php/module-reference/module-application-server/): 100.4.1
- [magento/module-application-server-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-server-new-relic/): 100.4.1
- [magento/module-application-server-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-performance-monitor/): 100.4.1
- [magento/module-application-server-state-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor/): 100.4.1
- [magento/module-application-server-state-monitor-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor-graph-ql/): 100.4.1
- [magento/module-async-order](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): 100.4.4
- [magento/module-async-order-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-async-order-graph-ql/): 100.4.3
- [magento/module-aws-s3-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-customer-custom-attributes/): 100.4.5
- [magento/module-aws-s3-vale-presente-importação-exportação](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-gift-card-import-export/): 100.4.5
- [magento/module-aws-s3-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-scheduled-import-export/): 100.4.5
- [magento/module-banner](https://developer.adobe.com/commerce/php/module-reference/module-banner/): 101.2.8
- [magento/module-banner-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-banner-customer-segment/): 100.4.6
- [magento/module-banner-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-banner-graph-ql/): 100.4.4
- [magento/module-banner-staging](https://developer.adobe.com/commerce/php/module-reference/module-banner-staging/): 100.4.2
- [magento/module-bundle-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export-staging/): 100.4.5
- [magento/module-bundle-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-staging/): 100.4.8
- [magento/module-catalog-event](https://developer.adobe.com/commerce/php/module-reference/module-catalog-event/): 101.1.7
- [magento/module-catalog-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export-staging/): 100.4.5
- [magento/module-catalog-inventory-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-staging/): 100.4.6
- [magento/module-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions/): 100.4.8
- [magento/module-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions-graph-ql/): 100.4.6
- [magento/module-catalog-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-staging/): 100.4.8
- [magento/module-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging/): 100.4.8
- [magento/module-catalog-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging-graph-ql/): 100.4.7
- [magento/module-catalog-url-rewrite-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-staging/): 100.4.7
- [magento/module-checkout-address-search](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search/): 100.4.7
- [magento/module-checkout-address-search-dom-registry](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search-gift-registry/): 100.4.4
- [magento/module-checkout-staging](https://developer.adobe.com/commerce/php/module-reference/module-checkout-staging/): 100.4.7
- [magento/module-cms-staging](https://developer.adobe.com/commerce/php/module-reference/module-cms-staging/): 100.4.8
- [magento/module-configurable-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-staging/): 100.4.7
- [magento/module-custom-attribute-management](https://developer.adobe.com/commerce/php/module-reference/module-custom-attribute-management/): 100.4.7
- [magento/module-customer-balance](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance/): 100.4.8
- [magento/module-customer-balance-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance-graph-ql/): 100.4.5
- [magento/module-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes/): 100.4.8
- [magento/module-customer-custom-attributes-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes-graph-ql/): 100.4.1
- [magento/module-customer-finance](https://developer.adobe.com/commerce/php/module-reference/module-customer-finance/): 100.4.5
- [magento/module-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment/): 102.1.8
- [magento/module-customer-segment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment-graph-ql/): 100.4.1
- [magento/module-deferred-total-calculation](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/): 100.4.3
- [magento/module-downloadable-staging](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-staging/): 100.4.7
- [magento/module-elasticsearch-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions/): 100.4.4
- [magento/module-elasticsearch-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions-graph-ql/): 100.4.3
- [magento/module-enterprise](https://developer.adobe.com/commerce/php/module-reference/module-enterprise/): 100.4.6
- [magento/module-vale-presente](https://developer.adobe.com/commerce/php/module-reference/module-gift-card/): 101.3.8
- [magento/module-vale-presente-conta](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account/): 101.2.8
- [magento/module-vale-presente-card-account-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account-graph-ql/): 100.4.6
- [magento/module-dom-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-graph-ql/): 100.4.8
- [magento/module-vale-presente-import-export](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-import-export/): 100.4.5
- [magento/module-present-card-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-staging/): 100.4.5
- [magento/module-present-message-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-staging/): 100.4.5
- [magento/module-present-registry](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry/): 101.2.8
- [magento/module-present-registry-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry-graph-ql/): 100.4.4
- [magento/module-present-wrapping](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping/): 101.2.7
- [magento/module-present-wrapping-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-graph-ql/): 100.4.5
- [magento/module-present-wrapping-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-staging/): 100.4.5
- [magento/module-google-otimizer-staging](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer-staging/): 100.4.5
- [magento/module-google-tag-manager](https://developer.adobe.com/commerce/php/module-reference/module-google-tag-manager/): 100.4.8
- [magento/module-grouped-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-staging/): 100.4.6
- [magento/module-import-csv](https://developer.adobe.com/commerce/php/module-reference/module-import-csv/): 100.4.2
- [magento/module-import-csv-api](https://developer.adobe.com/commerce/php/module-reference/module-import-csv-api/): 100.4.2
- [magento/module-import-json](https://developer.adobe.com/commerce/php/module-reference/module-import-json/): 100.4.1
- [magento/module-import-json-api](https://developer.adobe.com/commerce/php/module-reference/module-import-json-api/): 100.4.1
- [magento/module-convite](https://developer.adobe.com/commerce/php/module-reference/module-invitation/): 100.4.7
- [magento/module-layered-navigation-staging](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation-staging/): 100.4.5
- [magento/module-logging](https://developer.adobe.com/commerce/php/module-reference/module-logging/): 101.2.8
- [magento/module-login-as-customer-logging](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-logging/): 100.4.8
- [magento/module-login-as-customer-website-restriction](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-website-restriction/): 100.4.6
- [magento/module-media-content-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog-staging/): 100.4.5
- [magento/module-msrp-staging](https://developer.adobe.com/commerce/php/module-reference/module-msrp-staging/): 100.4.6
- [magento/module-multicoupon](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon/): 100.4.1
- [magento/module-multicoupon-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-graph-ql/): 100.4.1
- [magento/module-multicoupon-ui](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-ui/): 100.4.1
- [magento/module-multiple-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist/): 100.4.8
- [magento/module-multiple-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist-graph-ql/): 100.4.4
- [magento/module-payment-staging](https://developer.adobe.com/commerce/php/module-reference/module-payment-staging/): 100.4.5
- [magento/module-persistent-history](https://developer.adobe.com/commerce/php/module-reference/module-persistent-history/): 100.4.5
- [magento/module-price-permissions](https://developer.adobe.com/commerce/php/module-reference/module-price-permissions/): 100.4.4
- [magento/module-product-video-staging](https://developer.adobe.com/commerce/php/module-reference/module-product-video-staging/): 100.4.5
- [magento/module-promotion-permissions](https://developer.adobe.com/commerce/php/module-reference/module-promotion-permissions/): 100.4.5
- [magento/module-quote-commerce-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-commerce-graph-ql/): 100.4.1
- [magento/module-quote-vale-presente-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-gift-card-options/): 100.4.5
- [magento/module-quote-staging](https://developer.adobe.com/commerce/php/module-reference/module-quote-staging/): 100.4.5
- [magento/module-reminder](https://developer.adobe.com/commerce/php/module-reference/module-reminder/): 101.2.7
- [magento/module-remote-storage-commerce](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage-commerce/): 100.4.4
- [magento/module-resource-connections](https://developer.adobe.com/commerce/php/module-reference/module-resource-connections/): 100.4.5
- [magento/module-review-staging](https://developer.adobe.com/commerce/php/module-reference/module-review-staging/): 100.4.5
- [magento/module-award](https://developer.adobe.com/commerce/php/module-reference/module-reward/): 101.2.8
- [magento/module-reforço-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-reward-graph-ql/): 100.4.7
- [magento/module-reforço-staging](https://developer.adobe.com/commerce/php/module-reference/module-reward-staging/): 100.4.5
- [magento/module-rma](https://developer.adobe.com/commerce/php/module-reference/module-rma/): 101.2.8
- [magento/module-rma-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-rma-graph-ql/): 100.4.7
- [magento/module-rma-staging](https://developer.adobe.com/commerce/php/module-reference/module-rma-staging/): 100.4.5
- [magento/module-sales-archive](https://developer.adobe.com/commerce/php/module-reference/module-sales-archive/): 101.0.6
- [magento/module-sales-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-staging/): 100.4.7
- [magento/module-scalable-checkout](https://developer.adobe.com/commerce/php/module-reference/module-scalable-checkout/): 100.4.7
- [magento/module-scalable-inventory](https://developer.adobe.com/commerce/php/module-reference/module-scalable-inventory/): 100.4.6
- [magento/module-scalable-oms](https://developer.adobe.com/commerce/php/module-reference/module-scalable-oms/): 100.4.6
- [magento/module-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-scheduled-import-export/): 101.2.8
- [magento/module-search-staging](https://developer.adobe.com/commerce/php/module-reference/module-search-staging/): 100.4.6
- [magento/module-staging](https://developer.adobe.com/commerce/php/module-reference/module-staging/): 101.2.8
- [magento/module-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-staging-graph-ql/): 100.4.5
- [magento/module-support](https://developer.adobe.com/commerce/php/module-reference/module-support/): 101.2.7
- [magento/module-swat](https://developer.adobe.com/commerce/php/module-reference/module-swat/): 100.4.6
- [magento/module-target-rule](https://developer.adobe.com/commerce/php/module-reference/module-target-rule/): 101.2.8
- [magento/module-target-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-target-rule-graph-ql/): 100.4.5
- [magento/module-versions-cms](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms/): 101.2.8
- [magento/module-versions-cms-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-page-cache/): 100.4.4
- [magento/module-versions-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite/): 100.4.6
- [magento/module-versions-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite-graph-ql/): 100.4.4
- [magento/module-visual-merchandiser](https://developer.adobe.com/commerce/php/module-reference/module-visual-merchandiser/): 100.4.8
- [magento/module-webapi-rest-gws](https://developer.adobe.com/commerce/php/module-reference/module-webapi-rest-gws/): 100.4.0
- [magento/module-website-restriction](https://developer.adobe.com/commerce/php/module-reference/module-website-restriction/): 100.4.7
- [magento/module-wee-staging](https://developer.adobe.com/commerce/php/module-reference/module-weee-staging/): 100.4.5
- [magento/module-wishlist-vale-presente](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card/): 100.4.4
- [magento/module-wishlist-dom-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card-graph-ql/): 100.4.4
- magento/page-builder-commerce: 1.7.5
- magento/product-community-edition: 2.4.8
- magento/security-package-ee: 1.0.3
- magento/theme-adminhtml-spectrum: 100.4.3
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1,16
- monólogo/monólogo: ^3,6
- opensearch-project/opensearch-php: ^2.3
- pelago/emogrificador: ^7,0
- php: ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3,2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3,0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4,2
- symfony/console: ^6,4
- symfony/intl: ^6,4
- symfony/mailer: ^6.4
- symfony/mime: ^6,4
- symfony/process: ^6.4
- symfony/string: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3,4
- webonyx/graphql-php: ^15,0
- wikimedia/less.php: ^5.0

## Licenças de terceiros

### Apache-2.0, somente LGPL-2.1

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>Biblioteca</td>
    <td>Cliente PHP para OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de API do Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Biblioteca</td>
    <td>AWS Common Runtime para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Biblioteca</td>
    <td>AWS SDK para PHP - Use o Amazon Web Services no seu projeto PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">abrir-telemetria/api</a>
    </td>
    <td>Biblioteca</td>
    <td>API para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">abrir-telemetria/contexto</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementação de contexto para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>Metapackage</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>Biblioteca</td>
    <td>Porta PHP do processador LESS</td>
  </tr>
  </tbody>
</table>

### Cláusula BSD- 2

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Biblioteca</td>
    <td>BaconQrCode é um gerador de código QR para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementação do PHP 7.1 enum</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>Biblioteca</td>
    <td>Ferramenta para gravar arquivos com segurança, para evitar condições de corrida</td>
  </tr>
  </tbody>
</table>

### BSD-3-Cláusula

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento-module</td>
    <td>O back-end do estoque Zend_Cache_Backend_File tem desempenho extremamente baixo para limpeza por tags, tornando-o inutilizável à medida que o número de itens em cache aumenta. Esse back-end faz muitas alterações, resultando em um enorme aumento de desempenho, especialmente para a limpeza de tags.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Biblioteca</td>
    <td>Um gerenciador de sessões baseado no Redis com bloqueio otimista</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma implementação em PHP do Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca simples para codificar e decodificar JSON Web Tokens (JWT) no PHP. Deve estar em conformidade com as especificações atuais.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Gerar e validar CAPTCHAs usando Figlets, imagens, ReCaptcha e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>Biblioteca</td>
    <td>Extensões para a API de reflexão do PHP, varredura de código estático e geração de código</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Biblioteca</td>
    <td>O fornece uma interface do usuário baseada em propriedade de objeto aninhado para acessar esses dados de configuração no código do aplicativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Biblioteca</td>
    <td>Injeção de dependência automatizada para contêineres PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escaper</a>
    </td>
    <td>Biblioteca</td>
    <td>Escapar com segurança do HTML, atributos do HTML, JavaScript, CSS e URLs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Acionar e ouvir eventos em um aplicativo PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Biblioteca</td>
    <td>fornece funcionalidade para criar e consumir RSS e Atom feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">laminas/laminas-filter</a>
    </td>
    <td>Biblioteca</td>
    <td>Filtrar e normalizar dados e arquivos de forma programática</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece uma interface fácil para executar solicitações do HTTP (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornecer traduções para seu aplicativo e filtrar e validar valores internacionalizados</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Biblioteca</td>
    <td>fornece métodos convenientes para serializar PHP nativo para JSON e decodificar JSON para PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>Biblioteca</td>
    <td>Estratégias de carregamento automático e de plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Sistema de aplicação modular para aplicações em lamininas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>Biblioteca</td>
    <td>Camada MVC orientada por eventos do Laminas, incluindo aplicativos MVC, controladores e plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Biblioteca</td>
    <td>Oferece uma implementação leve e flexível de ACL (Access Control List, lista de controle de acesso) para gerenciamento de privilégios</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Invólucro OOP para o serviço Web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Biblioteca</td>
    <td>Sistema de roteamento flexível para aplicativos HTTP e de console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>Biblioteca</td>
    <td>Criar servidores RPC baseados em Reflexo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Contêiner de injeção de dependência de fábrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface orientada a objetos para sessões e armazenamento em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>Biblioteca</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Biblioteca</td>
    <td>Extensões SPL, utilitários de matriz, manipuladores de erros e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Biblioteca</td>
    <td>Criar FIGlets e tabelas baseadas em texto</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaces para o componente tradutor de laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Biblioteca</td>
    <td>Um componente que auxilia na manipulação e validação dos URIs (Uniform Resource Identifiers, identificadores uniformes de recursos)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Biblioteca</td>
    <td>Classes de validação para uma grande variedade de domínios e a capacidade de encadear validadores para criar critérios de validação complexos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Biblioteca</td>
    <td>Camada de visualização flexível que suporta e fornece várias camadas de visualização, auxiliares e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementação simples e rápida de enumerações com PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Biblioteca</td>
    <td>Um analisador PHP escrito em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca cliente do reCAPTCHA do Google para PHP 8.4 e superior</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>Biblioteca</td>
    <td>Minificador JavaScript construído no PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma porta PHP do compactador CSS YUI</td>
  </tr>
  </tbody>
</table>

### BSD-3-Cláusula-Modificação

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-module</td>
    <td>Infraestrutura Zend_Cache usando Redis com suporte completo para tags.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat">paragonie/dium_compat</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementação PHP pura de libsódio; usa a extensão PHP se ela existir</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1 ou posterior

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurifier</a>
    </td>
    <td>Biblioteca</td>
    <td>Filtro HTML compatível com padrões escrito em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>Biblioteca</td>
    <td>Anteriormente videlalvaro/php-amqplib.  Esta biblioteca é uma implementação PHP pura do protocolo AMQP. Foi testado contra RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca cliente PHP Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">brick/math</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca aritmética de precisão arbitrária</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">exportador/brick</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma alternativa poderosa para var_export(), que pode exportar fechamentos e objetos sem __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">christian-riesen/base32</a>
    </td>
    <td>Biblioteca</td>
    <td>Codificador/decodificador Base32 de acordo com RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>Biblioteca</td>
    <td>Credis é uma interface leve para a loja de valores-chave Redis que envolve a biblioteca phpredis quando disponível para melhor desempenho.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">composer/ca-bundle</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite encontrar um caminho para o pacote de CA do sistema e inclui um fallback para o pacote de CA Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">composer/class-map-generator</a>
    </td>
    <td>Biblioteca</td>
    <td>Utilitários para escanear código PHP e gerar mapas de classe.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">compositor/compositor</a>
    </td>
    <td>Biblioteca</td>
    <td>O Composer ajuda você a declarar, gerenciar e instalar dependências de projetos PHP. Ele garante que você tenha a pilha certa em todos os lugares.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">compositor/minificador de metadados</a>
    </td>
    <td>Biblioteca</td>
    <td>Pequena biblioteca de utilitários que lida com minificação e expansão de metadados.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">compositor/pcre</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de encapsulamento PCRE que oferece substituições preg_* seguras para tipos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">compositor/semver</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de servidor que oferece utilitários, análise de restrição de versão e validação.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">composer/spdx-licenses</a>
    </td>
    <td>Biblioteca</td>
    <td>Lista de licenças SPDX e biblioteca de validação.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">composer/xdebug-handler</a>
    </td>
    <td>Biblioteca</td>
    <td>Reinicia um processo sem o Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">doutrina/lexer</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de analisadores Lexer de Doutrina PHP que pode ser usada em Analisadores Descendentes Recursivos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">guias/validador de email</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca para validar emails em relação a vários RFCs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">elástico/transporte</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca PHP de transporte HTTP para produtos Elastic</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Biblioteca</td>
    <td>Cliente PHP para Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Biblioteca</td>
    <td>Código QR Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Biblioteca</td>
    <td>Bifurcação de garoa/transmissões (abandonada) para ser usada com elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Bifurcação de guzzle/RingPHP (abandonada) para ser usada com elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Biblioteca</td>
    <td>Guzzle é uma biblioteca cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promessas</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de promessas do Guzzle</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementação de mensagem PSR-7 que também fornece métodos de utilitário comuns</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinarco-íris/json-schema</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca para validar um esquema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">liga/flysystem</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstração de armazenamento de arquivo para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">liga/flysystem-aws-s3-v3</a>
    </td>
    <td>Biblioteca</td>
    <td>Adaptador de sistema de arquivos AWS S3 para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">liga/flysystem-local</a>
    </td>
    <td>Biblioteca</td>
    <td>Adaptador de sistema de arquivos local para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-detection</a>
    </td>
    <td>Biblioteca</td>
    <td>Detecção de tipo MIME para Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monólogo/monólogo</a>
    </td>
    <td>Biblioteca</td>
    <td>Envia seus registros para arquivos, soquetes, caixas de entrada, bancos de dados e vários serviços da Web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Biblioteca</td>
    <td>Especificar declarativamente como extrair elementos de um documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementações de tempo constante da codificação RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Biblioteca</td>
    <td>PHP 5.x polyfill para random_bytes() e random_int() do PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emotificador</a>
    </td>
    <td>Biblioteca</td>
    <td>Converte estilos CSS em atributos de estilo em linha no seu código HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>Localiza e instala implementações PSR-7, PSR-17, PSR-18 e HTTPlug</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Biblioteca</td>
    <td>HTTPlug, a abstração do cliente HTTP para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promessa</a>
    </td>
    <td>Biblioteca</td>
    <td>Promessa usada para solicitações HTTP assíncronas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Biblioteca</td>
    <td>Converta seletores de CSS em consultas XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Biblioteca</td>
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Biblioteca</td>
    <td>Funções de acessador e mutador de propriedade.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Biblioteca</td>
    <td>polyfill do PHP 5.x-8.x para extensão mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de comunicações seguras PHP - implementações de PHP puro de RSA, AES, SSH2, SFTP, X.509 etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum para o armazenamento em cache de bibliotecas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum para a leitura do relógio.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum de contêiner (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaces padrão para manipulação de eventos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum para clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-fatory</a>
    </td>
    <td>Biblioteca</td>
    <td>PSR-17: interfaces comuns para fábricas de mensagens HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum para mensagens HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>Biblioteca</td>
    <td>Interface comum para bibliotecas de registro</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>Biblioteca</td>
    <td>Um polyfill para getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">ramsey/collection</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca PHP para representar e manipular coleções.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca PHP para geração e trabalho com identificadores universalmente exclusivos (UUIDs).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">reação/promessa</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma implementação leve do CommonJS Promises/A para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Biblioteca</td>
    <td>Analisador para arquivos CSS escritos em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Biblioteca</td>
    <td>Linter JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Biblioteca</td>
    <td>utilitários de formato de arquivo PHAR, para quando o PHP lhe mostrar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/manipulador de sinal</a>
    </td>
    <td>Biblioteca</td>
    <td>Manipulador simples de sinais Unix que falha silenciosamente quando os sinais não são suportados para um fácil desenvolvimento entre plataformas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Biblioteca</td>
    <td>Encapsulamento de chave AES para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma biblioteca PHP para gerar senhas únicas de acordo com RFC 4226 (algoritmo HOTP) e RFC 6238 (algoritmo TOTP) e compatível com o Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma estrutura PHP para gerenciamento da Infraestrutura de Chave Pública. Ele inclui certificados de chave pública X.509, certificados de atributo, solicitações de certificação e validação do caminho de certificação.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Biblioteca</td>
    <td>Ajuda a localizar, carregar, combinar, preencher automaticamente e validar valores de configuração de qualquer tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symfony/console</a>
    </td>
    <td>Biblioteca</td>
    <td>Facilita a criação de interfaces de linha de comando belas e testáveis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-seletor</a>
    </td>
    <td>Biblioteca</td>
    <td>Converte seletores CSS em expressões XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">injeção de symfony/dependência</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite padronizar e centralizar a maneira como os objetos são construídos em seu aplicativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">symfony/deprecation-contracts</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma função e convenção genéricas para acionar avisos de substituição</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece ferramentas para gerenciar erros e facilitar a depuração do código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece ferramentas que permitem que os componentes do aplicativo se comuniquem entre si despachando eventos e ouvindo-os</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-contracts</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstrações genéricas relacionadas ao evento de despacho</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece utilitários básicos para o sistema de arquivos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Biblioteca</td>
    <td>Localiza arquivos e diretórios por meio de uma interface intuitiva e fluente</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece métodos avançados para buscar recursos HTTP de forma síncrona ou assíncrona</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-contracts</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstrações genéricas relacionadas a clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Biblioteca</td>
    <td>Define uma camada orientada a objetos para a especificação HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece um processo estruturado para converter uma Solicitação em uma Resposta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece acesso aos dados de localização da biblioteca ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Biblioteca</td>
    <td>Ajuda a enviar emails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite manipular mensagens MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para funções ctype</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para funções grapheme_* da intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Biblioteca</td>
    <td>polyfill Symfony para as funções idn_to_ascii e idn_to_utf8 da intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para a classe Normalizer da intl e funções relacionadas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Biblioteca</td>
    <td>Preenchimento múltiplo Symfony para a extensão Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 7.3+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.0+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.1+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.2+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.3+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Biblioteca</td>
    <td>Executa comandos em subprocessos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">symfony/service-contracts</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstrações genéricas relacionadas com serviços de escrita</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece uma API orientada a objetos para strings e lida com bytes, pontos de código UTF-8 e clusters de grapheme de forma unificada</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Biblioteca</td>
    <td>Fornece mecanismos para percorrer qualquer variável PHP arbitrária</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite exportar qualquer estrutura de dados PHP serializável para código PHP simples</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Biblioteca</td>
    <td>Carrega e despeja arquivos YAML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Symfony-bundle</td>
    <td>Biblioteca JSON Object Signing and Encryption para PHP e Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>Biblioteca</td>
    <td>Uma porta PHP da implementação de referência do GraphQL</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-vale-presente
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-vale-presente-conta
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-wrapping
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-award
    </td>
    <td>Módulo Magento2</td>
    <td>N/D</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>Biblioteca</td>
    <td>Codificador CBOR para PHP</td>
  </tr>
  </tbody>
</table>

### Proprietário

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### proprietário

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>Módulo Magento2</td>
    <td>Bifurcação do módulo Magento Braintree 2.2.0 de Gene Commerce para PayPal.</td>
  </tr>
  </tbody>
</table>
