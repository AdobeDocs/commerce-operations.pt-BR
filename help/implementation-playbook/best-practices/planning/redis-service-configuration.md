---
title: Práticas recomendadas para a configuração do serviço Redis
description: Saiba como melhorar o desempenho do armazenamento em cache usando a implementação estendida do cache Redis para o Adobe Commerce 2.3.5.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Práticas recomendadas para a configuração do serviço Redis

- Para o Adobe Commerce 2.3.3 e posterior implantado na infraestrutura de nuvem, atualize para o Redis versão 5.0.
- Para o Adobe Commerce versão 2.3.5 ou superior, use a implementação estendida do cache de Redis. Essa implementação inclui as seguintes otimizações para minimizar o número de consultas Redis realizadas em cada solicitação do Adobe Commerce:
   - Diminua o tamanho das transferências de dados de rede entre Redis e Adobe Commerce
   - Diminua o consumo de Redis de ciclos da CPU melhorando a capacidade do adaptador de determinar automaticamente o que precisa ser carregado
   - Reduzir as condições de corrida em operações de gravação de Redis

## Produtos e versões afetados

Adobe Commerce na infraestrutura de nuvem com a versão 2.3.3 ou posterior.
Adobe Commerce (todos os métodos de implantação), versão 2.3.5 e posterior

## Atualizar a versão Redis para implantações em nuvem

Para implantações do Adobe Commerce em infraestrutura de nuvem com o Adobe Commerce 2.3.3 ou posterior, atualize o serviço Redis para o Redis versão 5.0. Para obter instruções, consulte os seguintes tópicos na documentação do Adobe Commerce em infraestrutura de nuvem:

- [Configurar o serviço Redis](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Alterar a versão do serviço](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Configurar a implementação estendida do cache de Redis

Para o Adobe Commerce 2.3.5 e superior, atualize sua configuração para usar a implementação estendida do cache de Redis `\Magento\Framework\Cache\Backend\Redis`.

### Configuração para implantações em nuvem

Com `ece-tools` 2002.1.1 ou superior, configure o cache aprimorado do Redis definindo o `REDIS_BACKEND` variável de implantação no arquivo de configuração do ambiente, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Para obter detalhes, consulte [Implantar variáveis > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) na documentação do Adobe Commerce sobre a infraestrutura em nuvem.

>[!NOTE]
>
> Verifique a versão das ferramentas gráficas instaladas no ambiente do Cloud local na linha de comando usando o `composer show magento/ece-tools` comando. Se necessário, [atualizar a versão das ferramentas](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

### Configuração para implantações locais

Para implantações locais do Adobe Commerce, configure a nova implementação do cache do Redis usando o `bin/magento:setup` comandos. Para obter instruções, consulte [Usar Redis para cache padrão](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Informações adicionais

- [Versão Adobe Commerce v2.3.5 - Melhorias de desempenho](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Cache de Página Redis](../../../configuration/cache/redis-pg-cache.md)


