---
title: Configurar armazenamento em cache
description: Saiba mais sobre mecanismos de armazenamento em cache e opções de configuração para aplicativos do Adobe Commerce. Descubra alternativas para o cache padrão do sistema de arquivos.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Configurar armazenamento em cache

O [!DNL Commerce] permite que você configure alternativas para o cache padrão do sistema de arquivos. Este guia discute algumas dessas alternativas, a saber:

- Configure os seguintes mecanismos de cache na configuração [!DNL Commerce]:

   - [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de arquivos (padrão): nenhuma configuração é necessária para usar o cache padrão do sistema de arquivos.

- Configurar o [Verniz](config-varnish.md) sem modificar a configuração [!DNL Commerce].

## Terminologia de cache

[!DNL Commerce] usa a seguinte terminologia de cache:

- **Front-end**—Semelhante a uma interface ou gateway para armazenamento em cache, implementado por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de cache** — Pode ser um dos tipos fornecidos com [!DNL Commerce] ou você pode [criar o seu próprio](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Back-end** — Especifica detalhes sobre [armazenamento em cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Back-end de dois níveis** — Armazena registros de cache em dois back-end: um mais rápido e um mais lento.

  >[!INFO]
  >
  >A configuração do cache de back-end de dois níveis está fora do escopo deste guia.

## Opções de configuração

- Modificando o front-end do cache `default` fornecido—

  Você modifica somente o arquivo `<magento_root>/app/etc/di.xml`, a configuração de injeção de dependência global do aplicativo Commerce.

- Configurar seu próprio front-end de cache personalizado—

  Você modifica somente o arquivo `<magento_root>/app/etc/env.php` porque ele substitui a configuração equivalente no arquivo `di.xml`.

>[!TIP]
>
>O verniz não requer alterações na configuração [!DNL Commerce]. Consulte [Configurar e usar verniz](config-varnish.md).
