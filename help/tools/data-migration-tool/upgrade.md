---
title: Atualizar o [!DNL Data Migration Tool]
description: Saiba como atualizar o [!DNL Data Migration Tool] para transferir dados entre a Magento 1 e a Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '235'
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

Caso ainda não o tenha feito, [atualize o software Magento](../../upgrade/overview.md).

### Fazer backup do diretório `vendor/magento/data-migration-tool`

Antes de atualizar o [!DNL Data Migration Tool], faça backup pelo menos do diretório `vendor/magento/data-migration-tool`. Durante a atualização, ele pode ser excluído e substituído pelo código atualizado.

Também é possível fazer backup de toda a base de código e do banco de dados da Magento usando o seguinte comando:

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>O diretório `vendor/magento/data-migration-tool` contém seu código personalizado. Se você não fizer backup, poderá perder suas personalizações durante a atualização.


### Verificar se as versões são correspondentes

As versões do [!DNL Data Migration Tool] e do software Magento devem ser exatamente iguais. Por exemplo, o Magento 2.1.2 exige a versão 2.1.2 do [!DNL Data Migration Tool].

Consulte o tópico [Instalar [!DNL Data Migration Tool]](install.md) para saber como:

* [Verifique](install.md#check-your-version) sua versão do Magento 2

* [Localizar](install.md#find-released-versions-of-data-migration-tool) versões lançadas de [!DNL Data Migration Tool]

* [Verificar](install.md#check-version-of-installed-data-migration-tool) a versão [!DNL Data Migration Tool]

## Atualizar o [!DNL Data Migration Tool]

1. Faça logon no servidor de aplicativos como ou alterne para [o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Digite o seguinte comando:

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   onde `<version>` deve corresponder à versão da base de código do Magento 2.

   Por exemplo, para a versão 2.1.2, digite:

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. Aguarde enquanto o comando é concluído.
