---
title: Tamanho do cache do Realpath
description: Saiba como otimizar o desempenho do Adobe Commerce atualizando a configuração do cache readlpath do PHP para usar as configurações recomendadas.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Práticas recomendadas de configuração do cache Realpath

O cache do Realpath armazena em cache os caminhos reais do sistema de arquivos dos nomes de arquivos referenciados, em vez de pesquisá-los sempre. Toda vez que várias funções de arquivo são executadas ou requerem um arquivo e usar um caminho relativo, o PHP tem que procurar onde esse arquivo realmente existe.

Para melhorar o desempenho do Commerce, use as seguintes configurações recomendadas para configurar o `realpath_cache` configurações no `php.ini` arquivo:

- Defina o tamanho do cache como 10 MB (`realpath cache_size=10M`)
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
- [A &quot;Atualização programada&quot; dos indexadores otimiza o desempenho do Magento](../maintenance/indexer-configuration.md)
