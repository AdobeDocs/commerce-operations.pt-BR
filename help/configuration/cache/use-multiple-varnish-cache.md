---
title: Limpeza de cache com várias instâncias de verniz
description: Saiba como a limpeza do cache funciona com várias instâncias de Verniz no Adobe Commerce. Descubra as práticas recomendadas de configuração e gerenciamento.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 0%

---

# Limpeza de cache com várias instâncias de verniz

O Adobe Commerce oferece suporte a várias instâncias de verniz prontas para uso.

Este tópico mostra as noções básicas para configurar várias instâncias de Verniz com o Commerce.

{{varnish-config-cloud}}

## Configuração para limpar várias instâncias de verniz

O Commerce limpa hosts do Varnish depois que você configura hosts do Varnish usando o comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Você deve usar o parâmetro `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts vernizes e portas de escuta. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde você pode omitir `<listen port>` se for a porta 80.

Por exemplo,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Você pode limpar todos os hosts do Varnish ao atualizar o cache do Commerce (também conhecido como _limpeza_ do cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **SISTEMA** > Ferramentas > **Gerenciamento de Cache** e em **Limpar Cache do Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache de várias instâncias do Varnish da cli, use o comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
