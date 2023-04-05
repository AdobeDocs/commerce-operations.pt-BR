---
title: Limpeza de cache com Varnish
description: Saiba como a limpeza de cache funciona com a Varnish e como usá-la como um acelerador de cache da Web para o aplicativo Adobe Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Limpeza de cache com Varnish

Este tópico discute as noções básicas do uso da Varnish como acelerador de armazenamento em cache na Web para Adobe Commerce e Magento Open Source.

## Limpeza variável

De acordo com [Documentação variada](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *limpeza* é o que acontece quando você escolhe um objeto do cache e o descarta junto com suas variantes.&quot; Uma limpeza Varna é semelhante a um comando de limpeza de cache (ou ao clicar em **Liberar cache Magento** em Admin).

Na verdade, ao limpar, liberar ou atualizar o cache do Commerce, o Varnish também é eliminado.

Depois de ter instalado e configurado o Varnish para funcionar com o Commerce, as seguintes ações podem resultar em uma limpeza Varnish :

- Manutenção de um site.

   Por exemplo, qualquer coisa que você faça no Administrador em:

   - **ARMAZENAMENTOS** > **Configurações** > **Configuração** > GERAL > **Geral**
   - **ARMAZENAMENTOS** > **Configurações** > **Configuração** > GERAL > **Configuração de moeda**
   - **ARMAZENAMENTOS** > **Configurações** > **Configuração** > GERAL > **Armazenar endereços de email**

   Quando o Commerce detecta essa alteração, uma mensagem é exibida, informando-o para atualizar o cache.

- Manutenção de uma loja (por exemplo, adição ou edição de categorias, preços, produtos e regras de preços promocionais).

   A Varnish é removida automaticamente ao executar qualquer uma dessas tarefas.

- Manutenção do código-fonte.

   Você deve atualizar o cache e também excluir periodicamente tudo no `generated/code` e `generated/metadata` diretórios. Para obter informações sobre como atualizar o cache, consulte a próxima seção.

## Configurar o Commerce para limpar o Varnish

O Commerce limpa hosts Varnish depois que você configura hosts Varnish usando o [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

Você pode usar o parâmetro opcional `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts Varnish e portas de escuta. Configure todos os hosts Varnish, caso tenha um ou vários. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde é possível omitir `<listen port>` se for a porta 80.

Por exemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Você pode, então, limpar hosts Varnish ao atualizar o cache do Commerce (também conhecido como *limpeza* o cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **[!UICONTROL SYSTEM]** > Ferramentas > **Gerenciamento de cache**, depois clique em **Liberar cache Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache usando a linha de comando, normalmente use o [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando como [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
