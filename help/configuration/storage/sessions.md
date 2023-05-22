---
title: Local de armazenamento da sessão
description: Saiba onde os arquivos de sessão são armazenados.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Local de armazenamento da sessão

Este tópico discute como localizar onde seus arquivos de sessão estão armazenados. O sistema usa a seguinte lógica para armazenar arquivos de sessão:

- Se você configurou o memcached, as sessões são armazenadas na RAM; consulte [Usar memcached para armazenamento de sessão](memcached.md).
- Se você configurou o Redis, as sessões são armazenadas no servidor Redis; consulte [Usar Redis para armazenamento de sessão](../cache/redis-session.md).
- Se você estiver usando o armazenamento de sessão baseado em arquivo padrão, armazenaremos as sessões nos seguintes locais na ordem mostrada:

   1. Diretório definido em [`env.php`](#example-in-envphp)
   1. Diretório definido em [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` diretório

## Exemplo em `env.php`

Um trecho de exemplo de `<magento_root>/app/etc/env.php` seguinte forma:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

O exemplo anterior armazena arquivos de sessão em `/var/www/session`

## Exemplo em `php.ini`

Como usuário com `root` privilégios, abra o `php.ini` arquivo e pesquise pelo valor de `session.save_path`. Isso identifica onde as sessões são armazenadas.

## Gerenciar tamanho da sessão

Consulte a [Gerenciamento de sessão](https://docs.magento.com/user-guide/stores/security-session-management.html) no _Guia do usuário_.

## Configuração da coleta de lixo

Para limpar sessões expiradas, o sistema chama o `gc` (_coleta de lixo_) aleatoriamente de acordo com uma probabilidade calculada pelo `gc_probability / gc_divisor` diretiva. Por exemplo, se você definir essas diretivas como `1/100` respectivamente, significa uma probabilidade `1%` (_probabilidade de uma chamada de coleta de lixo por 100 solicitações_).

O manipulador da coleta de lixo usa o `gc_maxlifetime` diretiva — o número de segundos após o qual as sessões são vistas como _lixo_ e potencialmente limpo.

Em alguns sistemas operacionais (Debian/Ubuntu), o padrão `session.gc_probability` diretiva é `0`, que impede a execução do manipulador de coleta de lixo.

É possível substituir a variável `session.gc_` diretivas do `php.ini` arquivo no `<magento_root>/app/etc/env.php` arquivo:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

A configuração varia, dependendo do tráfego e das necessidades específicas do site do comerciante.
