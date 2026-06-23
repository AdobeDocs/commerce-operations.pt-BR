---
title: Instalar e configurar Redis
description: Saiba como instalar e configurar o Redis para armazenamento em cache e armazenamento de sessão com o Adobe Commerce. Descubra opções para otimização e ajuste de desempenho.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T20:26:29.348Z'
TQID: 'https://experienceleague.adobe.com/N61AAy4ihSIlhEjdvpji2XVOdZuHWhytp9zgoAU41K4'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 0%

---

# Instalar e configurar o Redis

O Redis é um armazenamento de dados na memória que pode ser usado como back-end de cache e para armazenamento de sessão. Os principais recursos incluem:

- Armazenamento de sessão PHP
- Limpeza do cache com base em marcas sem `foreach` loops
- Salvamentos no disco e replicação mestre/escravo

{{cloud-cache-config}}

## Instalar Redis

A instalação e configuração do software Redis está fora do escopo deste guia. Consulte recursos como:

- [Página Baixar Redis](https://redis.io/download)
- [Início rápido do Redis](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página da documentação do Redis](https://redis.io/docs)

## Definir a configuração do Redis

Dependendo da sua instalação, você geralmente pode encontrar sua configuração Redis em um dos seguintes arquivos: `/etc/redis/redis.conf` ou `/etc/redis/<port>.conf`

Para otimizar a instância Redis de acordo com seus requisitos, você obtém melhores resultados usando uma instância dedicada a cada sessão, cache do Commerce e FPC.

Para sessões, a Adobe recomenda que você ative a persistência para copiar dados Redis para o disco usando uma das seguintes opções de persistência: instantâneos comuns do Backup do banco de dados Redis (RDB) ou logs de persistência de Anexar somente arquivo (AOF).

- **Os instantâneos do RDB (Backup do Banco de Dados Redis**) armazenam o banco de dados completo em um arquivo de despejo após um determinado tempo, quando um número mínimo de chaves foi alterado desde o último salvamento. Use a configuração `save` dentro do arquivo `redis.conf` para definir essa configuração.

- **Anexar Somente Arquivo** (AOF) armazena cada operação de gravação enviada para Redis em um arquivo de diário. O Redis lê esse arquivo somente ao reiniciar e o usa para restaurar o conjunto de dados original.

Você também pode ativar as opções RDB e AOF ao mesmo tempo. Para obter detalhes adicionais, incluindo as vantagens e desvantagens das opções de persistência, consulte a [documentação sobre Persistência Redis](https://redis.io/topics/persistence).

Para a instância de cache, configure-a de modo que seja grande o suficiente para armazenar todo o cache do Commerce. Os requisitos de tamanho dependem de fatores diferentes, como o número de produtos e as visualizações da loja. Como ponto de partida, você pode usar o tamanho da pasta de cache no sistema de arquivos. Por exemplo, se a pasta `var/cache` no sistema de arquivos tiver 5 GB, configure a instância Redis com pelo menos 5 GB para começar. A persistência não é necessária para a instância de cache porque o cache do Commerce pode ser restaurado. Consulte [Guia de cache Redis](https://redis.io/docs/latest/develop/use/).

Para ajuste de desempenho, é possível ativar as seguintes configurações para exclusão assíncrona. Essas configurações não alteram o comportamento do Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

No Redis 6.x e posterior, você também pode adicionar o seguinte valor:

```ini
lazyfree-lazy-user-del yes
```
