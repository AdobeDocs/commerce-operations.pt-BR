---
title: Gerenciar os indexadores
description: Veja exemplos de como visualizar e gerenciar indexadores do Commerce.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# Gerenciar os indexadores

{{file-system-owner}}

Para exibir uma lista de todos os indexadores:

```bash
bin/magento indexer:info
```

A lista é exibida da seguinte maneira:

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

## Exibir status do indexador

Use este comando para visualizar o status de todos os indexadores ou indexadores específicos. Por exemplo, descubra se um indexador precisa ser reindexado.

Opções de comando:

```bash
bin/magento indexer:status [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omit `[indexer]` para visualizar o status de todos os indexadores.

Exemplo de resultado:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Reindexar

Use este comando para reindexar todos os indexadores ou os selecionados apenas uma vez.

>[!INFO]
>
>Esse comando reindexa apenas uma vez. Para manter os indexadores atualizados, você deve configurar um [trabalho cron](../cli/configure-cron-jobs.md).

Opções de comando:

```bash
bin/magento indexer:reindex [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omit `[indexer]` para reindexar todos os indexadores.

Exemplo de resultado:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>A reindexação de todos os indexadores pode demorar muito para lojas com um grande número de produtos, clientes, categorias e regras promocionais.

### Reindexação em modo paralelo

Os indexadores têm escopo e vários segmentos para suportar a reindexação no modo paralelo. Ele é paralelizado pela dimensão do indexador e é executado em vários threads, reduzindo o tempo de processamento.

Neste contexto, `dimension` é o escopo da reindexação, por exemplo, uma `website` ou apenas um `customer_group`.

A paralelização de índice afeta apenas indexadores com escopo, o que significa que o Commerce divide os dados em várias tabelas usando o indexador como seu escopo, em vez de manter todos os dados em uma única tabela.

Você pode executar os seguintes índices no modo paralelo:

- `Catalog Search Fulltext` pode ser rotulada em paralelo por exibições de loja.
- `Category Product` pode ser rotulada em paralelo por exibições de loja.
- `Catalog Price` pode ser rotulada em paralelo por grupos de sites e de clientes.
- `Catalog Permissions` pode ser em paralelo por grupos de clientes.

Para usar a paralelização, defina um dos modos de dimensões disponíveis para o indexador de preço do produto:

- `none` (padrão)
- `website`
- `customer_group`
- `website_and_customer_group`

Por exemplo, para definir o modo por site:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Para usar a paralelização para permissões de Catálogo, defina um dos modos de dimensões disponíveis para o indexador de Permissões de Catálogo:

- `none` (padrão)
- `customer_group`

Ou para verificar o modo atual:

```bash
bin/magento indexer:show-dimensions-mode
```

Para reindexar no modo paralelo, execute o comando reindex usando a variável de ambiente `MAGE_INDEXER_THREADS_COUNT`ou adicione uma variável de ambiente ao `env.php` arquivo. Essa variável define o número de threads para o processamento de reindexação.

Por exemplo, o comando a seguir executa a variável `Catalog Search Fulltext` indexador em três threads:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Redefinir indexador

Use este comando para invalidar o status de todos os indexadores ou indexadores específicos.

Opções de comando:

```bash
bin/magento indexer:reset [indexer]
```

Onde ```[indexer]``` é uma lista de indexadores separada por espaços. Omit `[indexer]` para invalidar todos os indexadores.

Exemplo de resultado:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Configurar indexadores

Use este comando para definir as seguintes opções de indexador:

- **Atualizar ao salvar (`realtime`)**: Os dados indexados são atualizados quando uma alteração é feita no Administrador. (Por exemplo, o índice de produtos da categoria é reindexado depois que os produtos são adicionados a uma categoria no Administrador.) Este é o padrão.
- **Atualizar por programação (`schedule`)**: Os dados são indexados de acordo com o agendamento definido pelo seu trabalho cron.

[Saiba mais sobre indexação](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Exibir a configuração atual

Para exibir a configuração atual do indexador:

```bash
bin/magento indexer:show-mode [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omit `[indexer]` para mostrar todos os modos de indexadores. Por exemplo, para mostrar o modo de todos os indexadores:

Exemplo de resultado:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Configurar indexadores

>[!INFO]
>
>Antes de alternar entre modos de indexador, recomendamos colocar seu site na [manutenção](../../installation/tutorials/maintenance-mode.md) modo e [desativar trabalhos do cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Isso garante que você não sofra bloqueios de banco de dados.

Para especificar a configuração do indexador:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Em que:

- `realtime`—Define os indexadores selecionados para atualização ao salvar.
- `schedule`—Define os indexadores especificados a serem salvos de acordo com o cronograma do cron.
- `indexer`—É uma lista de indexadores separada por espaços. Omit `indexer` para configurar todos os indexadores da mesma maneira.

Por exemplo, para alterar somente os produtos da categoria e os indexadores de categorias de produto para atualizar conforme a programação, insira:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemplo de resultado:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Os acionadores de banco de dados relacionados a indexadores são adicionados quando o modo de indexador é definido como `schedule` e removido quando o modo indexador está definido como `realtime`. Se os acionadores estiverem ausentes no banco de dados enquanto os indexadores estiverem definidos como `schedule`, altere os indexadores para `realtime` e depois os altere para `schedule`. Isso redefine os acionadores.
