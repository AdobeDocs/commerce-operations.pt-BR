---
title: Limpeza de cache com verniz
description: Saiba como a limpeza de cache funciona com o Vernish e como um acelerador de cache da Web para o aplicativo do Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Limpeza de cache com verniz

Este tópico discute as noções básicas do uso do Varnish como acelerador de cache da Web para o Adobe Commerce e o Magento Open Source.

## Purging de verniz

De acordo [Documentação de verniz](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *limpar* é o que acontece quando você seleciona um objeto do cache e o descarta junto com suas variantes.&quot; Uma limpeza de Verniz é semelhante a um comando de limpeza de cache (ou clique em **Liberar cache de Magento** em Admin).

Na verdade, quando você limpa, limpa ou atualiza o cache do Commerce, o Varnish também é limpo.

Depois de instalar e configurar o Verniz para funcionar com o Commerce, as seguintes ações podem resultar em uma limpeza de Verniz:

- Manutenção de um site.

   Por exemplo, qualquer coisa que você fizer no Administrador do:

   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Geral**
   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Configuração de moeda**
   - **LOJAS** > **Configurações** > **Configuração** > GERAL > **Armazenar endereços de email**

   Quando o Commerce detectar essa alteração, uma mensagem será exibida informando para atualizar o cache.

- Manutenção de uma loja (por exemplo, adição ou edição de categorias, preços, produtos e regras de precificação promocional).

   O verniz é removido automaticamente quando você executa qualquer uma dessas tarefas.

- Mantendo código-fonte.

   Você deve atualizar o cache e também excluir periodicamente tudo no `generated/code` e `generated/metadata` diretórios. Para obter informações sobre como atualizar o cache, consulte a próxima seção.

## Configurar o Commerce para limpar o verniz

O Commerce limpa hosts vernizes depois de configurar hosts vernizes usando o [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

Você pode usar o parâmetro opcional `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts do Vernish e portas de escuta. Configure todos os hosts de verniz, independentemente de você ter um ou vários. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, em que é possível omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Em seguida, você pode expurgar hosts Verniz ao atualizar o cache de Comércio (também conhecido como *limpeza* o cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **[!UICONTROL SYSTEM]** > Ferramentas > **Gerenciamento de cache** e, em seguida, clique em **Liberar cache de Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache usando a linha de comando, você geralmente usa o [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando como [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
