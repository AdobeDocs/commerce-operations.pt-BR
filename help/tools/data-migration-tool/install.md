---
title: Instale o [!DNL Data Migration Tool]
description: Saiba como instalar o [!DNL Data Migration Tool] para transferir dados entre o Magento 1 e o Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Instale o [!DNL Data Migration Tool]

>[!INFO]
>
>Versões de Magento e [!DNL Data Migration Tool] deve corresponder.


Certifique-se de usar *mesma versão lançada* do Magento 2 e do [!DNL Data Migration Tool]. Por exemplo, para o Magento versão 2.2.0, você também deve usar o [!DNL Data Migration Tool] versão 2.2.0.

## Verificar a versão

Use um dos seguintes métodos para verificar sua versão do Magento:

- [Composer](#composer-metapackage)
- [Repositório GitHub](#github-repository)

### Metapackeamento do compositor

Se você tiver baixado o software Magento usando um [Composer](https://glossary.magento.com/composer) metapackage, digite o seguinte comando:

```bash
php <magento_root>/bin/magento --version
```

### Repositório GitHub

Se você clonou o repositório GitHub Magento 2, digite os seguintes comandos:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Se você estiver atualmente na `develop` ramificação, você deve alterar para um [ramificação liberada](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) antes de continuar.

Se você ainda não instalou o software Adobe Commerce ou Magento Open Source, [instale-o agora](../../installation/prerequisites/commerce.md).
Se você estiver clonando o repositório GitHub, certifique-se de fazer o check-out de uma tag de versão conforme discutido em [(Contribuidor) Clonar o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Encontrar versões lançadas do [!DNL Data Migration Tool]

Vá para o [Versões](https://github.com/magento/data-migration-tool/releases) da página [!DNL Data Migration Tool] Repositório GitHub para encontrar as versões disponíveis lançadas.

## Instale o [!DNL Data Migration Tool]

Você pode instalar o [!DNL Data Migration Tool] de:

- [&quot;repo.magento.com&quot;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Antes de instalar, verifique se você tem:

- Concluídas todas as tarefas mencionadas no [Pré-condições](prerequisites.md) seção
- [Verificada a versão](install.md#check-your-version) do software Magento 2

### Instalar de `repo.magento.com`

Para instalar o [!DNL Data Migration Tool], você deve atualizar `composer.json` no diretório de instalação raiz do Magento para fornecer a localização do [!DNL Data Migration Tool] pacote.

1. Faça logon no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Insira os seguintes comandos:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Onde `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.2.0, insira:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Quando solicitado, insira [chaves de autenticação](../../installation/prerequisites/authentication-keys.md). Sua chave pública é seu nome de usuário; sua chave privada é sua senha.

### Instalar a partir do GitHub

Se você clonou o repositório GitHub, siga as etapas abaixo para instalar o [!DNL Data Migration Tool].

1. Faça logon no servidor de aplicativos como, ou alterne para, o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para o diretório raiz do aplicativo.
1. Insira os seguintes comandos:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   em que `<version>` deve corresponder à versão da base de código Magento 2.

   Por exemplo, para a versão 2.2.0, insira:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Verificar versão do instalado [!DNL Data Migration Tool]

1. Altere para sua [!DNL Data Migration Tool] diretório: `<vendor>/magento/data-migration-tool`.

1. Abrir [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) em um editor de texto.

1. O `version` a entrada nesse arquivo é a versão do [!DNL Data Migration Tool].
