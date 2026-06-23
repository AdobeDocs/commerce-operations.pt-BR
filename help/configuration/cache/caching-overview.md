---
title: Visão geral do armazenamento em cache e opções de configuração
description: Saiba mais sobre armazenamento em cache no Adobe Commerce, incluindo armazenamento de back-end, configuração de front-end e armazenamento em cache de página inteira com cache L2, Vernish, Redis e Valkey.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# Visão geral do armazenamento em cache e opções de configuração

O Adobe Commerce conta com uma arquitetura de cache em várias camadas para reduzir a carga do banco de dados, minimizar o processamento redundante e acelerar a entrega de páginas. No nível do aplicativo, o Commerce mantém mais de uma dúzia de [tipos de cache](../cli/manage-cache.md#clean-and-flush-cache-types), como configuração, layout, HTML de bloco e coleções, cada um deles pode ser roteado para um back-end de armazenamento dedicado como [Redis](config-redis.md) ou [Valkey](config-valkey.md). Para armazenamento em cache de página inteira em implantações locais, a Adobe recomenda [Verniz](config-varnish.md). As implantações do Commerce na nuvem usam o Fastly. Camadas adicionais, como [cache L2](level-two-cache.md) e [assinatura de conteúdo estático](static-content-signing.md), melhoram ainda mais o desempenho de implantações de vários nós e alto tráfego.

Este guia explica como cada camada de armazenamento em cache funciona e mostra como configurar front-ends, back-ends e opções avançadas para atender aos requisitos de implantação.

## Armazenamento em cache de front-ends

Um front-end de cache é uma interface entre o Commerce e o back-end de armazenamento em cache. Você pode definir vários front-ends, cada um com configurações de back-end diferentes, e atribuir [tipos de cache](../cli/manage-cache.md#clean-and-flush-cache-types) específicos a cada front-end.  Para obter detalhes sobre a configuração, consulte [Configurar front-ends do cache](cache-types.md).

## Armazenamento em cache de back-end

Um back-end de cache é o mecanismo de armazenamento subjacente para dados em cache. O Commerce fornece um back-end padrão do sistema de arquivos, mas você pode configurar outros back-end, como Redis ou Valkey, para melhorar o desempenho e a escalabilidade. Para obter detalhes sobre as opções disponíveis, consulte [Opções de back-end do cache](cache-options.md).

## Armazenamento em cache de página inteira com Vernish

O [Cache de Verniz](config-varnish.md) é um acelerador HTTP que armazena páginas inteiras em cache na memória. Para ambientes de produção locais, a Adobe recomenda o Vernish, pois ele é significativamente mais rápido que o cache de página inteira integrado. O Commerce em ambientes na nuvem usa o [Fastly](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/fastly) para armazenamento em cache de página inteira, em vez do Varnish.

>[!NOTE]
>
>O Varnish opera como um proxy reverso na frente do servidor da Web e não requer alterações na configuração de back-end do cache do Commerce.

## Cache L2 (dois níveis)

O [cache L2](level-two-cache.md) armazena os dados do cache localmente em cada nó da Web ao usar um cache remoto (Redis ou Valkey) como fonte da verdade. Isso reduz o tráfego de rede entre os nós da Web e o cache remoto, o que melhora o desempenho para sites de alto tráfego.

## Armazenamento em cache de conteúdo estático

[Assinatura de conteúdo estático](static-content-signing.md) invalida o cache do navegador para recursos estáticos (CSS, JavaScript, imagens) incorporando uma versão de implantação nas URLs de arquivo.

## Terminologia de cache

[!DNL Commerce] usa a seguinte terminologia de cache:

- **Front-end** — Uma interface ou gateway para armazenar em cache, implementado por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de cache** — Um dos tipos internos fornecidos com [!DNL Commerce] (como `config`, `layout`, `block_html`, `full_page`) ou um [tipo personalizado](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Back-end** — Especifica os detalhes do [armazenamento em cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend).
- **Back-end de dois níveis** — Armazena registros de cache em dois back-ends: um cache local (rápido) e um cache remoto (compartilhado). Consulte [configuração do cache L2](level-two-cache.md).

## Opções de configuração

Para mapeamento de front-end para tipo e sintaxe de configuração de cache:

**No local** — A configuração de cache é armazenada em dois arquivos:

- `<magento_root>/app/etc/di.xml` — A configuração de injeção de dependência global. Modifique este arquivo para alterar o front-end do cache `default` fornecido.
- `<magento_root>/app/etc/env.php` — Configuração específica do ambiente. Modifique este arquivo para configurar os front-ends do cache personalizado. Este arquivo substitui a configuração equivalente em `di.xml`.

Para obter detalhes, consulte:

- [Configurar front-ends do cache](cache-types.md)—Associe um front-end do cache a tipos específicos de cache
- [Opções de back-end do cache](cache-options.md)—Referência de opção de back-end

**Adobe Commerce na Nuvem** — Configurar cache com `CACHE_CONFIGURATION` em `.magento.env.yaml`. Consulte [Práticas recomendadas para a configuração do serviço Redis e Valkey](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md).
