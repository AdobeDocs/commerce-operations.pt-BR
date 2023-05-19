---
title: Configurar armazenamento em cache
description: Saiba mais sobre armazenamento em cache e como configurar mecanismos de cache para o aplicativo Adobe Commerce e Magento Open Source.
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Configurar armazenamento em cache

[!DNL Commerce] O permite configurar alternativas para o cache padrão do sistema de arquivos. Este guia discute algumas dessas alternativas, a saber:

- Configure os seguintes mecanismos de cache no [!DNL Commerce] configuração:

   - [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de arquivos (padrão): nenhuma configuração é necessária para usar o cache padrão do sistema de arquivos.

- Configurar o [Verniz](config-varnish.md) sem modificar o [!DNL Commerce] configuração.

## Terminologia de cache

[!DNL Commerce] O usa a seguinte terminologia de armazenamento em cache:

- **Front-end**— semelhante a uma interface ou gateway para armazenamento em cache, implementado pelo [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de cache**—Pode ser um dos tipos fornecidos com [!DNL Commerce] ou você pode [crie o seu próprio](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Infraestrutura**—Especifica detalhes sobre [armazenamento em cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Infraestrutura de dois níveis**—Armazena registros de cache em dois back-ends: um mais rápido e um mais lento.

   >[!INFO]
   >
   >A configuração do cache de back-end de dois níveis está fora do escopo deste guia.

## Opções de configuração

- Modificação das informações fornecidas `default` front-end do cache—

   Você modifica somente o `<magento_root>/app/etc/di.xml` arquivo, a configuração de injeção de dependência global do aplicativo Commerce.

- Configurar seu próprio front-end de cache personalizado—

   Você modifica somente o `<magento_root>/app/etc/env.php` arquivo porque substitui a configuração equivalente no `di.xml` arquivo.

>[!TIP]
>
>O verniz não requer alterações no [!DNL Commerce] configuração. Consulte [Configurar e usar verniz](config-varnish.md).
