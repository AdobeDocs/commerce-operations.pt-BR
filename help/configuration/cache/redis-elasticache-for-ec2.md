---
title: Configurar o Redis com o AWS ElastiCache
description: Saiba como usar o AWS ElastiCache como um back-end Redis para Adobe Commerce no EC2. Descubra a configuração, a validação e a definição da linha de comando.
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# Configurar o Redis com o AWS ElastiCache

A partir do Commerce 2.4.3, as instâncias hospedadas no Amazon EC2 podem usar um AWS ElastiCache no lugar de uma instância local do Redis.

>[!WARNING]
>
>Esta seção é aplicável somente para instâncias do Commerce em execução em VPCs do Amazon EC2.

## Pré-requisitos

- **Criar um cache sem servidor do Redis OSS**—No Console de Gerenciamento do AWS, crie o cache do Redis na mesma região e VPC da instância EC2. Para obter instruções, consulte a [documentação do AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Verifique a conexão com sua instância EC2 Commerce**

   - Abra uma conexão SSH com sua instância EC2
   - Na instância EC2, instale o cliente Redis:

     ```shell
     sudo apt-get install redis
     ```

   - Adicionar uma regra de entrada ao grupo de segurança EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Adicione uma regra de entrada ao grupo de segurança do Cluster ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conecte-se à CLI Redis:

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configurar o Commerce para usar o cluster

O Commerce oferece suporte a vários tipos de configurações de cache. Geralmente, as configurações de armazenamento em cache são divididas entre front-end e back-end. O armazenamento em cache front-end está classificado como `default`, usado para qualquer tipo de cache. Você pode personalizar ou dividir em caches de nível inferior para obter melhor desempenho. Uma configuração comum do Redis é separar o cache padrão e o cache de página em seu próprio banco de dados Redis (RDB).

Execute comandos `setup` para especificar os pontos de extremidade Redis.

Para configurar o Commerce para Redis como cache padrão:

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Para configurar o Commerce para o cache de página Redis:

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Para configurar o Commerce para usar o Redis para armazenamento de sessão:

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificar conectividade

**Para verificar se o Commerce está se comunicando com ElastiCache**:

1. Abra uma conexão SSH com a instância do Commerce EC2.
1. Inicie o monitor Redis.

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Abra uma página na interface do Commerce.
1. Verifique a [saída do cache](#verify-connectivity) em seu terminal.
