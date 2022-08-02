---
title: Reverter Banco de Dados Dividido
description: Reverter de uma implementação obsoleta do banco de dados dividido para uma única implementação do banco de dados.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Reverter do Banco de Dados Dividido

{{ee-only}}

Para clientes do Adobe Commerce que implementaram [Dividir Banco de Dados](multi-master.md), o tópico a seguir descreve como reverter ou migrar de volta para um único banco de dados. Recomendamos que os comerciantes da Adobe Commerce que atualmente usam o Banco de Dados Dividido façam upgrade para a versão 2.4.2 e posterior revisem essas etapas, bem como nossas [comunicado](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sobre a desativação planejada do Banco de Dados Dividido.

A reversão de um banco de dados dividido para um único banco de dados envolve a criação de backups do `magento_quote` e `magento_sales` bancos de dados antes de carregá-los no `magento_main` banco de dados.

Neste exemplo, fazemos logon em todos os três bancos de dados, que estão instalados no mesmo host (`magento2-mysql`) como o usuário &quot;raiz&quot;. Você deve substituir esses valores pelos valores apropriados para seus bancos de dados.

1. Crie um backup do `magento_quote` banco de dados:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Crie um backup do `magento_sales` banco de dados:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Carregue o `magento_quote` no banco de dados `magento_main` banco de dados:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Carregue o `magento_sales` no banco de dados `magento_main` banco de dados:

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

1. Remova a configuração de implantação para `checkout` e `sales` no `connections` e `resources` seções da `env.php` arquivo.
1. Restaurar chaves estrangeiras:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifique seu trabalho

Para verificar se a implementação de seu único banco de dados está funcionando corretamente, execute as seguintes tarefas e verifique se os dados foram adicionados ao grupo `magento_main` tabelas de banco de dados usando uma ferramenta de banco de dados como [phpMyAdmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

1. Verifique se as chaves estrangeiras foram restauradas. Por exemplo, a variável `QUOTE_STORE_ID_STORE_STORE_ID` na chave `quote` tabela de banco de dados.
1. Verifique se os clientes podem fazer pedidos na loja.
1. Verifique se os pedidos criados antes de reverter o banco de dados dividido para um único banco de dados estão disponíveis no Administrador.
