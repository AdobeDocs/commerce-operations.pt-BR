---
title: Desinstalar ou reinstalar o Adobe Commerce
description: Siga estas etapas para desinstalar e reinstalar instalações no local do Adobe Commerce e do Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Desinstalar ou reinstalar o Adobe Commerce

Antes de usar esses comandos, é necessário [instale o aplicativo](../tutorials/install.md).

## Atualize o aplicativo

Para atualizar o aplicativo:

* Se você instalou o software a partir de um arquivo ou se usou o &#39;composer-create-project&#39;, consulte o [Guia de atualização](../../upgrade/overview.md).
* Se você for um desenvolvedor contribuidor (ou seja, você `git clone`), consulte [Atualize o aplicativo](../../upgrade/developer/git-installs.md).

## Reinstale o aplicativo

A maneira como você reinstala o aplicativo da linha de comando depende da sua função:

* Se você instalou o software a partir de um arquivo ou se usou o &#39;composer-create-project&#39;, consulte [Atualizar dependências de instalação](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Se você for um desenvolvedor contribuidor (ou seja, você começou a usar o `git clone`), consulte [Atualizar dependências de instalação](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Desinstalar o aplicativo

A desinstalação do aplicativo solta e restaura o banco de dados, remove a configuração da implantação e limpa os diretórios em `var`.

Para desinstalar o aplicativo, digite o seguinte comando:

```bash
bin/magento setup:uninstall
```

A seguinte mensagem é exibida para confirmar uma desinstalação bem-sucedida:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Manter arquivos gerados opcionalmente

Por padrão, `bin/magento setup:upgrade` limpa o código compilado e o cache. Normalmente, você usa `bin/magento setup:upgrade` para atualizar componentes e cada componente pode exigir classes compiladas diferentes.

No entanto, em algumas situações (principalmente, ao implantar na produção), talvez você queira evitar a limpeza do código compilado, pois isso pode levar algum tempo. (O [cache](https://glossary.magento.com/cache) ainda é limpo.) Para atualizar o [esquema de banco de dados](https://glossary.magento.com/database-schema) e dados *without* limpar código compilado, insira:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>O `--keep-generated` deve ser usada em circunstâncias limitadas por integradores de sistema experientes *only*. Essa opção deve *never* ser usada em um ambiente de desenvolvimento. O uso incorreto desse parâmetro opcional pode causar erros durante a execução do código.

## Instalar o aplicativo

* [Instalar usando a linha de comando](../advanced.md)
