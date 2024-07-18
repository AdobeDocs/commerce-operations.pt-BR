---
title: Configurar uma conexão remota com o banco de dados MySQL
description: Siga estas etapas para configurar uma conexão de banco de dados remota para instalações locais do Adobe Commerce.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Configurar uma conexão remota com o banco de dados MySQL

Às vezes, talvez você queira hospedar o banco de dados em um servidor separado em vez de executar o servidor de banco de dados e o servidor da Web na mesma máquina.

O Adobe forneceu uma maneira de se conectar a um servidor MySQL em uma máquina diferente. A partir do Adobe Commerce 2.4.3, você também pode configurar o aplicativo para usar um banco de dados Amazon Web Services (AWS) Aurora sem alterações no código.

O Aurora é um servidor MySQL de alto desempenho, totalmente compatível, hospedado na AWS.

## Conexão com um banco de dados AWS Aurora

Usar o Aurora como banco de dados é tão fácil quanto especificar o banco de dados na configuração normal do Adobe Commerce, usando o conector de banco de dados padrão.

Ao executar o `bin/magento setup:install`, use as informações do Aurora nos campos `db-`:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

O valor `db-host` é a URL Aurora com `https://` e `:portnumber` à direita removidos.

## Configuração de uma conexão de banco de dados remota

>[!NOTE]
>
>Este é um tópico avançado que deve ser usado somente por um administrador de rede ou administrador de banco de dados experiente. Você deve ter acesso de `root` ao sistema de arquivos e deve ser capaz de fazer login no MySQL como `root`.

### Pré-requisitos

Antes de começar, você deve:

* [Instalar MySQL server](mysql.md) no servidor de banco de dados.
* [Crie uma instância de banco de dados](mysql.md#configuring-the-database-instance) no servidor de banco de dados.
* Instale o cliente MySQL no nó da Web do Adobe Commerce. Consulte a documentação do MySQL para obter detalhes.

### Alta disponibilidade

Use as diretrizes a seguir para configurar conexões de banco de dados remoto se o servidor Web ou o servidor de banco de dados estiver clusterizado:

* Você deve configurar uma conexão para cada nó do servidor Web.
* Normalmente, você configura uma conexão de banco de dados para o balanceador de carga de banco de dados; no entanto, o clustering de banco de dados pode ser complexo e a configuração depende de você. O Adobe não faz recomendações específicas para clustering de banco de dados.

  Para obter mais informações, consulte a [documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Resolução de problemas de conexão

Se você tiver problemas ao se conectar a um dos hosts, primeiro execute ping no outro host para verificar se ele pode ser acessado. Talvez seja necessário permitir conexões de um host para outro modificando as regras de firewall e SELinux (se você usar SELinux).

## Criar a conexão remota

Para criar uma conexão remota:

1. No servidor de banco de dados, como um usuário com privilégios `root`, abra o arquivo de configuração MySQL.

   Para localizá-lo, digite o seguinte comando:

   ```bash
   mysql --help
   ```

   O local é exibido de forma semelhante ao seguinte:

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >No Ubuntu 16, o caminho normalmente é `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Pesquisar o arquivo de configuração para `bind-address`.

   Se existir, altere o valor da seguinte maneira.

   Se ele não existir, adicione-o à seção `[mysqld]`.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Consulte a [documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), especialmente se você tiver um servidor Web clusterizado.

1. Salve as alterações no arquivo de configuração e saia do editor de texto.
1. Reinicie o serviço MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >Se o MySQL não for iniciado, procure no syslog a origem do problema. Resolva o problema usando a [documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) ou outra fonte autoritativa.

## Conceder acesso a um usuário do banco de dados

Para permitir que o nó da Web se conecte ao servidor de banco de dados, você deve conceder a um usuário de banco de dados do nó da Web acesso ao banco de dados no servidor remoto.

Este exemplo concede ao usuário do banco de dados `root` acesso total ao banco de dados no host remoto.

Para conceder acesso a um usuário do banco de dados:

1. Efetue log-in no servidor de banco de dados.
1. Conectar ao banco de dados MySQL como o usuário `root`.
1. Digite o seguinte comando:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Por exemplo,

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Se o servidor Web estiver clusterizado, insira o mesmo comando em cada servidor Web. Você deve usar o mesmo nome de usuário para cada servidor Web.

## Verificar acesso ao banco de dados

No host do nó da Web, digite o seguinte comando para verificar se a conexão funciona:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Se o monitor MySQL for exibido da seguinte maneira, o banco de dados estará pronto para o Adobe Commerce:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Se o servidor Web estiver clusterizado, insira o comando em cada host do servidor Web.

## Instalar o Adobe Commerce

Ao instalar o Adobe Commerce, você deve especificar o seguinte:

* A URL de base (também chamada de *endereço de repositório*) especifica o nome de host ou endereço IP do *nó da Web*
* O host do banco de dados é o endereço IP do *servidor de banco de dados remoto* (ou balanceador de carga se o servidor de banco de dados estiver clusterizado)
* O nome de usuário do banco de dados é o *nó da Web local* usuário do banco de dados ao qual você deu acesso
* A senha do banco de dados é a senha do usuário do nó da Web local
* Nome do banco de dados é o nome do banco de dados no servidor remoto
