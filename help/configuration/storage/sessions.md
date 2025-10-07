---
title: Local de armazenamento da sessão
description: Saiba mais sobre locais de armazenamento de sessão e gerenciamento de arquivos no Adobe Commerce. Descubra a lógica de armazenamento e as opções de configuração.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Local de armazenamento da sessão

Este tópico discute como localizar onde seus arquivos de sessão estão armazenados. O sistema usa a seguinte lógica para armazenar arquivos de sessão:

- Se você configurou o memcached, as sessões são armazenadas na RAM; consulte [Usar memcached para armazenamento de sessão](memcached.md).
- Se você configurou o Redis, as sessões são armazenadas no servidor Redis; consulte [Usar Redis para armazenamento de sessão](../cache/redis-session.md).
- Se você estiver usando o armazenamento de sessão baseado em arquivo padrão, armazenaremos as sessões nos seguintes locais na ordem mostrada:

   1. Diretório definido em [`env.php`](#example-in-envphp)
   1. Diretório definido em [`php.ini`](#example-in-phpini)
   1. Diretório `<magento_root>/var/session`

## Exemplo em `env.php`

Este é um trecho de exemplo de `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

O exemplo anterior armazena arquivos de sessão em `/var/www/session`

## Exemplo em `php.ini`

Como um usuário com privilégios `root`, abra seu arquivo `php.ini` e procure o valor de `session.save_path`. Isso identifica onde as sessões são armazenadas.

## Gerenciar tamanho da sessão

Consulte o [Gerenciamento de sessão](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/security-session-management) no _Guia do usuário_.

## Configuração da coleta de lixo

Para limpar sessões expiradas, o sistema chama o manipulador `gc` (_coleta de lixo_) aleatoriamente de acordo com uma probabilidade calculada pela diretiva `gc_probability / gc_divisor`. Por exemplo, se você definir essas diretivas como `1/100` respectivamente, isso significa uma probabilidade de `1%` (_probabilidade de uma chamada de coleta de lixo por 100 solicitações_).

O manipulador de coleta de lixo usa a diretiva `gc_maxlifetime`—o número de segundos após o qual as sessões são vistas como _lixo_ e potencialmente limpas.

Em alguns sistemas operacionais (Debian/Ubuntu), a diretiva `session.gc_probability` padrão é `0`, o que impede a execução do manipulador de coleta de lixo.

Você pode substituir as diretivas `session.gc_` do arquivo `php.ini` no arquivo `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

A configuração varia, dependendo do tráfego e das necessidades específicas do site do comerciante.
