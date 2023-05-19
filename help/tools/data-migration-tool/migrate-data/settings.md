---
title: Configurações de migração de dados
description: Saiba como começar a migrar configurações do Magento 1 para o Magento 2 com o [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Configurações de migração de dados

A variável `Settings` O modo migra lojas, sites e configurações do sistema, como configurações de envio, pagamento e imposto. De acordo com nossa migração de dados [pedido](overview.md#migration-order), você deve migrar as configurações primeiro.

Antes de começar, siga as etapas abaixo para se preparar:

1. Efetue login no servidor de aplicativos como o [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Altere para a variável `/bin` ou verifique se ele foi adicionado ao seu sistema `PATH`.

>[!NOTE]
>
>Certifique-se de que o Magento 2 seja implantado em `default` modo. O modo de desenvolvedor pode causar erros de validação na ferramenta de migração.


Consulte a [primeiros passos](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração de configurações

Para iniciar a migração das configurações, execute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Onde:

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração

* `[-a|--auto]` é um argumento opcional que impede que a migração pare quando encontrar erros de verificação de integridade.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para a ferramenta de migração [`config.xml`](../configure.md#configure-migration-in-vendor-folder) arquivo; este argumento é obrigatório.

>[!NOTE]
>
>Este comando não migra todas as configurações. Verifique todas as configurações no Magento 2 Admin antes de continuar.


A variável `Migration completed` será exibida depois que as configurações forem transferidas com êxito.

## Configurar regras de migração personalizadas

Você pode ignorar, renomear ou alterar as configurações do sistema ao migrar as configurações. Para isso, especifique as regras personalizadas na `settings.xml` arquivo.

1. Efetue login no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Altere para o seguinte diretório:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por exemplo, se o aplicativo estiver instalado no `/var/www/html`, o `settings.xml.dist` O arquivo está em um dos seguintes diretórios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para criar um `settings.xml` da amostra fornecida, execute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Faça as alterações no `settings.xml`.

1. Para especificar o novo nome do arquivo de configurações para mapeamento, altere o `<settings_map_file>` na guia `path/to/config.xml` arquivo.

Para obter mais detalhes, consulte [Modo de migração de configurações](../technical-specification.md#settings-migration-mode) seção do Guia da ferramenta [especificação](../technical-specification.md).

## Próxima etapa de migração

* [Migrar dados](data.md)
