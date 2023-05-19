---
title: Atualizar o [!DNL Data Migration Tool]
description: Saiba como atualizar o [!DNL Data Migration Tool] para transferir dados entre Magento 1 e Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Atualizar o [!DNL Data Migration Tool]

Para verificar as versões da sua instalação atual do Magento 2 e do [!DNL Data Migration Tool] for exatamente igual, talvez seja necessário atualizar a ferramenta.

## Pré-requisitos

Antes de atualizar o [!DNL Data Migration Tool], você deve:

* Atualize seu software Magento para obter a versão mais recente

* Faça backup do `vendor/magento/data-migration-tool` diretório

* Certifique-se de que a variável [!DNL Data Migration Tool] versão corresponde à versão do aplicativo Magento

### Atualize seu software Magento

Se você ainda não tiver feito isso, [atualize o software do Magento](../../upgrade/overview.md).

### Faça backup do `vendor/magento/data-migration-tool` diretório

Antes de atualizar o [!DNL Data Migration Tool], faça backup de pelo menos o `vendor/magento/data-migration-tool` diretório. Durante a atualização, ele pode ser excluído e substituído pelo código atualizado.

Você também pode fazer backup de toda a base de código do Magento e do banco de dados usando o seguinte comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>A variável `vendor/magento/data-migration-tool` O diretório contém seu código personalizado. Se você não fizer backup, poderá perder suas personalizações durante a atualização.


### Verificar se as versões são correspondentes

As versões do [!DNL Data Migration Tool] e o software Magento deve ser exatamente igual. Por exemplo, o Magento 2.1.2 exige a versão 2.1.2 do [!DNL Data Migration Tool].

Consulte a [Instalar [!DNL Data Migration Tool]](install.md) tópico para saber como:

* [Marcar](install.md#check-your-version) sua versão do Magento 2

* [Localizar](install.md#find-released-versions-of-data-migration-tool) versões lançadas do [!DNL Data Migration Tool]

* [Marcar](install.md#check-version-of-installed-data-migration-tool) o [!DNL Data Migration Tool] version

## Atualizar o [!DNL Data Migration Tool]

1. Efetue login no servidor de aplicativos como ou alterne para [o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
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
