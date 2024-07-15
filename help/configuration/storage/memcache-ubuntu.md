---
title: Configurar o memcached no Ubuntu
description: Instalar e configurar o memcached no Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Configurar o memcached no Ubuntu

Esta seção fornece instruções para instalar o memcached no Ubuntu.

>[!INFO]
>
>O Adobe recomenda o uso da versão memcached 3.0.5 ou posterior.

Como o PHP não tem suporte nativo para memcache, você deve instalar uma extensão para o PHP usá-lo. Há duas extensões PHP disponíveis e é importante decodificar quais usar:

- `memcache` (_no d_) — uma extensão mais antiga, mas popular, que não é mantida regularmente.
A extensão `memcache` atualmente _não_ funciona com o PHP 7. Consulte a documentação do [PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

  O nome exato é `php5-memcache` para Ubuntu.

- `memcached` (_com`d`_)—uma extensão mais recente e mantida que é compatível com o PHP 7. Consulte a documentação do [PHP para memcached](https://www.php.net/manual/en/book.memcached.php).

  O nome exato é `php5-memcached` para Ubuntu.

## Instalar e configurar o memcached no Ubuntu

**Para instalar e configurar o memcached no Ubuntu**:

1. Como um usuário com privilégios `root`, digite o seguinte comando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Alterar a definição da configuração memcached para `CACHESIZE` e `-l`:

   1. Abra `/etc/memcached.conf` em um editor de texto.
   1. Localize o parâmetro `-m`.
   1. Alterar seu valor para pelo menos `1GB`
   1. Localize o parâmetro `-l`.
   1. Alterar seu valor para `127.0.0.1` ou `localhost`
   1. Salve as alterações em `memcached.conf` e saia do editor de texto.
   1. Reiniciar memcached.

      ```bash
      service memcached restart
      ```

1. Reinicie o servidor Web.

   Para o Apache, `service apache2 restart`

1. Prossiga para a próxima seção.

## Verificar trabalhos memcached antes de instalar o Magento

A Adobe recomenda testar o memcached para verificar se ele funciona antes de instalar o Commerce. Isso leva apenas alguns minutos e pode simplificar a solução de problemas posteriormente.

### Verificar se o memcached é reconhecido pelo servidor Web

Para verificar se o memcached é reconhecido pelo servidor Web:

1. Crie um arquivo `phpinfo.php` no docroot do servidor Web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vá para essa página em seu navegador da Web. Por exemplo:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Verifique se as exibições memcached estão sendo exibidas da seguinte maneira:

   ![Confirmar que o memcached é reconhecido pelo servidor Web](../../assets/configuration/memcache.png)

   Verifique se você está usando a versão memcached 3.0.5 ou posterior.

   Se o memcached não for exibido, reinicie o servidor Web e atualize a página do navegador. Se ainda assim não for exibido, verifique se você instalou a extensão `php-pecl-memcached`.

### Verificar se o armazenamento em cache memcached pode armazenar dados em cache

Este teste usa um script PHP para verificar se o memcached pode armazenar e recuperar dados do cache.

Para obter mais informações sobre este teste, consulte o [tutorial Como instalar e usar o Memcache no Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Crie `cache-test.php` no docroot do servidor Web com o seguinte conteúdo:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Onde `<memcached hostname or ip>` é `localhost`, `127.0.0.1`, ou o nome de host ou endereço IP do memcache. O `<memcached port>` é a porta de escuta; por padrão, `11211`.

Vá para essa página em um navegador da Web. Por exemplo

```http
http://192.0.2.1/cache-test.php
```

Na primeira vez que você for à página, será exibido o seguinte: `No matching key found. Refresh the browser to add it!`

Atualize o navegador. A mensagem foi alterada para `Successfully retrieved the data!`

Finalmente, você pode visualizar as chaves de memcache usando Telnet:

```bash
telnet localhost <memcache port>
```

No prompt, digite

```shell
stats items
```

O resultado é semelhante ao seguinte:

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Liberar armazenamento em cache memorizado e sair do Telnet:

```shell
flush_all
```

```shell
quit
```

[Informações adicionais sobre o teste Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
