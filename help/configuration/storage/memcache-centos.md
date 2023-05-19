---
title: Configurar memória em cache no CentOS
description: Instalar e configurar o memcached no CentOS.
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Configurar memória em cache no CentOS

Esta seção fornece instruções para instalar o memcached no CentOS. Para obter informações adicionais, consulte o [wiki memcached](https://github.com/memcached/old-wiki).

>[!INFO]
>
>o Adobe recomenda usar a versão estável mais recente memcached (atualmente 3.1.3 para memcached).

Como o PHP não tem suporte nativo para memcache, você deve instalar uma extensão para o PHP usá-lo. Há duas extensões PHP disponíveis e é importante decodificar quais usar:

- `memcache` (_não d_) — uma extensão mais antiga, mas popular, que não é mantida regularmente.
A variável `memcache` extensão atual _não_ trabalhar com o PHP 7. Consulte [Documentação do PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

   O nome exato é `php-pecl-memcache` para CentOS.

- `memcached` (_com um`d`_)—uma extensão nova e mantida que é compatível com o PHP 7. Consulte [Documentação do PHP para memcached](https://www.php.net/manual/en/book.memcached.php).

   O nome exato é `php-pecl-memcached` para CentOS.

## Instalar e configurar o memcached no CentOS

Para instalar o memcached no CentOS, execute as seguintes tarefas como um usuário com `root` privilégios:

1. Instalar o memcached e suas dependências:

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
   >A sintaxe dos comandos anteriores pode depender de quais repositórios de packages você usa. Por exemplo, se você usa webatic e PHP 5.6, digite `yum install -y php56w-pecl-memcache`. Uso `yum search memcache|grep php` para localizar o nome do pacote apropriado.


1. Alterar a definição da configuração memcached para `CACHESIZE` e `OPTIONS`:

   1. Abertura `/etc/sysconfig/memcached` em um editor de texto.
   1. Localize o valor de `CACHESIZE` e altere para pelo menos 1 GB. Por exemplo:

      ```config
      CACHESIZE="1GB"
      ```

   1. Localize o valor de `OPTIONS` e altere para `localhost` ou `127.0.0.1`

1. Salvar as alterações em `memcached` e saia do editor de texto.
1. Reiniciar memcached.

   ```bash
   service memcached restart
   ```

1. Reinicie o servidor Web.

   Para o Apache:

   ```bash
   service httpd restart
   ```

1. Prossiga para a próxima seção.

## Verificar trabalhos memcached antes de instalar o Commerce

A Adobe recomenda testar o memcached para garantir que funcione, antes de instalar o Commerce. Isso leva apenas alguns minutos e pode simplificar a solução de problemas posteriormente.

### Verificar se o memcached é reconhecido pelo servidor Web

Para verificar se o memcached é reconhecido pelo servidor Web:

1. Criar um `phpinfo.php` arquivo no docroot do servidor Web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vá para essa página em seu navegador da Web.

   Por exemplo, `http://192.0.2.1/phpinfo.php`

1. Verifique se o memcache é exibido da seguinte maneira:

![Confirmar o memcache é reconhecido pelo servidor Web](../../assets/configuration/memcache.png)

Verifique se você está usando a versão memcached 3.0.5 ou posterior.

Se o memcache não for exibido, reinicie o servidor Web e atualize a página do navegador. Se ainda não for exibido, verifique se você instalou o `php-pecl-memcache` extensão.

### Criar um teste de memcache consistindo em um banco de dados MySQL e um script PHP

O teste usa um banco de dados, tabela e dados MySQL para verificar se você pode recuperar os dados do banco de dados e armazená-los no memcache. Um script PHP primeiro pesquisa no cache. Se o resultado não existir, o script consultará o banco de dados. Depois que a consulta for atendida pelo banco de dados original, o script armazenará o resultado no memcache, usando o `set` comando.

[Mais detalhes sobre este teste](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Crie o banco de dados MySQL:

```bash
mysql -u root -p
```

No `mysql` digite os seguintes comandos:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Criar `cache-test.php` no docroot do servidor Web:

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

Onde `<memcached hostname or ip>` é `localhost`, `127.0.0.1`, ou o nome de host ou endereço IP do memcache. A variável `<memcached port>` é a porta de escuta; por padrão, `11211`.

Execute o script a partir da linha de comando.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

O primeiro resultado `got result from mysql`. Isso significa que a chave não existia no memcached, mas foi recuperada do MySQL.

O segundo resultado `got result from memcached`, que verifica se o valor foi armazenado com êxito no memcached.

Finalmente, você pode visualizar as chaves de memcache usando Telnet:

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

Liberar o armazenamento memcache e sair do Telnet:

```bash
flush_all
```

```bash
quit
```

[Informações adicionais sobre o teste Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
