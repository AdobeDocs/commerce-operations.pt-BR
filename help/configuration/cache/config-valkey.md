---
title: Configurar Valkey
description: Saiba como configurar o cache do Valkey para otimização de desempenho do Adobe Commerce. Descubra recursos, etapas de instalação e práticas recomendadas de configuração.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Configurar Valkey

Os principais recursos incluem:

- Armazenamento de sessão PHP
- Limpeza do cache com base em marcas sem `foreach` loops
- Salvamentos no disco e replicação mestre/escravo

## Instalar Valkey

Para instalar e configurar o software Valkey, consulte os seguintes recursos:

- [Baixar página Valkey](https://valkey.io/download/)
- [Início rápido do Valkey](https://valkey.io/topics/quickstart/)
- [Página de documentação da Valkey](https://valkey.io/docs)

## Definir a configuração do Valkey

Dependendo da sua instalação, você geralmente pode encontrar sua configuração Valkey no arquivo `/etc/valkey/valkey.conf` ou `/etc/valkey/<port>.conf`.

Para otimizar a instância do Valkey para seus requisitos, você pode obter os melhores resultados usando uma instância dedicada para cada sessão, cache do Commerce e FPC.

A Adobe recomenda ativar a persistência para que as sessões copiem dados Valkey para o disco. Você pode usar instantâneos Valkey Database Backup (RDB) ou logs de persistência Anexar Somente Arquivo (AOF).

- Os instantâneos do **RDB** (Banco de Dados Valkey) armazenam o banco de dados completo em um arquivo de despejo após um determinado tempo, quando um número mínimo de chaves foi alterado desde o último salvamento. Use a configuração `save` dentro do arquivo `valkey.conf` para definir essa configuração.

- **Anexar Somente Arquivo** (AOF) armazena cada operação de gravação enviada para Valkey em um arquivo de diário. A Valkey lê esse arquivo somente na reinicialização e o usa para restaurar o conjunto de dados original.

Você também pode ativar as opções RDB e AOF ao mesmo tempo. Para obter detalhes adicionais, incluindo as vantagens e desvantagens das opções de persistência, consulte a [documentação sobre Persistência Valkey](https://valkey.io/topics/persistence/).

Para a instância de cache, configure-a de modo que seja grande o suficiente para armazenar todo o cache do Commerce. Os requisitos de tamanho dependem de fatores diferentes, como o número de produtos e as visualizações da loja. Como ponto de partida, você pode usar o tamanho da pasta de cache no sistema de arquivos. Por exemplo, se a pasta `var/cache` no sistema de arquivos tiver 5 GB, configure a instância do Valkey com pelo menos 5 GB para começar. A persistência não é necessária para a instância de cache porque o cache do Commerce pode ser restaurado.

Para ajuste de desempenho, é possível ativar as seguintes configurações para exclusão assíncrona. Essas configurações não alteram o comportamento do Valkey.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
