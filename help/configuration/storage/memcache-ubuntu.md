---
title: Configurar memória em cache no Ubuntu
description: Instale e configure o cache em cache no Ubuntu.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# Configurar memória em cache no Ubuntu

Esta seção fornece instruções para instalar memorizado no Ubuntu.

>[!INFO]
>
>O Adobe recomenda usar a versão em cache 3.0.5 ou posterior.

Como o PHP não tem suporte nativo para memcache, você deve instalar uma extensão para o PHP usá-la. Há duas extensões PHP disponíveis e é importante decodificar quais usar:

- `memcache` (_sem d_) — uma extensão mais antiga, mas popular, que não é mantida regularmente.
O `memcache` extensão atualmente _não_ trabalhar com PHP 7. Consulte [Documentação PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

   O nome exato é `php5-memcache` para Ubuntu.

- `memcached` (_com um`d`_) — uma extensão mais recente e mantida compatível com o PHP 7. Consulte [Documentação PHP para memcache](https://www.php.net/manual/en/book.memcached.php).

   O nome exato é `php5-memcached` para Ubuntu.

## Instalar e configurar em cache no Ubuntu

**Para instalar e configurar o cache armazenado em cache no Ubuntu**:

1. Como um usuário com `root` , insira o seguinte comando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Altere a configuração em cache para `CACHESIZE` e `-l`:

   1. Abrir `/etc/memcached.conf` em um editor de texto.
   1. Localize a variável `-m` parâmetro.
   1. Alterar seu valor para pelo menos `1GB`
   1. Localize a variável `-l` parâmetro.
   1. Alterar seu valor para `127.0.0.1` ou `localhost`
   1. Salve as alterações em `memcached.conf` e saia do editor de texto.
   1. Reinicie em cache.

      ```bash
      service memcached restart
      ```

1. Reinicie o servidor da Web.

   Para o Apache, `service apache2 restart`

1. Continue com a próxima seção.

## Verifique se o cache funciona antes de instalar o Magento

O Adobe recomenda testar memached para garantir que funcione antes de instalar o Commerce. Isso leva apenas alguns minutos e pode simplificar a solução de problemas posteriormente.

### Verificar se o cache em cache é reconhecido pelo servidor da Web

Para verificar se o cache foi reconhecido pelo servidor da Web:

1. Crie um `phpinfo.php` no docroot do servidor web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vá para essa página no navegador da Web. Por exemplo:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Certifique-se de que o cache em cache seja exibido da seguinte maneira:

   ![Confirmar se o cache em cache é reconhecido pelo servidor da Web](../../assets/configuration/memcache.png)

   Verifique se você está usando a versão em cache 3.0.5 ou posterior.

   Se o cache não for exibido, reinicie o servidor da Web e atualize a página do navegador. Se ainda não for exibido, verifique se você instalou a variável `php-pecl-memcached` extensão.

### Verifique se os dados em cache podem armazenar em cache

Este teste usa um script PHP para verificar se o cache é capaz de armazenar e recuperar dados de cache.

Para obter mais informações sobre esse teste, consulte [Tutorial Como instalar e usar o Memcache no Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Criar `cache-test.php` no docroot do servidor da web com o seguinte conteúdo:

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

Onde `<memcached hostname or ip>` é `localhost`, `127.0.0.1`ou o nome do host ou endereço IP do memcache. O `<memcached port>` é a porta de escuta; por padrão, `11211`.

Vá para essa página em um navegador da Web. Por exemplo

```http
http://192.0.2.1/cache-test.php
```

Na primeira vez que você for para a página, o seguinte será exibido: `No matching key found. Refresh the browser to add it!`

Atualize o navegador. A mensagem muda para `Successfully retrieved the data!`

Por fim, você pode exibir as chaves do cache de memória usando Telnet:

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

Liberar armazenamento em cache memantado e sair do Telnet:

```shell
flush_all
```

```shell
quit
```

[Informações adicionais sobre o teste Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
