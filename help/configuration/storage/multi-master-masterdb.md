---
title: Configurar automaticamente os bancos de dados mestres
description: Consulte orientações sobre como configurar automaticamente a solução de banco de dados dividido.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Configurar automaticamente os bancos de dados mestres

{{ee-only}}

{{deprecate-split-db}}

Este tópico discute como começar a usar a solução de banco de dados dividido ao:

1. Instalando o Adobe Commerce com um único banco de dados mestre (denominado `magento`)
1. Criando dois bancos de dados mestres adicionais para check-out e OMS (nomeados como `magento_quote` e `magento_sales`)
1. Configuração do Adobe Commerce para usar os bancos de dados de check-out e vendas

>[!INFO]
>
>Este guia pressupõe que todos os três bancos de dados estejam no mesmo host que o aplicativo Commerce e que sejam nomeados como `magento`, `magento_quote` e `magento_sales`. No entanto, a escolha de onde localizar os bancos de dados e seu nome depende de você. Esperamos que nossos exemplos tornem as instruções mais fáceis de seguir.

## Instale o software da Adobe Commerce

Você pode ativar bancos de dados divididos a qualquer momento depois de instalar o software Adobe Commerce; em outras palavras, você pode adicionar bancos de dados divididos a um sistema Adobe Commerce que já tenha dados de check-out e pedido. Use as instruções no Adobe Commerce README ou no [guia de instalação](../../installation/overview.md) para instalar o software Adobe Commerce usando um único banco de dados mestre.

## Configurar bancos de dados mestres adicionais

Crie o checkout e os bancos de dados mestres OMS da seguinte maneira:

1. Faça logon no servidor de banco de dados como qualquer usuário.
1. Digite o seguinte comando para obter um prompt de comando do MySQL:

   ```bash
   mysql -u root -p
   ```

1. Digite a senha do usuário `root` do MySQL quando solicitado.
1. Digite os seguintes comandos na ordem mostrada para criar instâncias de banco de dados chamadas `magento_quote` e `magento_sales` com os mesmos nomes de usuário e senhas:

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

1. Digite `exit` para sair do prompt de comando.

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

## Configurar o Commerce para usar os bancos de dados mestres

Após configurar um total de três bancos de dados mestres, use a linha de comando para configurar o Commerce para usá-los. (O comando configura conexões de banco de dados e distribui tabelas entre os bancos de dados mestres.)

### Primeiros passos

Consulte [Executando comandos](../cli/config-cli.md#running-commands) para fazer logon e executar comandos CLI.

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
