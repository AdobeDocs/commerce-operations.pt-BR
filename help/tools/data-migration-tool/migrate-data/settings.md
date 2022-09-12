---
title: Configurações de migração de dados
description: Saiba como começar a migrar configurações do Magento 1 para o Magento 2 com o [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# Configurações de migração de dados

O `Settings` O modo migra lojas, sites e configurações do sistema, como configurações de envio, pagamento e imposto. De acordo com nossa migração de dados [pedido](overview.md#migration-order), primeiro deve migrar as configurações.

Antes de começar, execute as seguintes etapas para preparar:

1. Faça logon no servidor de aplicativos como [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Alterar para `/bin` ou verifique se ele foi adicionado ao seu sistema `PATH`.

>[!NOTE]
>
>Verifique se a Magento 2 foi implantada em `default` modo. O modo Desenvolvedor pode causar erros de validação na ferramenta de migração.


Consulte a [primeiros passos](overview.md#first-steps) para obter mais detalhes.

## Execute o comando de migração de configurações

Para iniciar a migração das configurações, execute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Em que:

* `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração

* `[-a|--auto]` é um argumento opcional que impede a interrupção da migração quando encontra erros de verificação de integridade.

* `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para a ferramenta de migração [`config.xml`](../configure.md#configure-migration-in-vendor-folder) ficheiro; esse argumento é obrigatório.

>[!NOTE]
>
>Este comando não migra todas as configurações. Verifique todas as configurações no Magento 2 [Administrador](https://glossary.magento.com/admin) antes de continuar.


O `Migration completed` é exibida após as configurações serem transferidas com êxito.

## Configurar regras de migração personalizadas

Você pode ignorar, renomear ou alterar as configurações do sistema ao migrar as configurações. Para isso, especifique as regras personalizadas na `settings.xml` arquivo.

1. Faça logon no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

1. Altere para o seguinte diretório:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por exemplo, se o aplicativo estiver instalado em `/var/www/html`, o `settings.xml.dist` O arquivo está em um dos seguintes diretórios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para criar um `settings.xml` do exemplo fornecido, execute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Faça as alterações em `settings.xml`.

1. Para especificar o novo nome do arquivo de configurações para mapeamento, altere a variável `<settings_map_file>` na `path/to/config.xml` arquivo.

Para obter mais detalhes, consulte a [Modo de migração de configurações](../technical-specification.md#settings-migration-mode) da seção da ferramenta [especificação](../technical-specification.md).

## Próxima etapa de migração

* [Migrar dados](data.md)
