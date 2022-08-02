---
title: Interface do logger
description: Introdução à interface do logger.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Interface do logger

Para começar a trabalhar com um logger, você deve criar uma instância de `\Psr\Log\LoggerInterface`. Com essa interface, você pode chamar as seguintes funções para gravar dados em arquivos de log:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [crítico()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergência()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Uma maneira de fazer isso é explicada no relatório [Atividade do banco de dados de log](../logs/database-activity.md) exemplo.

Uma outra maneira:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

O exemplo anterior mostra que `SomeModel` recebe uma `\Psr\Log\LoggerInterface` usando injeção de construtor. Em um método `doSomething`, se ocorrer algum erro, ele será registrado em um método `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define oito níveis de log (depurar, informações, aviso, aviso, erro, crítico, alerta e emergência).
