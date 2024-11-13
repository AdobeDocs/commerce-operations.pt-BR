---
title: Prática recomendada para tamanho de memória OPcache
description: Descreve como evitar a degradação de desempenho por configurações específicas de consumo de memória OPcache em projetos Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Prática recomendada para o tamanho da memória do OPcache no Adobe Commerce

Para a arquitetura do plano Pro do Adobe Commerce na infraestrutura em nuvem 2.3.x, é recomendável definir `opcache.memory_consumption` para pelo menos 2 GB, para evitar degradação do desempenho.

## Produtos e versões afetados

* Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce 2.3.x
* PHP 7.0 e posterior

## Configurar memória

Aloque pelo menos **2GB** de memória para o [módulo OPcache PHP](https://www.php.net/manual/en/book.opcache.php). O módulo OPcache está configurado no arquivo `php.ini`. Para alocar 2048 MB de memória, defina `opcache.memory_consumption = 2048`.

## Informações adicionais

* [Práticas recomendadas de desempenho - Configurações do PHP](../../../performance/software.md#php-settings)
* [Configurar opções do PHP](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
* [Problemas mais comuns de banco de dados no Adobe Commerce na infraestrutura em nuvem](../maintenance/resolve-database-performance-issues.md)
* [A &quot;Atualização programada&quot; dos indexadores otimiza o desempenho do Adobe Commerce](../maintenance/indexer-configuration.md)
