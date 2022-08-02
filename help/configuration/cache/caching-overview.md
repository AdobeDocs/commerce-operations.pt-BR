---
title: Configurar armazenamento em cache
description: Saiba mais sobre como armazenar em cache e configurar mecanismos de cache para o aplicativo Adobe Commerce e Magento Open Source.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Configurar armazenamento em cache

[!DNL Commerce] O permite configurar alternativas para o armazenamento em cache do sistema de arquivos padrão. Este guia discute algumas dessas alternativas. nomeadamente,

- Configure o seguinte [cache](https://glossary.magento.com/cache) na [!DNL Commerce] configuração:

   - [Banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de arquivos (padrão): Nenhuma configuração é necessária para usar o armazenamento em cache padrão do sistema de arquivos.

- Configure o [Verniz](config-varnish.md) sem modificar o [!DNL Commerce] configuração.

## Terminologia do armazenamento em cache

[!DNL Commerce] O usa a seguinte terminologia de armazenamento em cache:

- **Fronteira**—Semelhante a uma interface ou gateway para armazenar em cache, implementado por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de cache**—Pode ser um dos tipos fornecidos com [!DNL Commerce] ou você pode [crie seu próprio](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Back-end**—Especifica detalhes sobre [armazenamento em cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Back-end de dois níveis**—Armazena registros de cache em dois backends: mais rápido e mais lento.

   >[!INFO]
   >
   >A configuração de cache de back-end de dois níveis está além do escopo deste guia.

## Opções de configuração

- Modificação do fornecido `default` front-end de cache—

   Você modifica somente o `<magento_root>/app/etc/di.xml` arquivo, o arquivo global do aplicativo Commerce [injeção de dependência](https://glossary.magento.com/dependency-injection) configuração.

- Configuração de seu próprio front-end de cache personalizado—

   Você modifica somente o `<magento_root>/app/etc/env.php` porque substitui a configuração equivalente no `di.xml` arquivo.

>[!TIP]
>
>O verniz não requer alterações na variável [!DNL Commerce] configuração. Consulte [Configurar e usar o Varnish](config-varnish.md).
