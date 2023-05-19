---
title: Configurar automaticamente bancos de dados principais
description: Consulte orientações sobre como configurar automaticamente a solução de banco de dados dividido.
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Configurar automaticamente bancos de dados principais

{{ee-only}}

{{deprecate-split-db}}

Este tópico discute como começar a usar a solução de banco de dados dividido ao:

1. Instalação do Adobe Commerce com um único banco de dados principal (chamado de `magento`)
1. Criação de dois bancos de dados principais adicionais para checkout e OMS (nomeados como `magento_quote` e `magento_sales`)
1. Configuração do Adobe Commerce para usar os bancos de dados de check-out e vendas

>[!INFO]
>
>Este guia pressupõe que todos os três bancos de dados estão no mesmo host que o aplicativo Commerce e que eles sejam nomeados `magento`, `magento_quote`, e `magento_sales`. No entanto, a escolha de onde localizar os bancos de dados e seu nome depende de você. Esperamos que nossos exemplos tornem as instruções mais fáceis de seguir.

## Instale o software da Adobe Commerce

Você pode ativar bancos de dados divididos a qualquer momento depois de instalar o software Adobe Commerce; em outras palavras, você pode adicionar bancos de dados divididos a um sistema Adobe Commerce que já tenha dados de check-out e pedido. Use as instruções no arquivo LEIAME do Adobe Commerce ou no [guia de instalação](../../installation/overview.md) para instalar o software Adobe Commerce usando um único banco de dados principal.

## Configurar bancos de dados principais adicionais

Crie o check-out e os bancos de dados principais OMS da seguinte maneira:

1. Faça logon no servidor de banco de dados como qualquer usuário.
1. Digite o seguinte comando para obter um prompt de comando do MySQL:

   ```bash
   mysql -u root -p
   ```

1. Insira o MySQL `root` senha do usuário quando solicitado.
1. Insira os seguintes comandos na ordem mostrada para criar instâncias de banco de dados chamadas `magento_quote` e `magento_sales` com os mesmos nomes de usuário e senhas:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` para sair do prompt de comando.

1. Verifique os bancos de dados, um de cada vez:

   Fazer check-out do banco de dados:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Banco de dados do sistema de gerenciamento de pedidos:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Se o monitor MySQL for exibido, você criou o banco de dados corretamente. Se um erro for exibido, repita os comandos anteriores.

## Configurar o Commerce para usar os bancos de dados principais

Depois de configurar um total de três bancos de dados principais, use a linha de comando para configurar o Commerce para usá-los. (O comando configura conexões de banco de dados e distribui tabelas entre os bancos de dados principais.)

### Primeiros passos

Consulte [Execução de comandos](../cli/config-cli.md#running-commands) para fazer login e executar comandos da CLI.

### Configurar o banco de dados de check-out

Sintaxe de comando:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por exemplo,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

A seguinte mensagem é exibida para confirmar uma configuração bem-sucedida:

```terminal
Migration has been finished successfully!
```

### Configurar o banco de dados OMS

Sintaxe de comando:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por exemplo,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

A seguinte mensagem é exibida para confirmar uma configuração bem-sucedida:

```terminal
Migration has been finished successfully!
```
