---
title: Atividade do banco de dados de log
description: Configure o Commerce para registrar a atividade do banco de dados usando a interface do Logger.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Atividade do banco de dados de log

O exemplo a seguir mostra como registrar a atividade do banco de dados usando o [`Magento\Framework\DB\LoggerInterface`][interface], que tem duas implementações:

- Não registra nada (padrão): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Registra no `var/log` diretório: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Você pode usar a CLI de comércio para [habilitar e desabilitar o log do banco de dados](../cli/enable-logging.md#database-logging).

Para alterar a configuração padrão de `\Magento\Framework\DB\Logger\LoggerProxy`edite seu `app/etc/di.xml`.

Primeiro, altere os valores padrão de `loggerAlias` e `logCallStack` argumentos para:

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

Depois disso, forneça o caminho do arquivo para `Magento\Framework\DB\Logger\File`:

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
