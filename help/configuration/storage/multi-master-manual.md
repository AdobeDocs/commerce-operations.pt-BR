---
title: Configurar manualmente bancos de dados principais
description: Consulte orientações sobre como configurar manualmente a solução de banco de dados dividido.
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# Configurar manualmente bancos de dados principais

{{ee-only}}

{{deprecate-split-db}}

Se o aplicativo Commerce já estiver em produção ou se você já tiver instalado o código personalizado ou os componentes, talvez seja necessário configurar bancos de dados divididos manualmente. Antes de continuar, entre em contato com o Suporte da Adobe Commerce para ver se isso é necessário no seu caso.

A divisão manual de bancos de dados envolve:

- Criar os bancos de dados do sistema de gerenciamento de pedidos e check-out (OMS)
- Execute uma série de scripts SQL que:

   - Soltar chaves estrangeiras
   - Fazer backup de tabelas de banco de dados de vendas e cotações
   - Mover tabelas do banco de dados principal para os bancos de dados de vendas e cotações

>[!WARNING]
>
>Se qualquer código personalizado usar JOINs com tabelas nos bancos de dados de vendas e cota, você _não é possível_ usar bancos de dados divididos. Em caso de dúvida, entre em contato com os autores de qualquer código personalizado ou extensão para garantir que seu código não use JOINs.

Este tópico usa as seguintes convenções de nomenclatura:

- O nome do banco de dados principal é `magento` e seu nome de usuário e senha são `magento`
- O nome do banco de dados de aspas é `magento_quote` e seu nome de usuário e senha são `magento_quote`

   O banco de dados de cotações também é chamado de _check-out_ banco de dados.

- O nome do banco de dados de vendas é `magento_sales` e seu nome de usuário e senha são `magento_sales`

   O banco de dados de vendas também é conhecido como banco de dados OMS.

>[!INFO]
>
>Este guia pressupõe que todos os três bancos de dados estejam no mesmo host que o aplicativo Commerce. No entanto, a escolha de onde localizar os bancos de dados e seu nome depende de você. Esperamos que nossos exemplos tornem as instruções mais fáceis de seguir.

## Fazer backup do sistema Commerce

A Adobe recomenda que você faça backup do banco de dados e do sistema de arquivos atuais para poder restaurá-los caso tenha problemas durante o processo.

**Para fazer backup do seu sistema**:

