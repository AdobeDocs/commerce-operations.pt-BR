---
title: Configurar em cache no CentOS
description: Instale e configure em cache o CentOS.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Configurar em cache no CentOS

Esta seção fornece instruções para instalar o cache no CentOS. Para obter mais informações, consulte o [wiki memcached](https://github.com/memcached/old-wiki).

>[!INFO]
>
>A Adobe recomenda usar a versão em cache estável mais recente (atualmente, 3.1.3 para memcache).

Como o PHP não tem suporte nativo para memcache, você deve instalar uma extensão para o PHP usá-la. Há duas extensões PHP disponíveis e é importante decodificar quais usar:

- `memcache` (_sem d_) — uma extensão mais antiga, mas popular, que não é mantida regularmente.
O `memcache` extensão atualmente _não_ trabalhar com PHP 7. Consulte [Documentação PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

   O nome exato é `php-pecl-memcache` para CentOS.

- `memcached` (_com um`d`_) — uma extensão mais recente e mantida compatível com o PHP 7. Consulte [Documentação PHP para memcache](https://www.php.net/manual/en/book.memcached.php).

   O nome exato é `php-pecl-memcached` para CentOS.

## Instalar e configurar em cache no CentOS

Para instalar memcache no CentOS, execute as seguintes tarefas como usuário com `root` privilégios:

1. Instale em cache e suas dependências:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >A sintaxe dos comandos anteriores pode depender dos repositórios de pacotes usados. Por exemplo, se você usar webtatic e PHP 5.6, insira `yum install -y php56w-pecl-memcache`. Use `yum search memcache|grep php` para localizar o nome de pacote apropriado.


1. Altere a configuração em cache para `CACHESIZE` e `OPTIONS`:

   1. Abrir `/etc/sysconfig/memcached` em um editor de texto.
   1. Localize o valor para `CACHESIZE` e alterá-la para pelo menos 1 GB. Por exemplo:

      ```config
      CACHESIZE="1GB"
      ```

   1. Localize o valor para `OPTIONS` e altere para `localhost` ou `127.0.0.1`

1. Salve as alterações em `memcached` e saia do editor de texto.
1. Reinicie em cache.

   ```bash
   service memcached restart
   ```

1. Reinicie o servidor da Web.

   Para o Apache:

   ```bash
   service httpd restart
   ```

1. Continue com a próxima seção.

## Verificar se funciona em cache antes de instalar o Commerce

O Adobe recomenda testar memached para garantir que funcione antes de instalar o Commerce. Isso leva apenas alguns minutos e pode simplificar a solução de problemas posteriormente.

### Verificar se o cache em cache é reconhecido pelo servidor da Web

Para verificar se o cache em cache é reconhecido pelo servidor da Web:

1. Crie um `phpinfo.php` no docroot do servidor web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vá para essa página no navegador da Web.

   Por exemplo, `http://192.0.2.1/phpinfo.php`

1. Certifique-se de que o memcache seja exibido da seguinte maneira:

![Confirmar se o cache de memória é reconhecido pelo servidor da Web](../../assets/configuration/memcache.png)

Verifique se você está usando a versão em cache 3.0.5 ou posterior.

Se o cache de memória não for exibido, reinicie o servidor da Web e atualize a página do navegador. Se ainda não for exibido, verifique se você instalou a variável `php-pecl-memcache` extensão.

### Criar um teste de cache de memória que consiste em um banco de dados MySQL e um script PHP

O teste usa um banco de dados, tabela e dados do MySQL para verificar se você pode recuperar os dados do banco de dados e armazená-los no cache de memória. Um script PHP primeiro pesquisa o cache. Se o resultado não existir, o script consulta o banco de dados. Depois que o query for preenchido pelo banco de dados original, o script armazenará o resultado em memcache usando o `set` comando.

[Mais detalhes sobre este teste](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Criar o banco de dados MySQL:

```bash
mysql -u root -p
```

Na `mysql` , insira os seguintes comandos:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Criar `cache-test.php` no docroot do seu servidor da Web:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Onde `<memcached hostname or ip>` é `localhost`, `127.0.0.1`ou o nome do host ou endereço IP do memcache. O `<memcached port>` é a porta de escuta; por padrão, `11211`.

Execute o script a partir da linha de comando.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

O primeiro resultado é `got result from mysql`. Isso significa que a chave não existia em cache, mas foi recuperada do MySQL.

O segundo resultado é `got result from memcached`, que verifica se o valor é armazenado com êxito em cache.

Por fim, você pode exibir as chaves do cache de memória usando Telnet:

```bash
telnet localhost <memcache port>
```

No prompt, digite

```bash
stats items
```

O resultado é semelhante ao seguinte:

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Limpe o armazenamento do memcache e saia do Telnet:

```bash
flush_all
```

```bash
quit
```

[Informações adicionais sobre o teste Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
