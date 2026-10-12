---
title: Tamanho do cache do Realpath
description: Saiba como otimizar o desempenho do Adobe Commerce atualizando a configuração do cache readlpath do PHP para usar as configurações recomendadas.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Práticas recomendadas de configuração do cache Realpath

O cache do Realpath armazena em cache os caminhos reais do sistema de arquivos dos nomes de arquivos referenciados, em vez de pesquisá-los sempre. Toda vez que várias funções de arquivo são executadas ou requerem um arquivo e usar um caminho relativo, o PHP tem que procurar onde esse arquivo realmente existe.

Para melhorar o desempenho do Commerce, use as seguintes configurações recomendadas para definir as configurações de `realpath_cache` no arquivo `php.ini`:

- Defina o tamanho do cache como 10 MB (`realpath_cache_size=10M`)
- Defina a vida útil (ttl) como 7.200 segundos (`realpath_cache_ttl=7200`)

Para obter instruções de configuração, consulte [Como definir opções do PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Produtos e versões afetados

- Adobe Commerce no local, todas as versões 2.3.x e posteriores
- Adobe Commerce na infraestrutura em nuvem, todas as versões 2.3.x e posteriores

## Possível impacto no desempenho

Se os valores de configuração do cache do Realpath forem muito baixos ou muito altos, isso adicionará uma sobrecarga adicional durante a geração do cache, o que torna o desempenho lento.

## Informações adicionais

- [Local: configurações de PHP](../../../performance/software.md#php-settings)
- Em infraestrutura de nuvem:
  - [Práticas recomendadas do banco de dados](database-on-cloud.md)
  - [Problemas mais comuns de banco de dados no Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [A &quot;Atualização programada&quot; dos indexadores otimiza o desempenho da Magento](../maintenance/indexer-configuration.md)
