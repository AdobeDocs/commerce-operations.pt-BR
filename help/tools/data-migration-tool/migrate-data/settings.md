---
title: Configurações de migração de dados
description: Saiba como iniciar a migração de configurações do Magento 1 para o Magento 2 com o  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Configurações de migração de dados

O modo `Settings` migra lojas, sites e configurações do sistema, como configurações de remessa, pagamento e imposto. De acordo com nossa [ordem](overview.md#migration-order) de migração de dados, você deve migrar as configurações primeiro.

Antes de começar, siga as etapas abaixo para se preparar:

1. Faça logon no servidor de aplicativos como o [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Altere para o diretório `/bin` ou verifique se ele foi adicionado ao sistema `PATH`.

>[!NOTE]
>
>Verifique se o Magento 2 está implantado no modo `default`. O modo de desenvolvedor pode causar erros de validação na ferramenta de migração.


Consulte a seção [primeiras etapas](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração de configurações

Para iniciar a migração das configurações, execute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Onde:

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração

* `[-a|--auto]` é um argumento opcional que impede que a migração pare quando encontrar erros de verificação de integridade.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para o arquivo [`config.xml`](../configure.md#configure-migration-in-vendor-folder) da ferramenta de migração. Esse argumento é obrigatório.

>[!NOTE]
>
>Este comando não migra todas as configurações. Verifique todas as configurações no Administrador do Magento 2 antes de continuar.


A mensagem `Migration completed` é exibida após as configurações serem transferidas com êxito.

## Configurar regras de migração personalizadas

Você pode ignorar, renomear ou alterar as configurações do sistema ao migrar as configurações. Para isso, especifique suas regras personalizadas no arquivo `settings.xml`.

1. Faça logon no servidor de aplicativos como ou alterne para o [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Altere para o seguinte diretório:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por exemplo, se o aplicativo estiver instalado em `/var/www/html`, o arquivo `settings.xml.dist` estará em um dos seguintes diretórios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para criar um arquivo `settings.xml` a partir da amostra fornecida, execute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Faça as alterações em `settings.xml`.

1. Para especificar o novo nome do arquivo de configurações para mapeamento, altere a marca `<settings_map_file>` no arquivo `path/to/config.xml`.

Para obter mais detalhes, consulte a seção [Modo de migração das configurações](../technical-specification.md#settings-migration-mode) da [especificação](../technical-specification.md) da ferramenta.

## Próxima etapa de migração

* [Migrar dados](data.md)
