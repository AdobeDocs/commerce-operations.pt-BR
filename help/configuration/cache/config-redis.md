---
title: Configurar Redis
description: Obtenha uma visão geral dos recursos Redis e inicie sua configuração Redis.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Configurar Redis

Os recursos do Redis incluem:

- Armazenamento de sessão PHP
- Limpeza do cache com base em marcas sem `foreach` loops
- Salvamentos no disco e replicação mestre/escravo

## Instalar Redis

A instalação e configuração do software Redis está fora do escopo deste guia. Consulte recursos como:

- [Baixar página Redis](https://redis.io/download)
- [Início rápido do Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página da documentação do Redis](https://redis.io/docs)

## Definir a configuração do Redis

Dependendo da sua instalação, você geralmente pode encontrar sua configuração Redis em um dos seguintes arquivos: `/etc/redis/redis.conf` ou `/etc/redis/<port>.conf`

Para otimizar a instância Redis de acordo com seus requisitos, você obtém melhores resultados usando uma instância dedicada a cada sessão, cache do Commerce e FPC.

Para sessões, o Adobe recomenda que você ative a persistência para copiar dados Redis no disco usando uma das seguintes opções de persistência: instantâneos comuns do RDB (Redis Database Backup) ou logs de persistência AOF (Append Only File).

- **Os instantâneos do RDB (Backup do Banco de Dados Redis**) armazenam o banco de dados completo em um arquivo de despejo após um determinado tempo, quando um número mínimo de chaves foi alterado desde o último salvamento. Use a configuração `save` dentro do arquivo `redis.conf` para definir essa configuração.

- **Anexar Somente Arquivo** (AOF) armazena cada operação de gravação enviada para Redis em um arquivo de diário. O Redis lê esse arquivo somente ao reiniciar e o usa para restaurar o conjunto de dados original.

Você também pode ativar as opções RDB e AOF ao mesmo tempo. Para obter detalhes adicionais, incluindo as vantagens e desvantagens das opções de persistência, consulte a [documentação sobre Persistência Redis](https://redis.io/topics/persistence).

Para a instância de cache, configure-a de modo que seja grande o suficiente para armazenar todo o cache do Commerce. Os requisitos de tamanho dependem de fatores diferentes, como o número de produtos e as visualizações da loja. Como ponto de partida, você pode usar o tamanho da pasta de cache no sistema de arquivos. Por exemplo, se a pasta `var/cache` no sistema de arquivos tiver 5 GB, configure a instância Redis com pelo menos 5 GB para começar. A persistência não é necessária para a instância de cache porque o cache do Commerce pode ser restaurado. Consulte [Guia de cache Redis](https://redis.io/docs/manual/eviction/).

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
