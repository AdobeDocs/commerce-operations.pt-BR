---
title: Atualize o [!DNL Data Migration Tool]
description: Saiba como atualizar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Atualize o [!DNL Data Migration Tool]

Para certificar-se das versões da sua instalação Magento 2 atual e da [!DNL Data Migration Tool] corresponda exatamente, talvez seja necessário atualizar a ferramenta.

## Pré-requisitos

Antes de atualizar o [!DNL Data Migration Tool], você deve:

* Atualize seu software Magento para obter a versão mais recente

* Faça o backup do `vendor/magento/data-migration-tool` diretory

* Certifique-se de que a variável [!DNL Data Migration Tool] A versão corresponde à versão do aplicativo Magento

### Atualize seu software Magento

Se ainda não o fez, [atualizar o software Magento](../../upgrade/overview.md).

### Faça o backup do `vendor/magento/data-migration-tool` diretory

Antes de atualizar o [!DNL Data Migration Tool], faça backup pelo menos da variável `vendor/magento/data-migration-tool` diretório. Durante a atualização, ela pode ser excluída e substituída pelo código atualizado.

Você também pode fazer backup de toda a base de código e o banco de dados do Magento usando o seguinte comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>O `vendor/magento/data-migration-tool` O diretório contém seu código personalizado. Se você não fizer o backup, você poderá perder suas personalizações durante a atualização.


### Certifique-se de que as versões correspondam

As versões do [!DNL Data Migration Tool] e seu software Magento deve corresponder exatamente. Por exemplo, o Magento 2.1.2 requer a versão 2.1.2 do [!DNL Data Migration Tool].

Consulte a [Instalar [!DNL Data Migration Tool]](install.md) tópico para saber como:

* [Verificar](install.md#check-your-version) sua versão do Magento 2

* [Localizar](install.md#find-released-versions-of-data-migration-tool) versões lançadas do [!DNL Data Migration Tool]

* [Verificar](install.md#check-version-of-installed-data-migration-tool) o [!DNL Data Migration Tool] version

## Atualize o [!DNL Data Migration Tool]

1. Faça logon no servidor de aplicativos como ou alterne para [o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Digite o seguinte comando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   em que `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.1.2, insira:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Aguarde enquanto o comando é concluído.
