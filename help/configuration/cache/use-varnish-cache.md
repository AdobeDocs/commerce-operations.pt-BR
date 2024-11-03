---
title: Limpeza de cache com verniz
description: Saiba como a limpeza de cache funciona com o Vernish e como um acelerador de cache da Web para o aplicativo do Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Limpeza de cache com verniz

Este tópico discute as noções básicas do uso do Varnish como acelerador de cache da Web para o Adobe Commerce.

## Purging de verniz

De acordo com a [Documentação de verniz](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;Uma *limpeza* é o que acontece quando você seleciona um objeto do cache e o descarta junto com suas variantes.&quot; Uma limpeza de verniz é semelhante a um comando de limpeza de cache (ou ao clicar em **Limpar cache de Magento** no Administrador).

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

O Commerce limpa hosts do Varnish depois que você configura hosts do Varnish usando o comando [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

Você pode usar o parâmetro opcional `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts vernizes e portas de escuta. Configure todos os hosts de verniz, independentemente de você ter um ou vários. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde você pode omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Você pode limpar hosts do Varnish ao atualizar o cache do Commerce (também conhecido como *limpeza* do cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **[!UICONTROL SYSTEM]** > Ferramentas > **Gerenciamento de Cache** e em **Liberar Cache de Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache usando a linha de comando, você geralmente usa o comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
