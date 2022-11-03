---
title: Prática recomendada para o tamanho da memória do OPcache
description: Descreve como evitar a degradação do desempenho por configurações específicas do consumo de memória OPcache em projetos Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Prática recomendada para o tamanho da memória do OPcache no Adobe Commerce

Para o Adobe Commerce on cloud Infrastructure Pro plan architecture 2.3.x, é recomendável definir `opcache.memory_consumption` para, pelo menos, 2 GB, a fim de evitar a degradação do desempenho.

## Produtos e versões afetados

* Arquitetura do plano Adobe Commerce on cloud Infrastructure Pro 2.3.x
* PHP 7.0 e posterior

## Configurar memória

Alocar pelo menos **2 GB** da memória para o [Módulo PHP OPcache](https://www.php.net/manual/en/book.opcache.php). O módulo OPcache é configurado na variável `php.ini` arquivo. Para alocar 2048 MB de memória, defina `opcache.memory_consumption = 2048`.

## Informações adicionais

* [Práticas recomendadas de desempenho - Configurações PHP](../../../performance/software.md#php-settings)
* [Configurar opções do PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
* [Problemas mais comuns do banco de dados no Adobe Commerce na infraestrutura em nuvem](../maintenance/resolve-database-performance-issues.md)
* [Os indexadores &quot;Atualizar conforme o cronograma&quot; otimizam o desempenho da Adobe Commerce](../maintenance/indexer-configuration.md)
