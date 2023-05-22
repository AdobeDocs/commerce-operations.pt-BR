---
title: Interface do agente de log
description: Introdução à interface do agente de log.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Interface do agente de log

Para começar a trabalhar com um agente de log, você deve criar uma instância de `\Psr\Log\LoggerInterface`. Com essa interface, você pode chamar as seguintes funções para gravar dados em arquivos de log:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Uma maneira de fazer isso é explicada na [Registrar atividade do banco de dados](../logs/database-activity.md) exemplo.

Segue-se outro caminho:

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

O exemplo anterior mostra que `SomeModel` recebe um `\Psr\Log\LoggerInterface` objeto usando injeção de construtor. Em um método `doSomething`, se algum erro ocorrer, ele será registrado em um método `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define oito níveis de log (depuração, informações, aviso, aviso, erro, crítico, alerta e emergência).
