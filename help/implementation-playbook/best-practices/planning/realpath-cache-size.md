---
title: Tamanho do cache do Realpath
description: Saiba como otimizar o desempenho do Adobe Commerce atualizando a configuração do cache do readlpath PHP para usar as configurações recomendadas.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Práticas recomendadas de configuração do cache do Realpath

O cache do Realpath armazena em cache os caminhos reais do sistema de arquivos dos nomes de arquivo referenciados, em vez de pesquisá-los sempre. Toda vez que várias funções de arquivo são executadas ou exigem um arquivo e usam um caminho relativo, o PHP precisa procurar onde esse arquivo realmente existe.

Para melhorar o desempenho do Commerce, use as seguintes configurações recomendadas para definir a variável `realpath_cache` nas `php.ini` arquivo:

- Defina o tamanho do cache para 10 MB (`realpath cache_size=10M`)
- Defina o tempo de vida (ttl) como 7200 segundos (`realpath_cache_ttl=7200`)

Para obter instruções de configuração, consulte [Como definir opções PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Produtos e versões afetados

- Adobe Commerce no local, todas as versões 2.3.x e superior
- Adobe Commerce na infraestrutura de nuvem, todas as versões 2.3.x e superior

## Potencial impacto no desempenho

Se os valores de configuração do cache do Realpath forem muito baixos ou muito altos, ele adicionará uma sobrecarga adicional durante a geração do cache, o que retardará o desempenho.

## Informações adicionais

- [No local: configurações PHP](../../../performance/software.md#php-settings)
- Na infraestrutura de nuvem:
   - [Práticas recomendadas para bancos de dados](database-on-cloud.md)
   - [Problemas mais comuns do banco de dados no Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Os indexadores &quot;Atualizar conforme o agendamento&quot; otimizam o desempenho do Magento](../maintenance/indexer-configuration.md)