1. Faça logon no servidor do Commerce como ou alterne para a [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Digite os seguintes comandos:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Prossiga para a próxima seção.

## Configurar bancos de dados principais adicionais

Esta seção discute como criar instâncias de banco de dados para tabelas de vendas e cotações.

**Para criar bancos de dados de vendas e cotações OMS**:

1. Faça logon no servidor de banco de dados como qualquer usuário.
1. Digite o seguinte comando para obter um prompt de comando do MySQL:

   ```bash
   mysql -u root -p
   ```

1. Insira o MySQL `root` senha do usuário quando solicitado.
1. Insira os seguintes comandos na ordem mostrada para criar instâncias de banco de dados chamadas `magento_quote` e `magento_sales` com os mesmos nomes de usuário e senhas:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` para sair do prompt de comando.

1. Verifique os bancos de dados, um de cada vez:

   banco de dados quote:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Se o monitor MySQL for exibido, você criou o banco de dados corretamente. Se um erro for exibido, repita os comandos anteriores.

1. Prossiga para a próxima seção.

## Configurar o banco de dados de vendas

Esta seção discute como criar e executar scripts SQL que alteram tabelas de banco de dados de cotas e fazer backup dos dados dessas tabelas.

Os nomes das tabelas do banco de dados de vendas começam com:

- `salesrule_`
- `sales_`
- `magento_sales_`
- A variável `magento_customercustomattributes_sales_flat_order` a tabela também é afetada

>[!INFO]
>
>Esta seção contém scripts com nomes de tabela de banco de dados específicos. Se você tiver executado personalizações ou se quiser ver uma lista completa de tabelas antes de executar ações nelas, consulte [Scripts de referência](#reference-scripts).

Para obter mais informações, consulte:

- [Criar scripts SQL do banco de dados de vendas](#create-sales-database-sql-scripts)
- [Fazer backup dos dados de vendas](#back-up-sales-data)

### Criar scripts SQL do banco de dados de vendas

Crie os seguintes scripts SQL em um local acessível ao usuário como quem você fez logon no servidor do Commerce. Por exemplo, se você efetuar login ou executar comandos como `root`, é possível criar os scripts na variável `/root/sql-scripts` diretório.

#### Remover chaves estrangeiras

Esse script remove chaves estrangeiras que se referem a tabelas não relacionadas a vendas do banco de dados de vendas.

Crie o script a seguir e dê um nome como `1_foreign-sales.sql`. Substituir `<your main DB name>` com o nome do banco de dados.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Configurar o banco de dados de vendas

Execute o script anterior:

1. Faça logon no banco de dados MySQL como o `root` ou usuário administrativo:

   ```bash
   mysql -u root -p
   ```

1. No `mysql>` execute o script da seguinte maneira:

   ```shell
   source <path>/<script>.sql
   ```

   Por exemplo,

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Após a execução do script, insira `exit`.

### Fazer backup dos dados de vendas

Esta seção discute como fazer backup das tabelas de vendas do banco de dados principal do Commerce para que você possa restaurá-las no banco de dados de vendas separado.

Se você estiver no `mysql>` , digite `exit` para retornar ao shell de comando.

Execute o seguinte `mysqldump` comandos, um de cada vez, no shell de comandos. Em cada um, substitua o seguinte:

- `<your database root username>` com o nome do usuário raiz do banco de dados
- `<your database root user password>` com a senha do usuário
- `<your main Commerce DB name>` com o nome do banco de dados do Commerce
- `<path>` com um caminho de sistema de arquivos gravável

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Restaurar dados de vendas

Esse script restaura os dados de vendas no banco de dados de cotações.

#### Requisito NDB

Se você estiver usando um [Banco de Dados de Rede (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Converter tabelas do InnoDb para o tipo NDB em arquivos de despejo:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Remova linhas com uma chave FULLTEXT dos despejos porque as tabelas do NDB não oferecem suporte a FULLTEXT.

#### Restaurar os dados

Execute os seguintes comandos:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Onde

- `<your sales DB name>` com o nome do seu banco de dados de vendas.

   Neste tópico, o nome do banco de dados de amostra é `magento_sales`.

- `<root username>` com seu nome de usuário raiz do MySQL
- `<root user password>` com a senha do usuário
- Verificar o local dos arquivos de backup criados anteriormente (por exemplo, `/var/sales.sql`)

## Configurar o banco de dados de cotações

Esta seção discute as tarefas necessárias para eliminar chaves estrangeiras das tabelas do banco de dados de vendas e mover tabelas para o banco de dados de vendas.

>[!INFO]
>
>Esta seção contém scripts com nomes de tabela de banco de dados específicos. Se você tiver executado personalizações ou se quiser ver uma lista completa de tabelas antes de executar ações nelas, consulte [Scripts de referência](#reference-scripts).

Os nomes das tabelas do banco de dados de cotações começam com `quote`. A variável `magento_customercustomattributes_sales_flat_quote` e `magento_customercustomattributes_sales_flat_quote_address` as tabelas também são afetadas

### Remover chaves estrangeiras de tabelas de cotações

Esse script remove as chaves estrangeiras que se referem a tabelas de não-aspas das tabelas de aspas. Substituir `<your main Commerce DB name>` com o nome do banco de dados do Commerce.

Crie o script a seguir e dê um nome como `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Execute o script da seguinte maneira:

1. Faça logon no banco de dados MySQL como o usuário raiz ou administrativo:

   ```bash
   mysql -u root -p
   ```

1. No `mysql >` execute o script da seguinte maneira:
   `source <path>/<script>.sql`

   Por exemplo,

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Depois que o script for executado, insira `exit`.

### Fazer backup de tabelas de cotações

Esta seção discute como fazer backup das tabelas de cotações do banco de dados principal e restaurá-las no banco de dados de cotações.

Execute o seguinte comando em um prompt de comando:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### Requisito NDB

Se você estiver usando um [Banco de Dados de Rede (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Converter tabelas do InnoDb para o tipo NDB em arquivos de despejo:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Remova linhas com uma chave FULLTEXT dos despejos porque as tabelas do NDB não oferecem suporte a FULLTEXT.

### Restaurar tabelas para o banco de dados de cotações

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Excluir tabelas de vendas e cotações do banco de dados

Esse script fornece tabelas de vendas e cotações do banco de dados do Commerce. Substituir `<your main DB name>` com o nome do banco de dados do Commerce.

Crie o script a seguir e dê um nome como `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Execute o script da seguinte maneira:

1. Faça logon no banco de dados MySQL como o usuário raiz ou administrativo:

   ```bash
   mysql -u root -p
   ```

1. No `mysql>` execute o script da seguinte maneira:

   ```shell
   source <path>/<script>.sql
   ```

   Por exemplo,

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Depois que o script for executado, insira `exit`.

## Atualizar a configuração de implantação

A etapa final na divisão manual dos bancos de dados é adicionar informações de conexão e recursos à configuração de implantação do Commerce, `env.php`.

Para atualizar a configuração de implantação:

1. Faça logon no servidor do Commerce como ou alterne para a [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Faça backup da configuração de implantação:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Abertura `<magento_root>/app/etc/env.php` em um editor de texto e atualizá-lo usando as diretrizes discutidas nas seções a seguir.

### Atualizar conexões de banco de dados

Localize o bloco que começa com `'default'` (em `'connection'`) e adicione `'checkout'` e `'sales'` seções. Substitua os valores de amostra por valores apropriados para o seu site.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Atualizar recursos

Localize o bloco que começa com `'resource'` e adicionar `'checkout'` e `'sales'` seções, como se segue:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Scripts de referência

Esta seção fornece scripts que você pode executar e que imprimem uma lista completa de tabelas afetadas sem executar nenhuma ação nelas. Você pode usá-las para ver quais tabelas são afetadas antes de dividir os bancos de dados manualmente, o que pode ser útil se você usar extensões que personalizam o esquema do banco de dados.

Para usar esses scripts:

1. Crie um script SQL com o conteúdo de cada script nesta seção.
1. Em cada script, substitua `<your main DB name>` com o nome do banco de dados do Commerce.

   Neste tópico, o nome do banco de dados de amostra é `magento`.

1. Execute cada script a partir do `mysql>` solicitar como `source <script name>`
1. Examine a saída.
1. Copie o resultado de cada script para outro script SQL, removendo os caracteres de barra vertical (`|`).
1. Execute cada script a partir do `mysql>` solicitar como `source <script name>`.

   A execução desse segundo script executa as ações no banco de dados principal do Commerce.

### Remover chaves estrangeiras (tabelas de vendas)

Esse script remove chaves estrangeiras que se referem a tabelas não relacionadas a vendas do banco de dados de vendas.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Remover chaves estrangeiras (tabelas de aspas)

Esse script remove as chaves estrangeiras que se referem a tabelas de não-aspas das tabelas de aspas.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Descartar tabelas de vendas

Esse script remove as tabelas de vendas do banco de dados do Commerce.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Tabelas de citação

Descartar todas as tabelas que comecem com `quote_`.
