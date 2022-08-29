---
title: Migrar dados
description: Saiba como começar a migrar dados do Magento 1 para o Magento 2 com o [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Migrar dados

Antes de começar, execute as seguintes etapas para preparar:

1. Faça logon no servidor de aplicativos como [o proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Altere para o diretório de instalação do aplicativo ou verifique se ele foi adicionado ao sistema `PATH`.

Consulte a [primeiros passos](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração de dados

Para iniciar a migração de dados, execute:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Em que:

* `[-a|--auto]` é um argumento opcional que impede a interrupção da migração quando encontra erros de verificação de integridade.

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; este argumento é obrigatório

Nessa etapa, o [!DNL Data Migration Tool] O cria tabelas e acionadores adicionais para as tabelas de migração no banco de dados do Magento 1. Eles são usados na variável [incremental/delta](delta.md) etapa de migração. Tabelas adicionais contêm informações sobre registros alterados após a execução final da migração. Os acionadores de banco de dados são usados para preencher essas tabelas extras, de modo que, se uma nova operação estiver sendo executada na tabela específica (um registro é adicionado/modificado/removido), esses acionadores de banco de dados salvarão informações sobre essa operação na tabela extra. Quando executamos um processo de migração delta, a variável [!DNL Data Migration Tool] O verifica essas tabelas para os registros não processados e migra o conteúdo necessário para o banco de dados do Magento 2.

Cada nova tabela contém:

* `m2_cl` prefixo
* `INSERT`, `UPDATE`, `DELETE` acionadores de evento.

Por exemplo, para a variável `sales_flat_order` o [!DNL Data Migration Tool] cria:

* `m2_cl_sales_flat_order` tabela:

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
>O [!DNL Data Migration Tool] salva seu progresso atual enquanto ele é executado. Se erros ou uma intervenção do usuário impedir a execução, a ferramenta retomará o progresso no último estado em boas condições. Para forçar o [!DNL Data Migration Tool] para ser executado a partir do início, use o `--reset` argumento . Nesse caso, recomendamos que você restaure o despejo do banco de dados do Magento 2 para evitar a duplicação de dados migrados anteriormente.


## Possíveis erros de consistência

Enquanto estiver em execução, a variável [!DNL Data Migration Tool] pode relatar inconsistências entre bancos de dados Magento 1 e Magento 2 e exibir mensagens como as seguintes:

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

Consulte a [Solução de problemas](https://support.magento.com/hc/en-us/articles/360033020451) para obter mais informações e recomendações.

## Próxima etapa de migração

[Migrar alterações](delta.md)
