---
title: Configurar o Redis com o AWS ElastiCache
description: Para instâncias do Commerce hospedadas no EC2, saiba como usar o AWS ElastiCache no lugar de uma instância local do Redis. Descubra técnicas de configuração, de configuração e de validação da linha de comando.
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Configurar o Redis com o AWS ElastiCache

A partir do Commerce 2.4.3, as instâncias hospedadas no Amazon EC2 podem usar um AWS ElastiCache no lugar de uma instância local do Redis.

>[!WARNING]
>
>Esta seção é aplicável somente para instâncias do Commerce em execução em VPCs do Amazon EC2. Ele não funciona em instalações locais.

## Pré-requisitos

- **Criar um cache sem servidor do Redis OSS**—No Console de Gerenciamento do AWS, crie o cache do Redis na mesma região e VPC da instância EC2. Para obter instruções, consulte a [documentação do AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Verifique a conexão com sua instância EC2 Commerce**

   - Abra uma conexão SSH com sua instância EC2
   - Na instância EC2, instale o cliente Redis:

     ```bash
     sudo apt-get install redis
     ```

   - Adicionar uma regra de entrada ao grupo de segurança EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Adicione uma regra de entrada ao grupo de segurança do Cluster ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conecte-se à CLI Redis:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configurar o Commerce para usar o cluster

O Commerce oferece suporte a vários tipos de configurações de cache. Geralmente, as configurações de armazenamento em cache são divididas entre front-end e back-end. O armazenamento em cache front-end está classificado como `default`, usado para qualquer tipo de cache. Você pode personalizar ou dividir em caches de nível inferior para obter melhor desempenho. Uma configuração comum do Redis é separar o cache padrão e o cache de página em seu próprio banco de dados Redis (RDB).

Execute comandos `setup` para especificar os pontos de extremidade Redis.

Para configurar o Commerce para Redis como cache padrão:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Para configurar o Commerce para o cache de página Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Para configurar o Commerce para usar o Redis para armazenamento de sessão:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificar conectividade

**Para verificar se o Commerce está se comunicando com ElastiCache**:

1. Abra uma conexão SSH com a instância do Commerce EC2.
1. Inicie o monitor Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Abra uma página na interface do Commerce.
1. Verifique a [saída do cache](#verify-the-redis-connection) em seu terminal.
