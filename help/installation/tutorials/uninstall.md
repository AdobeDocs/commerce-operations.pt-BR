---
title: Desinstalar ou reinstalar o Adobe Commerce
description: Siga estas etapas para desinstalar e reinstalar as instalações locais do Adobe Commerce.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Desinstalar ou reinstalar o Adobe Commerce

Antes de usar estes comandos, você deve [instalar o aplicativo](../tutorials/install.md).

## Atualizar o aplicativo

Para atualizar o aplicativo:

* Se você instalou o software a partir de um arquivo morto ou se usou &#39;composer-create-project&#39;, consulte o [Guia de Atualização](../../upgrade/overview.md).
* Se você for um desenvolvedor contribuinte (isto é, se você usou o `git clone`), consulte [Atualizar o aplicativo](../../upgrade/developer/git-installs.md).

## Reinstale o aplicativo

A maneira como você reinstala o aplicativo a partir da linha de comando depende da sua função:

* Se você instalou o software a partir de um arquivo morto ou se usou &#39;composer-create-project&#39;, consulte [Atualizar dependências de instalação](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Se você for um desenvolvedor contribuinte (isto é, você começou a usar o `git clone`), consulte [Atualizar dependências de instalação](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Desinstalar o aplicativo

A desinstalação do aplicativo remove e restaura o banco de dados, remove a configuração da implantação e limpa diretórios em `var`.

Para desinstalar o aplicativo, digite o seguinte comando:

```bash
bin/magento setup:uninstall
```

A seguinte mensagem é exibida para confirmar uma desinstalação bem-sucedida:

```
[SUCCESS]: Magento uninstallation complete.
```

## Como opção, manter arquivos gerados

Por padrão, `bin/magento setup:upgrade` limpa o código compilado e o cache. Normalmente, você usa `bin/magento setup:upgrade` para atualizar componentes e cada componente pode exigir diferentes classes compiladas.

No entanto, em algumas situações (particularmente, na implantação em produção), talvez você queira evitar a limpeza do código compilado, pois pode levar algum tempo. (O cache ainda está limpo.) Para atualizar o esquema de banco de dados e os dados *sem* limpando o código compilado, digite:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>A opção `--keep-generated` opcional deve ser usada em circunstâncias limitadas por integradores de sistema experientes *somente*. Esta opção deve *nunca* ser usada em um ambiente de desenvolvimento. O uso inadequado desse parâmetro opcional pode causar erros durante a execução do código.

## Instalar o aplicativo

* [Instalar usando a linha de comando](../advanced.md)
