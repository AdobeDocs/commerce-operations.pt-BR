---
title: Limpeza de cache com verniz
description: Saiba como a limpeza de cache funciona com o acelerador de cache da Web do Varnish para Adobe Commerce. Descubra as técnicas de otimização e gerenciamento de cache.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 405
ht-degree: 0%

---

# Limpeza de cache com verniz

Este tópico discute as noções básicas do uso do Varnish como acelerador de cache da Web para o Adobe Commerce.

{{varnish-config-cloud}}

## Purging de verniz

De acordo com a [Documentação de verniz](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;Uma *limpeza* é o que acontece quando você seleciona um objeto do cache e o descarta junto com suas variantes.&quot; Uma limpeza de verniz é semelhante a um comando de limpeza de cache (ou ao clicar em **Limpar cache do Magento** no Administrador).

Na verdade, ao limpar, liberar ou atualizar o cache do Commerce, o Varnish também é limpo.

Depois de instalar e configurar o Verniz para funcionar com o Commerce, as seguintes ações podem resultar em uma limpeza de Verniz:

- Manutenção de um site.

  Por exemplo, qualquer coisa que você fizer no Administrador do:

   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Geral**
   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Configuração de Moeda**
   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Armazenar Endereços de Email**

  Quando o Commerce detecta essa alteração, uma mensagem é exibida informando que você atualize o cache.

- Manutenção de uma loja (por exemplo, adição ou edição de categorias, preços, produtos e regras de precificação promocional).

  O verniz é removido automaticamente quando você executa qualquer uma dessas tarefas.

- Mantendo código-fonte.

  Você deve atualizar o cache e também excluir periodicamente tudo nos diretórios `generated/code` e `generated/metadata`. Para obter informações sobre como atualizar o cache, consulte a próxima seção.

## Configurar o Commerce para limpar o verniz

O Commerce limpa hosts do Varnish depois que você configura hosts do Varnish usando o comando [`magento setup:config:set`](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

Você pode usar o parâmetro opcional `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts vernizes e portas de escuta. Configure todos os hosts de verniz, independentemente de você ter um ou vários. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde você pode omitir `<listen port>` se for a porta 80.

Por exemplo,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Você pode limpar hosts do Varnish ao atualizar o cache do Commerce (também conhecido como *limpeza* do cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **[!UICONTROL SYSTEM]** > Ferramentas > **Gerenciamento de Cache** e em **Limpar Cache do Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache usando a linha de comando, você geralmente usa o comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
