---
title: Baixar pacotes de dados de amostra do Composer
description: Siga estas etapas para instalar dados de amostra do Adobe Commerce usando o Gerenciador de pacotes PHP do Composer.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Baixar pacotes de dados de amostra do Composer

Esta seção discute como instalar dados de amostra se você tiver o software Adobe Commerce de qualquer uma das seguintes maneiras:

* Arquivo compactado baixado de `https://magento.com/tech-resources/download`.

  Se você baixou um arquivo do GitHub, esse método não funciona porque o arquivo `composer.json` não contém a URL `repo.magento.com`.

* Usado `composer create-project`

Você pode usar este método para obter dados de amostra para o Adobe Commerce, mas deve usar as mesmas [chaves de autenticação](../prerequisites/authentication-keys.md) usadas para instalar o aplicativo.

>[!NOTE]
>
>Se você encontrar erros, como `Could not find package...` ou `...no matching package found...`, verifique se não há erros de digitação no seu comando. Se ainda encontrar erros, talvez você não tenha acesso aos repositórios corretos do Composer, especialmente se estiver usando o Adobe Commerce. Contate o [Suporte da Adobe Commerce](https://support.magento.com/hc/en-us) para obter ajuda.

Você pode usar o Composer para instalar dados de exemplo antes ou depois de instalar o aplicativo; no entanto, pode haver [tarefas adicionais](remove-or-update.md).

Se você for um desenvolvedor contribuinte, consulte [Instalar clonando repositórios](git-repositories.md).

>[!WARNING]
>
>Não instale dados de amostra se seu aplicativo estiver definido como [modo de produção](../../configuration/bootstrap/application-modes.md#production-mode). Mude primeiro para o [modo de desenvolvedor](../../configuration/bootstrap/application-modes.md#developer-mode). A instalação de dados de amostra no modo de produção [falha](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar dados de exemplo usando a linha de comando, digite o seguinte comando como proprietário do sistema de arquivos no diretório `<app_root>`:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Se você estiver instalando dados de exemplo _após_ a instalação do aplicativo, também deverá executar o seguinte comando para atualizar o banco de dados e o esquema no diretório `<app_root>`:

```bash
bin/magento setup:upgrade
```

Você precisa [autenticar](../prerequisites/authentication-keys.md) para concluir a ação.

## Erro de autenticação

O seguinte erro de autenticação pode ser exibido:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Se o erro for exibido, altere para o diretório de instalação do aplicativo e execute o `composer update`, que solicita as [chaves de autenticação](../prerequisites/authentication-keys.md).

## Conclua a instalação dos dados de amostra

{{$include /help/_includes/sample-data-complete.md}}
