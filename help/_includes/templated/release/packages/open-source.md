---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '2073'
ht-degree: 0%

---
# Pacotes Magento Open Source

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

O Magento Open Source usa o Composer para gerenciar pacotes PHP.

O arquivo `composer.json` declara a lista de pacotes, enquanto o arquivo `composer.lock` armazena uma lista completa dos pacotes (uma versão completa de cada pacote e suas dependências) usados para criar uma instalação do Magento Open Source.

A documentação de referência a seguir é gerada a partir do arquivo `composer.lock` e abrange os pacotes necessários incluídos no Magento Open Source 2.4.8.

## Dependências

`magento/product-community-edition 2.4.8` tem as seguintes dependências:

```config
adobe-commerce/os-extensions-metapackage: 1.0.1
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ^2.0
composer/composer: ^2.0, !=2.2.16
duosecurity/duo_api_php: ^1.1
duosecurity/duo_universal_php: ^1.0
elasticsearch/elasticsearch: ^8.15
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-ftp: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.18
laminas/laminas-code: ^4.13
laminas/laminas-di: ^3.15
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^3.0
league/flysystem-aws-s3-v3: ^3.0
lib-libxml: *
magento/composer: ^1.10.1-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.8
magento/framework-amqp: 100.4.6
magento/framework-bulk: 101.0.4
magento/framework-message-queue: 100.4.8
magento/inventory-metapackage: 1.2.8
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento-zf-db: ^3.21.0
magento/magento2-base: 2.4.8
magento/module-admin-analytics: 100.4.7
magento/module-admin-notification: 100.4.7
magento/module-advanced-pricing-import-export: 100.4.8
magento/module-advanced-search: 100.4.6
magento/module-amqp: 100.4.5
magento/module-analytics: 100.4.8
magento/module-application-performance-monitor: 100.4.1
magento/module-application-performance-monitor-new-relic: 100.4.1
magento/module-async-config: 100.4.1
magento/module-asynchronous-operations: 100.4.8
magento/module-authorization: 100.4.8
magento/module-aws-s3: 100.4.6
magento/module-backend: 102.0.8
magento/module-backup: 100.4.8
magento/module-bundle: 101.0.8
magento/module-bundle-graph-ql: 100.4.8
magento/module-bundle-import-export: 100.4.7
magento/module-cache-invalidate: 100.4.6
magento/module-captcha: 100.4.8
magento/module-cardinal-commerce: 100.4.6
magento/module-catalog: 104.0.8
magento/module-catalog-analytics: 100.4.5
magento/module-catalog-cms-graph-ql: 100.4.4
magento/module-catalog-customer-graph-ql: 100.4.7
magento/module-catalog-graph-ql: 100.4.8
magento/module-catalog-import-export: 101.1.8
magento/module-catalog-inventory: 100.4.8
magento/module-catalog-inventory-graph-ql: 100.4.5
magento/module-catalog-rule: 101.2.8
magento/module-catalog-rule-configurable: 100.4.7
magento/module-catalog-rule-graph-ql: 100.4.5
magento/module-catalog-search: 102.0.8
magento/module-catalog-url-rewrite: 100.4.8
magento/module-catalog-url-rewrite-graph-ql: 100.4.6
magento/module-catalog-widget: 100.4.8
magento/module-checkout: 100.4.8
magento/module-checkout-agreements: 100.4.7
magento/module-checkout-agreements-graph-ql: 100.4.4
magento/module-cms: 104.0.8
magento/module-cms-graph-ql: 100.4.5
magento/module-cms-url-rewrite: 100.4.7
magento/module-cms-url-rewrite-graph-ql: 100.4.6
magento/module-compare-list-graph-ql: 100.4.4
magento/module-config: 101.2.8
magento/module-configurable-import-export: 100.4.6
magento/module-configurable-product: 100.4.8
magento/module-configurable-product-graph-ql: 100.4.8
magento/module-configurable-product-sales: 100.4.5
magento/module-contact: 100.4.7
magento/module-contact-graph-ql: 100.4.1
magento/module-cookie: 100.4.8
magento/module-cron: 100.4.8
magento/module-csp: 100.4.7
magento/module-currency-symbol: 100.4.6
magento/module-customer: 103.0.8
magento/module-customer-analytics: 100.4.5
magento/module-customer-downloadable-graph-ql: 100.4.4
magento/module-customer-graph-ql: 100.4.8
magento/module-customer-import-export: 100.4.8
magento/module-deploy: 100.4.8
magento/module-developer: 100.4.8
magento/module-dhl: 100.4.7
magento/module-directory: 100.4.8
magento/module-directory-graph-ql: 100.4.6
magento/module-downloadable: 100.4.8
magento/module-downloadable-graph-ql: 100.4.8
magento/module-downloadable-import-export: 100.4.7
magento/module-eav: 102.1.8
magento/module-eav-graph-ql: 100.4.5
magento/module-elasticsearch: 101.0.8
magento/module-elasticsearch-8: 101.0.0
magento/module-email: 101.1.8
magento/module-encryption-key: 100.4.6
magento/module-fedex: 100.4.6
magento/module-gift-message: 100.4.7
magento/module-gift-message-graph-ql: 100.4.6
magento/module-google-adwords: 100.4.5
magento/module-google-analytics: 100.4.4
magento/module-google-gtag: 100.4.3
magento/module-google-optimizer: 100.4.7
magento/module-graph-ql: 100.4.8
magento/module-graph-ql-cache: 100.4.5
magento/module-graph-ql-new-relic: 100.4.1
magento/module-graph-ql-resolver-cache: 100.4.1
magento/module-grouped-catalog-inventory: 100.4.5
magento/module-grouped-import-export: 100.4.6
magento/module-grouped-product: 100.4.8
magento/module-grouped-product-graph-ql: 100.4.8
magento/module-import-export: 101.0.8
magento/module-indexer: 100.4.8
magento/module-instant-purchase: 100.4.7
magento/module-integration: 100.4.8
magento/module-integration-graph-ql: 100.4.1
magento/module-jwt-framework-adapter: 100.4.4
magento/module-jwt-user-token: 100.4.3
magento/module-layered-navigation: 100.4.8
magento/module-login-as-customer: 100.4.8
magento/module-login-as-customer-admin-ui: 100.4.8
magento/module-login-as-customer-api: 100.4.7
magento/module-login-as-customer-assistance: 100.4.7
magento/module-login-as-customer-frontend-ui: 100.4.7
magento/module-login-as-customer-graph-ql: 100.4.5
magento/module-login-as-customer-log: 100.4.6
magento/module-login-as-customer-page-cache: 100.4.7
magento/module-login-as-customer-quote: 100.4.6
magento/module-login-as-customer-sales: 100.4.7
magento/module-marketplace: 100.4.6
magento/module-media-content: 100.4.6
magento/module-media-content-api: 100.4.7
magento/module-media-content-catalog: 100.4.6
magento/module-media-content-cms: 100.4.6
magento/module-media-content-synchronization: 100.4.7
magento/module-media-content-synchronization-api: 100.4.6
magento/module-media-content-synchronization-catalog: 100.4.5
magento/module-media-content-synchronization-cms: 100.4.5
magento/module-media-gallery: 100.4.7
magento/module-media-gallery-api: 101.0.7
magento/module-media-gallery-catalog: 100.4.5
magento/module-media-gallery-catalog-integration: 100.4.5
magento/module-media-gallery-catalog-ui: 100.4.5
magento/module-media-gallery-cms-ui: 100.4.5
magento/module-media-gallery-integration: 100.4.7
magento/module-media-gallery-metadata: 100.4.6
magento/module-media-gallery-metadata-api: 100.4.5
magento/module-media-gallery-renditions: 100.4.6
magento/module-media-gallery-renditions-api: 100.4.5
magento/module-media-gallery-synchronization: 100.4.7
magento/module-media-gallery-synchronization-api: 100.4.6
magento/module-media-gallery-synchronization-metadata: 100.4.4
magento/module-media-gallery-ui: 100.4.7
magento/module-media-gallery-ui-api: 100.4.6
magento/module-media-storage: 100.4.7
magento/module-message-queue: 100.4.8
magento/module-msrp: 100.4.7
magento/module-msrp-configurable-product: 100.4.5
magento/module-msrp-grouped-product: 100.4.5
magento/module-multishipping: 100.4.8
magento/module-mysql-mq: 100.4.6
magento/module-new-relic-reporting: 100.4.6
magento/module-newsletter: 100.4.8
magento/module-newsletter-graph-ql: 100.4.5
magento/module-offline-payments: 100.4.6
magento/module-offline-shipping: 100.4.7
magento/module-open-search: 100.4.2
magento/module-order-cancellation: 100.4.1
magento/module-order-cancellation-graph-ql: 100.4.1
magento/module-order-cancellation-ui: 100.4.1
magento/module-page-cache: 100.4.8
magento/module-payment: 100.4.8
magento/module-payment-graph-ql: 100.4.3
magento/module-paypal: 101.0.8
magento/module-paypal-captcha: 100.4.5
magento/module-paypal-graph-ql: 100.4.6
magento/module-persistent: 100.4.8
magento/module-product-alert: 100.4.7
magento/module-product-video: 100.4.8
magento/module-quote: 101.2.8
magento/module-quote-analytics: 100.4.7
magento/module-quote-bundle-options: 100.4.4
magento/module-quote-configurable-options: 100.4.4
magento/module-quote-downloadable-links: 100.4.4
magento/module-quote-graph-ql: 100.4.8
magento/module-related-product-graph-ql: 100.4.5
magento/module-release-notification: 100.4.6
magento/module-remote-storage: 100.4.6
magento/module-reports: 100.4.8
magento/module-require-js: 100.4.4
magento/module-review: 100.4.8
magento/module-review-analytics: 100.4.5
magento/module-review-graph-ql: 100.4.4
magento/module-robots: 101.1.4
magento/module-rss: 100.4.6
magento/module-rule: 100.4.7
magento/module-sales: 103.0.8
magento/module-sales-analytics: 100.4.5
magento/module-sales-graph-ql: 100.4.8
magento/module-sales-inventory: 100.4.5
magento/module-sales-rule: 101.2.8
magento/module-sales-rule-graph-ql: 100.4.1
magento/module-sales-sequence: 100.4.5
magento/module-sample-data: 100.4.6
magento/module-search: 101.1.8
magento/module-security: 100.4.8
magento/module-send-friend: 100.4.6
magento/module-send-friend-graph-ql: 100.4.4
magento/module-shipping: 100.4.8
magento/module-sitemap: 100.4.7
magento/module-store: 101.1.8
magento/module-store-graph-ql: 100.4.6
magento/module-swagger: 100.4.7
magento/module-swagger-webapi: 100.4.4
magento/module-swagger-webapi-async: 100.4.4
magento/module-swatches: 100.4.8
magento/module-swatches-graph-ql: 100.4.6
magento/module-swatches-layered-navigation: 100.4.4
magento/module-tax: 100.4.8
magento/module-tax-graph-ql: 100.4.4
magento/module-tax-import-export: 100.4.7
magento/module-theme: 101.1.8
magento/module-theme-graph-ql: 100.4.5
magento/module-translation: 100.4.8
magento/module-ui: 101.2.8
magento/module-ups: 100.4.8
magento/module-url-rewrite: 102.0.7
magento/module-url-rewrite-graph-ql: 100.4.7
magento/module-user: 101.2.8
magento/module-usps: 100.4.7
magento/module-variable: 100.4.6
magento/module-vault: 101.2.8
magento/module-vault-graph-ql: 100.4.4
magento/module-version: 100.4.5
magento/module-webapi: 100.4.7
magento/module-webapi-async: 100.4.6
magento/module-webapi-security: 100.4.5
magento/module-weee: 100.4.8
magento/module-weee-graph-ql: 100.4.5
magento/module-widget: 101.2.8
magento/module-wishlist: 101.2.8
magento/module-wishlist-analytics: 100.4.6
magento/module-wishlist-graph-ql: 100.4.8
magento/page-builder: 1.7.5
magento/security-package: 1.1.7
magento/theme-adminhtml-backend: 100.4.8
magento/theme-frontend-blank: 100.4.8
magento/theme-frontend-luma: 100.4.8
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^3.6
opensearch-project/opensearch-php: ^2.3
pelago/emogrifier: ^7.0
php: ~8.2.0||~8.3.0||~8.4.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/mailer: ^6.4
symfony/mime: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.4
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^5.0
```

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
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>biblioteca</td>
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
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de API do Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>biblioteca</td>
    <td>AWS Common Runtime para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>biblioteca</td>
    <td>AWS SDK para PHP - Use o Amazon Web Services no seu projeto PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api.git">abrir-telemetria/api</a>
    </td>
    <td>biblioteca</td>
    <td>API para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context.git">abrir-telemetria/contexto</a>
    </td>
    <td>biblioteca</td>
    <td>Implementação de contexto para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>metapackage</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>biblioteca</td>
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
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>biblioteca</td>
    <td>BaconQrCode é um gerador de código QR para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>biblioteca</td>
    <td>Enumerar PHP 7.1 implementação</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>biblioteca</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-módulo</td>
    <td>O back-end do estoque Zend_Cache_Backend_File tem desempenho extremamente baixo para limpeza por tags, tornando-o inutilizável à medida que o número de itens em cache aumenta. Esse back-end faz muitas alterações, resultando em um enorme aumento de desempenho, especialmente para a limpeza de tags.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>biblioteca</td>
    <td>Um gerenciador de sessões baseado no Redis com bloqueio otimista</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php.git">duosecurity/duo_universal_php</a>
    </td>
    <td>biblioteca</td>
    <td>Uma implementação em PHP do Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>biblioteca</td>
    <td>Uma biblioteca simples para codificar e decodificar JSON Web Tokens (JWT) no PHP. Deve estar em conformidade com as especificações atuais.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>biblioteca</td>
    <td>Gerar e validar CAPTCHAs usando Figlets, imagens, ReCaptcha e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>biblioteca</td>
    <td>Extensões para a API de reflexão do PHP, varredura de código estático e geração de código</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>biblioteca</td>
    <td>O fornece uma interface do usuário baseada em propriedade de objeto aninhado para acessar esses dados de configuração no código do aplicativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>biblioteca</td>
    <td>Injeção de dependência automatizada para contêineres PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escaper</a>
    </td>
    <td>biblioteca</td>
    <td>Escape com segurança html, atributos HTML, JavaScript, CSS e URLs com segurança</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>biblioteca</td>
    <td>Acionar e ouvir eventos em um php aplicativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>biblioteca</td>
    <td>fornece funcionalidade para criar e consumir feeds RSS e Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">laminas/laminas-filter</a>
    </td>
    <td>biblioteca</td>
    <td>Filtrar e normalizar dados e arquivos de forma programática</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece uma interface fácil para executar solicitações de protocolo de transferência de hiper textual (HTTP)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>biblioteca</td>
    <td>Fornecer traduções para seu aplicativo e filtrar e validar valores internacionalizados</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>biblioteca</td>
    <td>fornece métodos de conveniência para serializar nativo PHP para JSON e decodificar o JSON para nativo PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>biblioteca</td>
    <td>Estratégias de carregamento automático e de plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>biblioteca</td>
    <td>Sistema de aplicação modular para aplicações em lamininas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>biblioteca</td>
    <td>Camada MVC orientada por eventos do Laminas, incluindo aplicativos MVC, controladores e plug-ins</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>biblioteca</td>
    <td>Oferece uma implementação leve e flexível de ACL (Access Control List, lista de controle de acesso) para gerenciamento de privilégios</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>Invólucro OOP para o serviço Web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>biblioteca</td>
    <td>Sistema de roteamento flexível para aplicativos HTTP e de console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>biblioteca</td>
    <td>Criar servidores de RPC baseados em reflexão</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>biblioteca</td>
    <td>Contêiner de injeção de dependência de fábrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>biblioteca</td>
    <td>Interface voltada para objetos para sessões e armazenamento PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-soap</a>
    </td>
    <td>biblioteca</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>biblioteca</td>
    <td>Extensões SPL, utilitários de matriz, manipuladores de erros e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">texto laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Criar FIGlets e tabelas baseadas em texto</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator.git">laminas/laminas-translator</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaces para o componente translator do laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>biblioteca</td>
    <td>Um componente que auxilia na manipulação e validação dos URIs (Uniform Resource Identifiers, identificadores uniformes de recursos)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>biblioteca</td>
    <td>Classes de validação para uma grande variedade de domínios e a capacidade de encadear validadores para criar critérios de validação complexos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-visualização</a>
    </td>
    <td>biblioteca</td>
    <td>Camada de visualização flexível que suporta e fornece várias camadas de visualização, auxiliares e muito mais</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum.git">marc-mabe/php-enum</a>
    </td>
    <td>biblioteca</td>
    <td>Implementação simples e rápida de enumerações com PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>biblioteca</td>
    <td>Um analisador PHP escrito em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha.git">phpfui/recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>O biblioteca do cliente para o reCAPTCHA do Google para PHP 8.4 e superior</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>biblioteca</td>
    <td>Minificador JavaScript construído no PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>biblioteca</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-módulo</td>
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
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/dium_compat</a>
    </td>
    <td>biblioteca</td>
    <td>implementação PHP puro de libsodium; o usa a extensão PHP se existir</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-ou-posterior

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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>biblioteca</td>
    <td>Filtro HTML compatível com padrões escrito em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>biblioteca</td>
    <td>Anteriormente videlalvaro/php-amqplib.  Esta biblioteca é um implementação PHP puro do protocolo AMQP. Foi testado contra RabbitMQ.</td>
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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca cliente PHP Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">tijolo/matemática</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca aritmética de precisão arbitrária</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">exportador/brick</a>
    </td>
    <td>biblioteca</td>
    <td>Uma alternativa poderosa para var_export(), que pode exportar fechamentos e objetos sem __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>biblioteca</td>
    <td>Codificador/decodificador Base32 de acordo com RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>biblioteca</td>
    <td>O Credis é uma interface leve para o valor principal Redis armazenamento que vincula os phpredis biblioteca quando disponíveis para melhor desempenho.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>biblioteca</td>
    <td>Permite encontrar um caminho para o pacote de CA do sistema e inclui um fallback para o pacote de CA Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>biblioteca</td>
    <td>Utilitários para escanear código PHP e gerar mapas de classe.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">compositor/compositor</a>
    </td>
    <td>biblioteca</td>
    <td>O Composer ajuda você a declarar, gerenciar e instalar dependências de projetos PHP. Isso garante que você tenha a pilha certa em todos os lugares.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadados-minifier</a>
    </td>
    <td>biblioteca</td>
    <td>Pequena biblioteca de utilitários que lida com minificação e expansão de metadados.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositor/pcre</a>
    </td>
    <td>biblioteca</td>
    <td>O envolvimento do PCRE biblioteca que oferece substituições preg_* seguras ao tipo.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositor/semver</a>
    </td>
    <td>biblioteca</td>
    <td>O Semver biblioteca que oferece utilitários, análise de restrição de versão e validação.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>biblioteca</td>
    <td>Licenças SPDX lista e validação biblioteca.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Reinicia um processo sem o Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">doutrina/lexer</a>
    </td>
    <td>biblioteca</td>
    <td>O analisador lexer da doutrina PHP biblioteca que pode ser usado em analisadores recursivos e recursivos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator.git">guias/validador de email</a>
    </td>
    <td>biblioteca</td>
    <td>Uma biblioteca para validar emails em relação a vários RFCs</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php.git">elástico/transporte</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca PHP de transporte HTTP para produtos Elastic</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>biblioteca</td>
    <td>Cliente PHP para Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>biblioteca</td>
    <td>Código QR Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>biblioteca</td>
    <td>Bifurcação de garoa/transmissões (abandonada) para ser usada com elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>biblioteca</td>
    <td>Bifurcação de guzzle/RingPHP (abandonado) para ser usado com elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>biblioteca</td>
    <td>Guzzle é uma biblioteca cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promessas</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de promessas do Guzzle</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>biblioteca</td>
    <td>Implementação de mensagem PSR-7 que também fornece métodos comuns de utilitários</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">justinarco-íris/json-schema</a>
    </td>
    <td>biblioteca</td>
    <td>Uma biblioteca para validar um esquema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">liga/flysystem</a>
    </td>
    <td>biblioteca</td>
    <td>abstração armazenamento Arquivo para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">liga/flysystem-aws-s3-v3</a>
    </td>
    <td>biblioteca</td>
    <td>Adaptador do sistema de arquivos AWS S3 para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local.git">liga/flysystem-local</a>
    </td>
    <td>biblioteca</td>
    <td>Adaptador de sistema de arquivos local para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">detecção de tipo de liga/mime</a>
    </td>
    <td>biblioteca</td>
    <td>Detecção de tipo Mime para Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monólogo/monólogo</a>
    </td>
    <td>biblioteca</td>
    <td>Envia seus logs para arquivos, soquetes, caixas de entrada, bancos de dados e vários serviços da Web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>biblioteca</td>
    <td>Especificar declarativamente como extrair elementos de um documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>biblioteca</td>
    <td>Implementações de tempo constante da codificação RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>biblioteca</td>
    <td>PHP 5.x polyfill para random_bytes() e random_int() do PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emotificador</a>
    </td>
    <td>biblioteca</td>
    <td>Converte estilos CSS em atributos de estilo em linha no seu código HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery.git">php-http/discovery</a>
    </td>
    <td>composer-plugin</td>
    <td>Localiza e instala implementações PSR-7, PSR-17, PSR-18 e HTTPlug</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug.git">php-http/httplug</a>
    </td>
    <td>biblioteca</td>
    <td>HTTPlug, a abstração do cliente HTTP para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise.git">php-http/promessa</a>
    </td>
    <td>biblioteca</td>
    <td>Promessa usada para solicitações HTTP assíncronas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>biblioteca</td>
    <td>Converta seletores de CSS em consultas XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>biblioteca</td>
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>biblioteca</td>
    <td>Funções de acessador e mutador de propriedade.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>biblioteca</td>
    <td>PHP 5.x-8.x polyfill para extensão mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de comunicações seguras PHP - implementações de PHP puro de RSA, AES, SSH2, SFTP, X.509 etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>biblioteca</td>
    <td>Interface comum para o armazenamento em cache de bibliotecas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>biblioteca</td>
    <td>Interface comum para ler o relógio.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>biblioteca</td>
    <td>Interface de contêiner comum (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaces padrão para manipulação de eventos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>biblioteca</td>
    <td>Interface comum para clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-fatory</a>
    </td>
    <td>biblioteca</td>
    <td>PSR-17: interfaces comuns para fábricas de mensagens HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>biblioteca</td>
    <td>Interface comum para mensagens HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>biblioteca</td>
    <td>Interface comum para bibliotecas de registro</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>biblioteca</td>
    <td>Um polyfill para getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>biblioteca</td>
    <td>Uma biblioteca PHP para representar e manipular coleções.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>biblioteca</td>
    <td>Uma biblioteca PHP para geração e trabalho com identificadores universalmente exclusivos (UUIDs).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">reação/promessa</a>
    </td>
    <td>biblioteca</td>
    <td>Uma implementação leve do CommonJS Promises/A para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>biblioteca</td>
    <td>Analisador para arquivos CSS escritos em PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>biblioteca</td>
    <td>Linter JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>biblioteca</td>
    <td>utilitários de formato de arquivo PHAR, para quando o PHP lhe mostrar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/manipulador de sinal</a>
    </td>
    <td>biblioteca</td>
    <td>Manipulador simples de sinais Unix que falha silenciosamente quando os sinais não são suportados para um fácil desenvolvimento entre plataformas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>biblioteca</td>
    <td>Quebra de chave de AES para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>biblioteca</td>
    <td>Um biblioteca PHP para gerar senhas de uma vez de acordo com o RFC 4226 (Algoritmo HOTP) e RFC 6238 (Algoritmo TOTP) e compatível com o Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>biblioteca</td>
    <td>Uma estrutura PHP para gerenciamento da Infraestrutura de Chave Pública. Ele inclui certificados de chave pública X.509, certificados de atributo, solicitações de certificação e validação do caminho de certificação.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>biblioteca</td>
    <td>Ajuda a localizar, carregar, combinar, preencher automaticamente e validar valores de configuração de qualquer tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>biblioteca</td>
    <td>Facilita a criação de interfaces de linha de comando belas e testáveis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-seletor</a>
    </td>
    <td>biblioteca</td>
    <td>Converte seletores CSS em expressões XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">injeção de symfony/dependência</a>
    </td>
    <td>biblioteca</td>
    <td>Permite padronizar e centralizar a maneira como os objetos são construídos em seu aplicativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">contratos symfony/deprecation</a>
    </td>
    <td>biblioteca</td>
    <td>Uma função e convenção genéricas para acionar avisos de substituição</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece ferramentas para gerenciar erros e facilitar a depuração do código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece ferramentas que permitem que os componentes do aplicativo se comuniquem entre si despachando eventos e ouvindo-os</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>biblioteca</td>
    <td>Abstrações genéricas relacionadas ao evento de despacho</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece utilitários básicos para o sistema de arquivos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>biblioteca</td>
    <td>Localiza arquivos e diretórios por meio de uma interface intuitiva e fluente</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece métodos avançados para buscar recursos HTTP de forma síncrona ou assíncrona</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">contratos symfony/http-client</a>
    </td>
    <td>biblioteca</td>
    <td>Abstrações genéricas relacionadas a clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>biblioteca</td>
    <td>Define uma camada orientada a objetos para a especificação HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece um processo estruturado para converter uma solicitação em uma resposta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece acesso aos dados localização da UI biblioteca</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer.git">symfony/mailer</a>
    </td>
    <td>biblioteca</td>
    <td>Ajuda a enviar emails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime.git">symfony/mime</a>
    </td>
    <td>biblioteca</td>
    <td>Permite manipular mensagens MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para funções ctype</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para funções grapheme_* da intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>biblioteca</td>
    <td>polyfill Symfony para as funções idn_to_ascii e idn_to_utf8 da intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para a classe Normalizer da intl e funções relacionadas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>biblioteca</td>
    <td>Preenchimento múltiplo Symfony para a extensão Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 7.3+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.0+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.1+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82.git">symfony/polyfill-php82</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill reforçando alguns recursos do PHP 8.2+ para versões mais baixas do PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>biblioteca</td>
    <td>Suporte polifill symfony com alguns recursos PHP 8.3+ para versões PHP mais baixas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>biblioteca</td>
    <td>Executa comandos em subprocessos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contracts</a>
    </td>
    <td>biblioteca</td>
    <td>Abstrações genéricas relacionadas a serviços de escrita</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece uma API voltada para objetos para strings e negócios com bytes, pontos de código UTF-8 e clusters de grafema de forma unificada</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>biblioteca</td>
    <td>Fornece mecanismos para percorrer qualquer variável PHP arbitrária</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">exportador de symfony/var</a>
    </td>
    <td>biblioteca</td>
    <td>Permite exportar qualquer estrutura de dados PHP serializável para código PHP simples</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml.git">symfony/yaml</a>
    </td>
    <td>biblioteca</td>
    <td>Carrega e despeja arquivos YAML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>Biblioteca JSON Object Signing and Encryption para PHP e Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>biblioteca</td>
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
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-vale-presente
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-vale-presente-conta
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-wrapping
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-award
    </td>
    <td>magento2-module</td>
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
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>biblioteca</td>
    <td>Codificador CBOR para PHP</td>
  </tr>
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
      PayPal/módulo-braintree-core
    </td>
    <td>magento2-módulo</td>
    <td>Bifurcação do Magento Braintree módulo 2.2.0 por Gene Comércio para PayPal.</td>
  </tr>
  </tbody>
</table>
