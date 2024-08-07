---
title: Gravar no arquivo de log personalizado
description: Saiba como configurar arquivos de log personalizados.
feature: Configuration, Logs
badge: label="Contribuição de Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Gravar em um arquivo de log personalizado

O módulo `Magento\Framework\Logger` contém as seguintes classes de manipulador:

| Classe | Arquivo de log |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Você pode encontrá-los no diretório `lib/internal/Magento/Framework/Logger/Handler`.

Você pode usar uma das seguintes abordagens para fazer logon em um arquivo personalizado:

- Configurar um arquivo de log personalizado no `di.xml`
- Configurar um arquivo personalizado na classe de manipulador de log personalizado

## Configurar um arquivo de log personalizado no `di.xml`

Este exemplo mostra como usar [tipos virtuais](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) para registrar mensagens `debug` em um arquivo de log personalizado em vez de um `/var/log/debug.log` padrão.

1. No arquivo `di.xml` do módulo, defina um arquivo de log personalizado como um [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   O valor `name` de `Magento\Payment\Model\Method\MyCustomDebug` deve ser exclusivo.

1. Defina o manipulador em outro [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) com um `name` exclusivo:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Insira o `MyCustomLogger` [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) no objeto `Magento\Payment\Model\Method\Logger`:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. A classe virtual `Magento\Payment\Model\Method\MyCustomDebug` está inserida no manipulador `debug` da propriedade `$logger` na classe `Magento\Payment\Model\Method\Logger`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Mensagens de exceção são registradas no arquivo `/var/log/payment.log`.

## Configurar um arquivo de log personalizado na classe de manipulador de log

Este exemplo mostra como usar uma classe de manipulador de agente de log personalizado para registrar mensagens `error` em um arquivo de log específico.

1. Crie uma classe que registre dados. Neste exemplo, a classe é definida em `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Defina o manipulador para esta classe como um [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) no arquivo `di.xml` do módulo.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` é um identificador exclusivo.

1. Na definição `type`, especifique o nome da classe em que o manipulador de log personalizado está inserido. Use o nome do tipo virtual da etapa anterior como argumento para esse tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Código Source da classe `Vendor\ModuleName\Observer\MyObserver`:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. A classe `Vendor\ModuleName\Logger\Handler\ErrorHandler` é inserida no manipulador `error` da propriedade `$logger` em `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Mensagens de exceção registradas no arquivo `/var/log/my_custom_logger/error.log`.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
