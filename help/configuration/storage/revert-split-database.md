---
title: Reverter banco de dados dividido
description: Reverter de uma implementação de banco de dados dividido obsoleta para uma única implementação de banco de dados.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Reverter do Banco de Dados Dividido

{{ee-only}}

Para clientes do Adobe Commerce que implementaram o [Dividir banco de dados](multi-master.md), o tópico a seguir descreve como reverter ou migrar de volta para um único banco de dados. Recomendamos que os comerciantes do Adobe Commerce que atualmente usam o banco de dados dividido e planejam atualizar para a versão 2.4.2 e posterior revisem essas etapas, bem como nosso [comunicado](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) na descontinuação planejada de Split Database.

A reversão de um banco de dados dividido para um único envolve a criação de backups do `magento_quote` e `magento_sales` bancos de dados antes de carregá-los no único `magento_main` banco de dados.

Neste exemplo, fazemos login em todos os três bancos de dados, que estão instalados no mesmo host (`magento2-mysql`) como o usuário &quot;root&quot;. Você deve substituir esses valores pelos valores apropriados para seus bancos de dados.

1. Crie um backup do `magento_quote` banco de dados:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Crie um backup do `magento_sales` banco de dados:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Carregue o `magento_quote` banco de dados na `magento_main` banco de dados:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Carregue o `magento_sales` banco de dados na `magento_main` banco de dados:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Solte o `magento_sales` banco de dados:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Solte o `magento_quote` banco de dados:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Remova a configuração de implantação para `checkout` e `sales` no `connections` e `resources` seções do `env.php` arquivo.
1. Restaurar chaves estrangeiras:

   ```bash
   bin/magento setup:upgrade
   ```

## Verificar seu trabalho

Para verificar se a implementação de seu único banco de dados está funcionando corretamente, execute as tarefas a seguir e verifique se os dados foram adicionados ao `magento_main` tabelas de banco de dados usando uma ferramenta de banco de dados como [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Verifique se chaves estrangeiras foram restauradas. Por exemplo, a variável `QUOTE_STORE_ID_STORE_STORE_ID` na caixa `quote` tabela de banco de dados.
1. Verifique se os clientes podem fazer pedidos da loja.
1. Verifique se os pedidos criados antes de reverter o banco de dados dividido para um único banco de dados estão disponíveis no Administrador.
