---
title: Configurar uma conexão remota de banco de dados do MySQL
description: Siga estas etapas para configurar uma conexão de banco de dados remoto para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurar uma conexão remota de banco de dados do MySQL

Às vezes, é possível hospedar o banco de dados em um servidor separado, em vez de executar o servidor de banco de dados e o servidor da Web na mesma máquina.

O Adobe forneceu uma maneira de se conectar a um servidor MySQL em uma máquina diferente. A partir do Adobe Commerce e do Magento Open Source 2.4.3, você também pode configurar o aplicativo para usar um banco de dados Amazon Web Services (AWS) Aurora sem alterações de código.

O Aurora é um servidor MySQL de alto desempenho e totalmente compatível hospedado na AWS.

## Conexão com um banco de dados AWS Aurora

Usar o Aurora como banco de dados é tão fácil quanto especificar o banco de dados na configuração regular do Adobe Commerce e do Magento Open Source, usando o conector de banco de dados padrão.

Ao executar `bin/magento setup:install`use as informações do Aurora no `db-` campos:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

O `db-host` é o URL do Aurora com o valor `https://` e à direita `:portnumber`  removido.

## Configurando uma conexão de banco de dados remoto

>[!NOTE]
>
>Este é um tópico avançado que deve ser usado somente por um administrador de rede ou administrador de banco de dados experiente. Você deve ter `root` acesso ao sistema de arquivos e você deve poder fazer logon no MySQL como `root`.

### Pré-requisitos

Antes de começar, você deve:

* [Instalar o servidor MySQL](mysql.md) no servidor de banco de dados.
* [Criar uma instância de banco de dados](mysql.md#configuring-the-database-instance) no servidor de banco de dados.
* Instale o cliente MySQL no nó da Web Adobe Commerce ou Magento Open Source. Consulte a documentação do MySQL para obter detalhes.

### Alta disponibilidade

Use as diretrizes a seguir para configurar conexões de banco de dados remoto se o servidor da Web ou o servidor de banco de dados estiver em cluster:

* Você deve configurar uma conexão para cada nó do servidor da Web.
* Normalmente, você configura uma conexão de banco de dados com o balanceador de carga do banco de dados; no entanto, o clustering do banco de dados pode ser complexo e a configuração depende de você. O Adobe não faz recomendações específicas para o clustering do banco de dados.

   Para obter mais informações, consulte [Documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Resolvendo problemas de conexão

Se tiver problemas para se conectar a um dos hosts, primeiro faça o ping no outro host para garantir que ele esteja acessível. Talvez seja necessário permitir conexões de um host para outro modificando o firewall e as regras do SELinux (se você usar o SELinux).

## Criar a conexão remota

Para criar uma conexão remota:

1. No servidor de banco de dados, como um usuário com `root` , abra o arquivo de configuração do MySQL.

   Para localizá-lo, insira o seguinte comando:

   ```bash
   mysql --help
   ```

   O local é exibido de maneira semelhante ao seguinte:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >No Ubuntu 16, o caminho normalmente é `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Pesquise no arquivo de configuração por `bind-address`.

   Se existir, altere o valor da seguinte maneira.

   Se ele não existir, adicione-o ao `[mysqld]` seção.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Consulte [Documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), especialmente se você tiver um servidor da Web em cluster.

1. Salve as alterações no arquivo de configuração e saia do editor de texto.
1. Reinicie o serviço MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Se o MySQL não for iniciado, procure a origem do problema no syslog. Resolva o problema usando [Documentação do MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) ou outra fonte de autorização.

## Conceder acesso a um usuário do banco de dados

Para permitir que o nó da Web se conecte ao servidor de banco de dados, é necessário conceder a um usuário do banco de dados de nós da Web acesso ao banco de dados no servidor remoto.

Esse exemplo concede o `root` usuário do banco de dados com acesso total ao banco de dados no host remoto.

Para conceder acesso a um usuário do banco de dados:

1. Faça logon no servidor de banco de dados.
1. Conecte-se ao banco de dados MySQL como o `root` usuário.
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
   >Se o servidor Web estiver em cluster, insira o mesmo comando em cada servidor Web. Você deve usar o mesmo nome de usuário para cada servidor da Web.

## Verificar o acesso ao banco de dados

No host do nó da Web, insira o seguinte comando para verificar se a conexão funciona:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Se o monitor MySQL for exibido da seguinte maneira, o banco de dados estará pronto para Adobe Commerce ou Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Se o servidor da Web estiver em cluster, insira o comando em cada host do servidor da Web.

## Instale o Adobe Commerce ou o Magento Open Source

Ao instalar o Adobe Commerce ou o Magento Open Source, você deve especificar o seguinte:

* A base [URL](https://glossary.magento.com/url) (também conhecido como *endereço da loja*) especifica o nome do host ou endereço IP do *nó da web*
* O host do banco de dados é o *servidor de banco de dados remoto* Endereço IP (ou balanceador de carga se o servidor de banco de dados estiver em cluster)
* O nome de usuário do banco de dados é *nó da Web local* usuário do banco de dados ao qual você deu acesso
* A senha do banco de dados é a senha do usuário do nó da Web local
* Nome do banco de dados é o nome do banco de dados no servidor remoto
