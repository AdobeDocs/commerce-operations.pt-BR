---
title: Registrar atividade do banco de dados
description: Configure o Commerce para registrar a atividade do banco de dados usando a interface do Logger.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Registrar atividade do banco de dados

O exemplo a seguir mostra como registrar a atividade do banco de dados usando o [`Magento\Framework\DB\LoggerInterface`][interface], que tem duas implementações:

- Não registra nada (padrão): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Logs no diretório `var/log`: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Você pode usar a CLI do Commerce para [habilitar e desabilitar o log do banco de dados](../cli/enable-logging.md#database-logging).

Para alterar a configuração padrão do `\Magento\Framework\DB\Logger\LoggerProxy`, edite o `app/etc/di.xml`.

Primeiro, altere os valores padrão dos argumentos `loggerAlias` e `logCallStack` para:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Depois disso, forneça o caminho de arquivo para `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Por fim, compile o código com:

```bash
bin/magento setup:di:compile
```

E limpe o cache com:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
