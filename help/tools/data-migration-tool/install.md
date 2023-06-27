---
title: Instale o [!DNL Data Migration Tool]
description: Saiba como instalar o [!DNL Data Migration Tool] para transferir dados entre Magento 1 e Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Instale o [!DNL Data Migration Tool]

>[!INFO]
>
>Versões do Magento e [!DNL Data Migration Tool] deve corresponder.


Verifique se você está usando *a mesma versão lançada* do Magento 2 e do [!DNL Data Migration Tool]. Por exemplo, para a versão 2.2.0 do Magento, você também deve usar o [!DNL Data Migration Tool] versão 2.2.0.

## Verifique sua versão

Use um dos seguintes métodos para verificar sua versão do Magento:

- [Compositor](#composer-metapackage)
- [Repositório do GitHub](#github-repository)

### Metapackage do compositor

Se você baixou o software Magento usando um metapackage Composer, digite o seguinte comando:

```bash
php <magento_root>/bin/magento --version
```

### Repositório do GitHub

Se você clonou o repositório GitHub Magento 2, insira os seguintes comandos:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Se, atualmente, você estiver na `develop` ramificação, você deve alterar para uma [ramificação liberada](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) antes de continuar.

Se você ainda não tiver instalado o software Adobe Commerce ou Magento Open Source, [instalar agora](../../installation/prerequisites/commerce.md).
Se estiver clonando o repositório GitHub, verifique uma tag de versão, conforme discutido em [(Colaborador) Clonar o repositório do GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Localizar versões lançadas de [!DNL Data Migration Tool]

Vá para a [Versões](https://github.com/magento/data-migration-tool/releases) página do [!DNL Data Migration Tool] Repositório GitHub para encontrar versões lançadas disponíveis.

## Instale o [!DNL Data Migration Tool]

Você pode instalar o [!DNL Data Migration Tool] de:

- [&quot;repo.magento.com&quot;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Antes de instalar, verifique se você tem:

- Concluiu todas as tarefas mencionadas na [Pré-condições](prerequisites.md) seção
- [Verificada a versão](install.md#check-your-version) do software Magento 2

### Instalar de `repo.magento.com`

Para instalar o [!DNL Data Migration Tool], você deve atualizar `composer.json` no diretório de instalação raiz do Magento para fornecer a localização do [!DNL Data Migration Tool] pacote.

1. Efetue login no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Digite os seguintes comandos:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Onde `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.2.0, digite:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Quando solicitado, insira o [chaves de autenticação](../../installation/prerequisites/authentication-keys.md). Sua chave pública é seu nome de usuário; sua chave privada é sua senha.

### Instalar do GitHub

Se você tiver clonado o repositório GitHub, siga as etapas abaixo para instalar o [!DNL Data Migration Tool].

1. Efetue login no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Digite os seguintes comandos:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   onde `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.2.0, digite:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Verificar versão do instalado [!DNL Data Migration Tool]

1. Altere para o seu [!DNL Data Migration Tool] diretório: `<vendor>/magento/data-migration-tool`.

1. Abertura [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) em um editor de texto.

1. A variável `version` nesse arquivo é a versão da variável [!DNL Data Migration Tool].
