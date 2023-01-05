---
title: Configurar Redis
description: Obtenha uma visão geral dos recursos do Redis e inicie a configuração do Redis.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Configurar Redis

Os recursos de Redis incluem:

- armazenamento de sessão PHP
- Limpeza de cache com base em tag sem `foreach` loops
- Salvamentos em disco e replicação principal/escrava

## Instalar o Redis

A instalação e configuração do software Redis está além do escopo deste guia. Consulte recursos como:

- [Baixar a página Redis](https://redis.io/download)
- [Início rápido de Redis](https://redis.io/docs/getting-started/)
- [Oceano digital](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página Documentação do Redis](https://redis.io/docs)

## Configurar a configuração do Redis

Dependendo da sua instalação, você geralmente pode encontrar a configuração do Redis em um dos seguintes arquivos: `/etc/redis/redis.conf` ou `/etc/redis/<port>.conf`

Para otimizar a instância do Redis de acordo com seus requisitos, você obtém melhores resultados usando uma instância dedicada para cada sessão, Cache de comércio e FPC.

Para sessões, o Adobe recomenda que você ative a persistência para copiar os dados do Redis para o disco usando uma das seguintes opções de persistência: instantâneos regulares de RDB (Redis Database Backup) ou registros de persistência de somente arquivo de anexação (AOF).

- **Backup do Banco de Dados Redis** Os instantâneos do (RDB) armazenam o banco de dados completo em um arquivo de despejo após um determinado tempo, quando um número mínimo de chaves foi alterado desde o último salvamento. Use o `save` na configuração `redis.conf` para configurar essa configuração.

- **Anexar apenas arquivo** (AOF) armazena cada operação de gravação enviada a Redis em um arquivo de diário. O Redis lê este arquivo somente na reinicialização e o usa para restaurar o conjunto de dados original.

Você também pode ativar as opções RDB e AOF ao mesmo tempo. Para obter detalhes adicionais, incluindo as vantagens e desvantagens das opções de persistência, consulte o [Documentação de Persistência de Redis](https://redis.io/topics/persistence).

Para a instância do cache, configure a instância de forma que seja grande o suficiente para armazenar todo o cache do Commerce. Os requisitos de tamanho dependem de fatores diferentes, como o número de produtos e visualizações de loja. Como ponto de partida, você pode usar o tamanho da pasta de cache em seu sistema de arquivos. Por exemplo, se a variável `var/cache` A pasta no seu sistema de arquivos é de 5 GB, configure a instância do Redis com pelo menos 5 GB para iniciar. A persistência não é necessária para a instância do cache porque o cache do Commerce pode ser restaurado. Consulte [Guia de cache de Redis](https://redis.io/docs/manual/eviction/).

Para o ajuste de desempenho, você pode ativar as seguintes configurações para exclusão assíncrona. Essas configurações não alteram o comportamento de Redis.

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
