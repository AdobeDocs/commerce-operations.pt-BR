---
title: Atualizar o  [!DNL Data Migration Tool]
description: Saiba como atualizar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Atualizar o [!DNL Data Migration Tool]

Para verificar se as versões da sua instalação atual do Magento 2 e do [!DNL Data Migration Tool] são exatamente iguais, talvez seja necessário atualizar a ferramenta.

## Pré-requisitos

Antes de atualizar o [!DNL Data Migration Tool], você deve:

* Atualize seu software Magento para obter a versão mais recente

* Fazer backup do diretório `vendor/magento/data-migration-tool`

* Verifique se a versão [!DNL Data Migration Tool] corresponde à versão do aplicativo Magento

### Atualize seu software Magento

Se ainda não tiver feito isso, [atualize o software Magento](../../upgrade/overview.md).

### Fazer backup do diretório `vendor/magento/data-migration-tool`

Antes de atualizar o [!DNL Data Migration Tool], faça backup pelo menos do diretório `vendor/magento/data-migration-tool`. Durante a atualização, ele pode ser excluído e substituído pelo código atualizado.

Você também pode fazer backup de toda a base de código do Magento e do banco de dados usando o seguinte comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>O diretório `vendor/magento/data-migration-tool` contém seu código personalizado. Se você não fizer backup, poderá perder suas personalizações durante a atualização.


### Verificar se as versões são correspondentes

As versões do [!DNL Data Migration Tool] e do software Magento devem ser exatamente iguais. Por exemplo, o Magento 2.1.2 exige a versão 2.1.2 do [!DNL Data Migration Tool].

Consulte o tópico [Instalar [!DNL Data Migration Tool]](install.md) para saber como:

* [Verificar](install.md#check-your-version) a sua versão do Magento 2

* [Localizar](install.md#find-released-versions-of-data-migration-tool) versões lançadas de [!DNL Data Migration Tool]

* [Verificar](install.md#check-version-of-installed-data-migration-tool) a versão [!DNL Data Migration Tool]

## Atualizar o [!DNL Data Migration Tool]

1. Faça logon no servidor de aplicativos como ou alterne para [o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Digite o seguinte comando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   onde `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.1.2, digite:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Aguarde enquanto o comando é concluído.
