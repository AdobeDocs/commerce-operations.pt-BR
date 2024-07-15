---
title: Migrar dados
description: Saiba como iniciar a migração de dados do Magento 1 para o Magento 2 com o  [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Migrar dados

Antes de começar, siga as etapas abaixo para se preparar:

1. Faça logon no servidor de aplicativos como [o proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório de instalação do aplicativo ou verifique se ele foi adicionado ao sistema `PATH`.

Consulte a seção [primeiras etapas](overview.md#first-steps) para obter mais detalhes.

## Executar o comando de migração de dados

Para começar a migrar dados, execute:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Onde:

* `[-a|--auto]` é um argumento opcional que impede que a migração pare quando encontrar erros de verificação de integridade.

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; este argumento é obrigatório

Nesta etapa, o [!DNL Data Migration Tool] cria tabelas e acionadores adicionais para as tabelas de migração no banco de dados Magento 1. Eles são usados na etapa de migração [incremental/delta](delta.md). Tabelas adicionais contêm informações sobre registros alterados após a execução final da migração. Os gatilhos de banco de dados são usados para preencher essas tabelas extras; portanto, se uma nova operação estiver sendo executada na tabela específica (um registro é adicionado/modificado/removido), esses gatilhos de banco de dados salvarão informações sobre essa operação na tabela extra. Quando executamos um processo de migração delta, o [!DNL Data Migration Tool] verifica se há registros não processados nessas tabelas e migra o conteúdo necessário para o banco de dados Magento 2.

Cada nova tabela contém:

* Prefixo `m2_cl`
* `INSERT`, `UPDATE`, `DELETE` disparadores de eventos.

Por exemplo, para `sales_flat_order`, [!DNL Data Migration Tool] cria:

* Tabela `m2_cl_sales_flat_order`:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` acionadores:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>O [!DNL Data Migration Tool] salva seu progresso atual à medida que é executado. Se ocorrer erros ou uma intervenção do usuário impedir a execução, a Ferramenta retomará o progresso no último estado em boas condições. Para forçar a execução de [!DNL Data Migration Tool] desde o início, use o argumento `--reset`. Nesse caso, recomendamos que você restaure o dump do banco de dados do Magento 2 para evitar a duplicação de dados migrados anteriormente.


## Possíveis erros de consistência

Durante a execução, o [!DNL Data Migration Tool] pode relatar inconsistências entre os bancos de dados Magento 1 e Magento 2 e exibir mensagens como as seguintes:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Consulte a seção [Solução de problemas](https://support.magento.com/hc/en-us/articles/360033020451) deste guia para obter mais informações e recomendações.

## Próxima etapa de migração

[Migrar alterações](delta.md)
