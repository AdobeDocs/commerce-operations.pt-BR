---
title: Limpeza de cache com várias instâncias de verniz
description: Saiba como a limpeza do cache funciona com várias instâncias de Verniz.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Cache limpando várias instâncias de Verniz

O Adobe Commerce oferece suporte a várias instâncias de verniz prontas para uso.

Este tópico mostra as noções básicas para configurar várias instâncias de Verniz com o Commerce.

## Configuração para limpar várias instâncias de verniz

O Commerce limpa hosts do Varnish depois que você configura hosts do Varnish usando o comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Você deve usar o parâmetro `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts vernizes e portas de escuta. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde você pode omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Você pode limpar todos os hosts do Varnish ao atualizar o cache do Commerce (também conhecido como _limpeza_ do cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **SISTEMA** > Ferramentas > **Gerenciamento de Cache** e em **Liberar Cache de Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache de várias instâncias do Varnish da cli, use o comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
