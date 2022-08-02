---
title: Limpeza de cache com várias instâncias do Varnish
description: Saiba como a limpeza de cache funciona com várias instâncias do Varnish.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Limpeza de cache em várias instâncias do Varnish

O Adobe Commerce e o Magento Open Source oferecem suporte para várias instâncias de Varnish prontas para uso.

Este tópico mostra as noções básicas para configurar várias instâncias de Varnish com o Commerce.

## Configuração para limpar várias instâncias do Varnish

O Commerce limpa hosts Varnish depois que você configura hosts Varnish usando o [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) comando.

Você deve usar o `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts Varnish e portas de escuta. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde é possível omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Você pode limpar todos os hosts Varnish ao atualizar o cache do Commerce (também conhecido como _limpeza_ o cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **SISTEMA** > Ferramentas > **Gerenciamento de cache**, depois clique em **Liberar cache Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache de várias instâncias do Varnish da cli, use o [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando como [proprietário do sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
