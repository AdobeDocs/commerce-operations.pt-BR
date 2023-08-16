---
title: Limpeza de cache com várias instâncias de verniz
description: Saiba como a limpeza do cache funciona com várias instâncias de Verniz.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Cache limpando várias instâncias de Verniz

O Adobe Commerce e o Magento Open Source oferecem suporte a várias instâncias de verniz prontas para uso.

Este tópico mostra as noções básicas para configurar várias instâncias de Verniz com o Commerce.

## Configuração para limpar várias instâncias de verniz

O Commerce limpa hosts vernizes depois de configurar hosts vernizes usando o [`magento setup:config:set`](../../installation/tutorials/deployment.md) comando.

Você deve usar o `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts do Vernish e portas de escuta. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, em que é possível omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Em seguida, você pode limpar todos os hosts de verniz ao atualizar o cache de comércio (também conhecido como _limpeza_ o cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **SISTEMA** > Ferramentas > **Gerenciamento de cache** e, em seguida, clique em **Liberar cache de Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache de várias instâncias do Varnish a partir da cli, use o [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando como [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
