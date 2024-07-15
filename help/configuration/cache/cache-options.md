---
title: Opções de cache
description: Configure o acesso ao armazenamento em cache de baixo nível.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Opções de cache de baixo nível

O aplicativo Commerce usa um front-end e back-end de cache de baixo nível para fornecer acesso ao armazenamento em cache.

## Cache de front-end de baixo nível

O Commerce estende o [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando o cache de front-end [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

## Cache de back-end de baixo nível

Em geral, o aplicativo Commerce funciona com qualquer cache de back-end ao qual o [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) ofereça suporte. No entanto, este guia aborda apenas os seguintes caches de back-end de baixo nível:

- [Redis](config-redis.md)
- [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Sistema de arquivos (padrão): nenhuma configuração é necessária para usar o cache do sistema de arquivos.

[Verniz](config-varnish.md) não requer a configuração de um back-end de cache de baixo nível.
