---
title: Interface do agente de log
description: Saiba como usar a interface do agente de log no Adobe Commerce para fazer logon personalizado. Conheça a implementação do PSR-3 e as funções de registro.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Interface do agente de log

Para começar a trabalhar com um agente de log, você deve criar uma instância de `\Psr\Log\LoggerInterface`. Com essa interface, você pode chamar as seguintes funções para gravar dados em arquivos de log:

- [alerta()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [crítico()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [depurar()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergência()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [erro()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [informações()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [aviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [aviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Uma maneira de fazer isso é explicada no exemplo de [Atividade do banco de dados de log](../logs/database-activity.md).

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

O exemplo anterior mostra que `SomeModel` recebe um objeto `\Psr\Log\LoggerInterface` usando injeção de construtor. Em um método `doSomething`, se ocorrer algum erro, ele será registrado em um método `critical` (`$this->logger->critical($e);`).

A [RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define oito níveis de log (depuração, informações, aviso, aviso, erro, crítico, alerta e emergência).
