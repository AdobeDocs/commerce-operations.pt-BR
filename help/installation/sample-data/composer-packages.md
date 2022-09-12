---
title: Baixar pacotes do Composer de dados de amostra
description: Siga estas etapas para instalar os dados de amostra do Adobe Commerce e do Magento Open Source usando o Gerenciador de pacotes PHP do Composer.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Baixar pacotes do Composer de dados de amostra

Esta seção discute como instalar dados de amostra se você tiver o software Adobe Commerce ou Magento Open Source de qualquer uma das seguintes maneiras:

* Arquivo compactado baixado de `https://magento.com/tech-resources/download`.

   Se você baixou um arquivo do GitHub, esse método não funcionará porque a variável `composer.json` O arquivo não contém o `repo.magento.com` URL.

* Usado `composer create-project`

Você pode usar esse método para obter dados de amostra para Adobe Commerce e Magento Open Source, mas deve usar o mesmo [chaves de autenticação](../prerequisites/authentication-keys.md) que você costumava instalar o aplicativo.

>[!NOTE]
>
>Se encontrar erros, como `Could not find package...` ou `...no matching package found...`, certifique-se de que não haja erros de digitação em seu comando. Se você ainda encontrar erros, talvez não tenha acesso aos repositórios corretos do Composer, especialmente se estiver usando o Adobe Commerce. Contato [Suporte Adobe Commerce](https://support.magento.com/hc/en-us) para obter ajuda.

Você pode usar o Composer para instalar dados de amostra antes ou depois de instalar o aplicativo; no entanto, pode haver [tarefas adicionais](remove-or-update.md).

Se você for um desenvolvedor contribuinte, consulte [Instalar por clonagem de repositórios](git-repositories.md).

>[!WARNING]
>
>Não instale dados de amostra se o aplicativo estiver configurado para [modo de produção](../../configuration/bootstrap/application-modes.md#production-mode). Mudar para [modo desenvolvedor](../../configuration/bootstrap/application-modes.md#developer-mode) primeiro. Instalação de dados de amostra no modo de produção [fail](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar dados de amostra usando a linha de comando, digite o seguinte comando como proprietário do sistema de arquivos na `<app_root>` diretório:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Se você estiver instalando dados de amostra _after_ ao instalar o aplicativo, você também deve executar o seguinte comando para atualizar o banco de dados e o schema no `<app_root>` diretório:

```bash
bin/magento setup:upgrade
```

Você deve [autenticar](../prerequisites/authentication-keys.md) para concluir a ação.

## Erro de autenticação

O seguinte erro de autenticação pode ser exibido:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Se o erro for exibido, altere para o diretório de instalação do aplicativo e execute `composer update`, que solicita que você [chaves de autenticação](../prerequisites/authentication-keys.md).

## Conclua a instalação de dados de amostra

{{$include /help/_includes/sample-data-complete.md}}
