---
title: Disponibilidade do produto
description: Saiba mais sobre quais recursos do Adobe Commerce são compatíveis no momento e verifique sua compatibilidade com versões específicas do Adobe Commerce.
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: 3592b81b260eee7d3889f3f9cf702d8f13aacae3
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 15%

---

# Disponibilidade do produto

A tabela a seguir descreve o status da disponibilidade do software Adobe Commerce e onde obtê-lo, especialmente para software que está disponível fora do pacote convencional do Adobe Commerce Composer.

Os serviços e as extensões são testados na versão mais recente lançada do Commerce no momento do lançamento dos produtos.

As versões compatíveis foram totalmente testadas pelo Adobe. A assistência para versões compatíveis está disponível no Suporte ao cliente do Adobe. As versões mais antigas podem funcionar corretamente, mas não são oficialmente compatíveis.

>[!NOTE]
>
>O suporte para versões do Adobe Commerce também inclui suporte para [patches de segurança disponíveis](versions.md).

## Extensões criadas no Adobe

Essas extensões do Adobe Commerce são dissociadas da base de código principal do Adobe Commerce. Isso permite que o Adobe libere iterações dessas extensões em um período mais flexível e forneça aos clientes acesso antecipado a novos recursos.


A tabela a seguir mostra o suporte à versão para cada extensão relativa à versão do Adobe Commerce.

| **Versões do Adobe Commerce** | 2.4.7-beta2 | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                          |
|---------------------------------------|-------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Eventos Adobe I/O para Adobe Commerce_ | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | - | [Compositor](https://developer.adobe.com/commerce/extensibility/events/installation/) <br/>[Notas de versão](https://developer.adobe.com/commerce/extensibility/events/release-notes/) |
| _B2B_ | 1.4.2 | 1.4.0+ | 1.3.5+ | 1.3.4 | 1.3.3 | 1.3.2 | [Compositor](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _Conector Experience Platform_ | 3.0.0-beta1 | 3.0.0-beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _Page Builder_ | - | - | 1.7.3 | 1.7.2 | 1.7.1 | - | [Guia do usuário](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |

## Commerce Services

[Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) O é um conjunto de recursos hospedados no Adobe que fornecem funcionalidade robusta e tempos de resposta rápidos, juntamente com a sua instância do Commerce.

Recomenda-se que os comerciantes usem a versão mais recente de um serviço para garantir a maior estabilidade e funcionalidade. A documentação descreve a versão lançada no momento.

* No momento, os Serviços da Adobe Commerce são compatíveis com o Commerce 2.4.4 e posterior. É recomendável que os comerciantes usem a versão mais recente do serviço.
* Os serviços são considerados compatíveis com as versões anteriores do Commerce 2.4.x, mas não são oficialmente compatíveis.
* Os serviços não são compatíveis com o Commerce 2.3.x, exceto com o Product Recommendations 3.3.7 e versões anteriores.

A tabela a seguir mostra o suporte à versão para cada serviço em relação à versão do Adobe Commerce.

| **Versões do Adobe Commerce** | 2.4.7-beta2 | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                                |
|----------------------------------------|-------------|-------------|--------|-----------------|-----------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Sales Channel Amazon_ | - | - | 4.4.0+ | 4.3.0+ | 4.3.0+ | 4.3.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _Serviço de catálogo do Adobe Commerce_ | 1.11 | 1.11 | 1.11 | 1.11 | 1.11 | - | [Visão geral](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _Gerenciador de canais_ | - | - | 2.0.0 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _Live Search_ | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | - | [Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _Payment Services_ | 2.2.0 | 2.2.0 | 2.2.0 | PHP 8.1 | PHP 8.1 | - | [Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [Notas de versão](https://commercemarketplace.adobe.com/magento-payment-services.html) |
| _Recommendations do produto_ | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | - | [Marketplace](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Check-out rápido_ | - | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Processamento na loja para o Adobe Commerce_ | - | - | 1.5.0 | 1.2.0+ | 1.2.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [Notas de versão](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |
