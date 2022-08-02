---
title: Local de armazenamento da sessão
description: Saiba onde os arquivos de sessão estão armazenados.
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Local de armazenamento da sessão

Este tópico discute como localizar onde os arquivos de sessão estão armazenados. O sistema usa a seguinte lógica para armazenar arquivos de sessão:

- Se você configurou em cache, as sessões são armazenadas na RAM; see [Usar memcache para armazenamento de sessão](memcached.md).
- Se você configurou o Redis, as sessões são armazenadas no servidor Redis; see [Use Redis para armazenamento de sessão](../cache/redis-session.md).
- Se você estiver usando o armazenamento padrão baseado em arquivo, armazenamos sessões nos seguintes locais na ordem mostrada:

   1. Diretório definido em [`env.php`](#example-in-envphp)
   1. Diretório definido em [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` diretory

## Exemplo em `env.php`

Um trecho de amostra de `<magento_root>/app/etc/env.php` a seguir:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

O exemplo anterior armazena arquivos de sessão em `/var/www/session`

## Exemplo em `php.ini`

Como um usuário com `root` privilégios, abra `php.ini` e pesquise o valor de `session.save_path`. Isso identifica onde as sessões são armazenadas.

## Gerenciar tamanho da sessão

Consulte a [Gerenciamento de sessão](https://docs.magento.com/user-guide/stores/security-session-management.html) no _Guia do usuário_.

## Configuração da coleta de lixo

Para limpar sessões expiradas, o sistema chama a função `gc` (_coleta de lixo_) manipulador aleatoriamente de acordo com uma probabilidade calculada pela variável `gc_probability / gc_divisor` diretiva. Por exemplo, se você definir essas diretivas como `1/100` significa, respectivamente, uma probabilidade de `1%` (_probabilidade de uma chamada de coleta de lixo por 100 solicitações_).

O manipulador de coleta de lixo usa a variável `gc_maxlifetime` diretiva — o número de segundos após os quais as sessões são vistas como _lixo_ e potencialmente limpas.

Em alguns sistemas operacionais (Debian/Ubuntu), o padrão `session.gc_probability` diretiva `0`, que impede a execução do manipulador de coleta de lixo.

É possível substituir a variável `session.gc_` diretivas da `php.ini` no `<magento_root>/app/etc/env.php` arquivo:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

A configuração varia, dependendo do tráfego e das necessidades específicas do site do comerciante.
