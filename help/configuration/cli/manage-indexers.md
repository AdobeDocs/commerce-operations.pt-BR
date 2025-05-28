---
title: Gerenciar os indexadores
description: Consulte exemplos de como exibir e gerenciar indexadores do Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Gerenciar os indexadores

{{file-system-owner}}

Para exibir uma lista de todos os indexadores:

```bash
bin/magento indexer:info
```

A lista é exibida da seguinte maneira:

```
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

>[!NOTE]
>
> Os comerciantes do Adobe Commerce que usam o Live Search, o Serviço de Catálogo ou as Recomendações de Produto têm a opção de usar a [indexação de preço com base em SaaS](https://experienceleague.adobe.com/en/docs/commerce/price-indexer/price-indexing).

## Exibir status do indexador

Use este comando para exibir o status de todos os indexadores ou indexadores específicos. Por exemplo, descubra se um indexador precisa ser reindexado.

Opções de comando:

```bash
bin/magento indexer:status [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omitir `[indexer]` para exibir o status de todos os indexadores.

Exemplo de resultado:

```
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

Use esse comando para reindexar todos os indexadores ou os indexadores selecionados apenas uma vez.

>[!INFO]
>
>Esse comando reindexa apenas uma vez. Para manter os indexadores atualizados, você deve configurar um [trabalho do cron](../cli/configure-cron-jobs.md).

Opções de comando:

```bash
bin/magento indexer:reindex [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omitir `[indexer]` para reindexar todos os indexadores.

Exemplo de resultado:

```
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
>A reindexação de todos os indexadores pode levar muito tempo para lojas com um grande número de produtos, clientes, categorias e regras promocionais.

### Reindexação no modo paralelo

{{php-process-control}}

Os indexadores têm escopo e são multisegmentados para oferecer suporte à reindexação no modo paralelo. Ela é paralelizada pela dimensão do indexador e é executada em várias threads, reduzindo o tempo de processamento.

Neste contexto, `dimension` é o escopo da reindexação, por exemplo, um `website` ou apenas um `customer_group` específico.

A paralelização de índice afeta apenas indexadores com escopo, o que significa que o Commerce divide os dados em várias tabelas usando o indexador como escopo, em vez de manter todos os dados em uma tabela.

Você pode executar os seguintes índices no modo paralelo:

- `Catalog Search Fulltext` pode ser paralelizado por exibições de armazenamento.
- `Category Product` pode ser paralelizado por exibições de armazenamento.
- O `Catalog Price` pode ser comparado a sites e grupos de clientes.
- `Catalog Permissions` pode ser paralelizado por grupos de clientes.

>[!INFO]
>
>A paralelização para Texto completo da pesquisa no catálogo e Produto da categoria é ativada por padrão.

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

Para reindexar no modo paralelo, execute o comando reindex usando a variável de ambiente `MAGE_INDEXER_THREADS_COUNT` ou adicione uma variável de ambiente ao arquivo `env.php`. Essa variável define o número de threads para o processamento de reindexação.

Por exemplo, o comando a seguir executa o indexador `Catalog Search Fulltext` em três threads:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Redefinir indexador

Use este comando para invalidar o status de todos os indexadores ou indexadores específicos.

Opções de comando:

```bash
bin/magento indexer:reset [indexer]
```

Onde ```[indexer]``` é uma lista de indexadores separada por espaços. Omitir `[indexer]` para invalidar todos os indexadores.

Exemplo de resultado:

```
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

Use este comando para definir as seguintes opções do indexador:

- **Atualização ao salvar (`realtime`)**: os dados indexados são atualizados quando uma alteração é feita no Administrador. (Por exemplo, o índice de produtos da categoria é reindexado depois que os produtos são adicionados a uma categoria no Administrador.)
- **Atualizar por agendamento (`schedule`)**: os dados são indexados de acordo com o agendamento definido pelo seu trabalho cron.

[Saiba mais sobre indexação](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Exibir a configuração atual

Para exibir a configuração do indexador atual:

```bash
bin/magento indexer:show-mode [indexer]
```

Onde `[indexer]` é uma lista de indexadores separada por espaços. Omitir `[indexer]` para mostrar os modos de todos os indexadores. Por exemplo, para mostrar o modo de todos os indexadores:

Exemplo de resultado:

```
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

### Definir o modo do indexador

>[!IMPORTANT]
>
>Defina o [!DNL Customer Grid] com `realtime` em vez de `schedule`. O [!DNL Customer Grid] só pode ser reindexado usando a opção [!UICONTROL Update on Save]. Este índice não dá suporte à opção `Update by Schedule`. Use a seguinte linha de comando para definir este indexador para atualizar ao salvar: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Consulte [Práticas recomendadas para a configuração de indexador](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) no _Manual de implementação_.

>[!INFO]
>
>Antes de alternar os modos do indexador, defina o site como [manutenção](../../installation/tutorials/maintenance-mode.md) e [desabilite os trabalhos cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Isso garante que você não seja afetado por bloqueios no banco de dados.

Para especificar a configuração do indexador:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Onde:

- `realtime` — Define os indexadores selecionados para atualização ao salvar.
- `schedule` — Define os indexadores especificados para serem salvos de acordo com o cronograma cron.
- `indexer` — É uma lista de indexadores separada por espaços. Omitir `indexer` para configurar todos os indexadores da mesma maneira.

Por exemplo, para alterar apenas os produtos da categoria e os indexadores de categorias de produto para atualizar no cronograma, insira:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemplo de resultado:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Os gatilhos de banco de dados relacionados a indexadores são adicionados quando o modo do indexador está definido como `schedule` e removidos quando o modo do indexador está definido como `realtime`. Se houver disparadores ausentes no banco de dados enquanto os indexadores estiverem definidos como `schedule`, altere os indexadores para `realtime` e altere-os de volta para `schedule`. Isso redefine os acionadores.

### Definir status do indexador

O comando `bin/magento indexer:set-status` foi introduzido no Adobe Commerce 2.4.7. Ele permite que os administradores modifiquem o status operacional de um ou mais indexadores, otimizando o desempenho do sistema durante operações extensas, como importações, atualizações ou manutenção de dados.

Sintaxe de comando:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Onde:

- `invalid` — Marca os indexadores como desatualizados, solicitando a reindexação na próxima execução do cron, a menos que estejam suspensos.
- `suspended` — Interrompe temporariamente atualizações automáticas acionadas por cron para indexadores. Esse status se aplica aos modos de tempo real e agendamento, garantindo que as atualizações automáticas sejam pausadas durante operações intensivas.
- `valid` — Indica que os dados do indexador estão atualizados, sem necessidade de reindexação.
- `indexer` — É uma lista de indexadores separada por espaços. Omitir `indexer` para configurar todos os indexadores da mesma maneira.

Por exemplo, para suspender indexadores específicos, insira:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Exemplo de resultado:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Gerenciar status do indexador suspenso

Quando um indexador é definido com o status `suspended`, ele afeta principalmente a reindexação automática e as atualizações de exibição materializada. Esta é uma breve visão geral:

**Reindexação ignorada**: a reindexação automática é ignorada para `suspended` indexadores e qualquer indexador que compartilhe o mesmo `shared_index`. Isso garante que os recursos do sistema sejam preservados, não reindexando dados relacionados a processos suspensos.

**Atualizações de Exibição Materializada Ignoradas**: assim como a reindexação, as atualizações de exibições materializadas relacionadas a indexadores `suspended` ou seus índices compartilhados também são pausadas. Essa ação reduz ainda mais a carga do sistema durante os períodos de suspensão.

>[!INFO]
>
>O comando `indexer:reindex` reindexa todos os indexadores, incluindo aqueles marcados como `suspended`, tornando-o útil para atualizações manuais quando os automáticos são pausados.

>[!IMPORTANT]
>
>Alterar o status de um indexador de `suspended` ou `invalid` para `valid` requer cuidado. Essa ação pode levar à degradação do desempenho se houver dados não indexados acumulados.
>
>É crucial garantir que todos os dados sejam indexados com precisão antes de atualizar manualmente o status para `valid` para manter o desempenho do sistema e a integridade dos dados.
