---
title: Baixar pacotes de dados de amostra do Composer
description: Siga estas etapas para instalar dados de amostra do Adobe Commerce usando o Gerenciador de pacotes PHP do Composer.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Baixar pacotes de dados de amostra do Composer

Esta seção discute como instalar dados de amostra se você tiver o software Adobe Commerce ou Magento Open Source de qualquer uma das seguintes maneiras:

* Baixado um arquivo compactado de `https://magento.com/tech-resources/download`.

  Se você baixou um arquivo do GitHub, esse método não funciona, pois o `composer.json` o arquivo não contém o `repo.magento.com` URL.

* Usado `composer create-project`

Você pode usar esse método para obter dados de amostra para o Adobe Commerce, mas deve usar o mesmo [chaves de autenticação](../prerequisites/authentication-keys.md) usado para instalar o aplicativo.

>[!NOTE]
>
>Se você encontrar erros, como `Could not find package...` ou `...no matching package found...`, verifique se não há erros de digitação no comando. Se ainda encontrar erros, talvez você não tenha acesso aos repositórios corretos do Composer, especialmente se estiver usando o Adobe Commerce. Contato [Suporte ao Adobe Commerce](https://support.magento.com/hc/en-us) para obter ajuda.

Você pode usar o Composer para instalar dados de amostra antes ou depois de instalar o aplicativo; no entanto, pode haver [tarefas adicionais](remove-or-update.md).

Se você for um desenvolvedor contribuinte, consulte [Instalação por clonagem de repositórios](git-repositories.md).

>[!WARNING]
>
>Não instale dados de amostra se seu aplicativo estiver definido para [modo de produção](../../configuration/bootstrap/application-modes.md#production-mode). Alternar para [modo de desenvolvedor](../../configuration/bootstrap/application-modes.md#developer-mode) primeiro. Instalação de dados de amostra no modo de produção [falha](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar dados de amostra usando a linha de comando, digite o seguinte comando como proprietário do sistema de arquivos na `<app_root>` diretório:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Se estiver instalando dados de amostra _após_ instalando o aplicativo, você também deve executar o seguinte comando para atualizar o banco de dados e o esquema no `<app_root>` diretório:

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

Se o erro for exibido, altere para o diretório de instalação do aplicativo e execute `composer update`, que solicita o seu [chaves de autenticação](../prerequisites/authentication-keys.md).

## Conclua a instalação dos dados de amostra

{{$include /help/_includes/sample-data-complete.md}}
