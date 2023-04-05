---
title: Opções de cache
description: Configure o acesso ao armazenamento em cache de baixo nível.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Opções de cache de baixo nível

O aplicativo Commerce usa um front-end e back-end de cache de baixo nível para fornecer acesso ao armazenamento de cache.

## Cache de front-end de baixo nível

Extensões de comércio [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) ao aplicar [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) cache de front-end.

## Cache de back-end de baixo nível

Em geral, o aplicativo Commerce funciona com qualquer cache de backend que [Tendência do Zend_Cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) suporta. No entanto, este guia abrange apenas os seguintes caches de backend de baixo nível:

- [Redis](config-redis.md)
- [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Sistema de arquivos (padrão): Nenhuma configuração é necessária para usar o armazenamento em cache do sistema de arquivos.

[Verniz](config-varnish.md) não requer a configuração de um back-end de cache de baixo nível.
