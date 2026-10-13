---
title: Reverter banco de dados dividido
description: Reverter de uma implementação de banco de dados dividido obsoleta para uma única implementação de banco de dados.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%
---
# Reverter do Banco de Dados Dividido

{{ee-only}}

Para clientes do Adobe Commerce que implementaram o [Split Database](multi-master.md), o tópico a seguir descreve como reverter ou migrar de volta para um único banco de dados. Recomendamos que os comerciantes do Adobe Commerce que atualmente usam o banco de dados dividido planejem atualizar para a versão 2.4.2 e posterior revisem essas etapas.

A reversão de um banco de dados dividido para um único envolve a criação de backups dos bancos de dados `magento_quote` e `magento_sales` antes de carregá-los no único banco de dados `magento_main`.

Neste exemplo, fazemos logon em todos os três bancos de dados, que estão instalados no mesmo host (`magento2-mysql`) como o usuário &quot;raiz&quot;. Você deve substituir esses valores pelos valores apropriados para seus bancos de dados.

1. Criar um backup do banco de dados `magento_quote`:

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Criar um backup do banco de dados `magento_sales`:

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Carregar o banco de dados `magento_quote` no banco de dados `magento_main`:

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Carregar o banco de dados `magento_sales` no banco de dados `magento_main`:

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Descartar o banco de dados `magento_sales`:

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Descartar o banco de dados `magento_quote`:

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Remova a configuração de implantação para `checkout` e `sales` nas seções `connections` e `resources` do arquivo `env.php`.
1. Restaurar chaves estrangeiras:

   ```shell
   bin/magento setup:upgrade
   ```

## Verificar seu trabalho

Para verificar se a implementação de seu único banco de dados está funcionando corretamente, execute as tarefas a seguir e verifique se os dados foram adicionados às tabelas de banco de dados do `magento_main` usando uma ferramenta de banco de dados como o [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Verifique se chaves estrangeiras foram restauradas. Por exemplo, a chave `QUOTE_STORE_ID_STORE_STORE_ID` na tabela de banco de dados `quote`.
1. Verifique se os clientes podem fazer pedidos da loja.
1. Verifique se os pedidos criados antes de reverter o banco de dados dividido para um único banco de dados estão disponíveis no Administrador.
