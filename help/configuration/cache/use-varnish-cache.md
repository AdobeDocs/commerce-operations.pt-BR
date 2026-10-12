---
title: Limpeza de cache com verniz
description: Saiba como a limpeza de cache funciona com o acelerador de cache da Web do Varnish para Adobe Commerce. Descubra as técnicas de otimização e gerenciamento de cache.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '392'
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

O Commerce limpa hosts do Varnish depois que você configura hosts do Varnish usando o comando [`magento setup:config:set`](/help/tools/reference/commerce-on-premises.md#setupconfigset).

Você pode usar o parâmetro opcional `--http-cache-hosts` para especificar uma lista separada por vírgulas de hosts vernizes e portas de escuta. Configure todos os hosts de verniz, independentemente de você ter um ou vários. (Não separe hosts com um caractere de espaço.)

O formato do parâmetro deve ser `<hostname or ip>:<listen port>`, onde você pode omitir `<listen port>` se for a porta 80.

Por exemplo,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Você pode limpar hosts do Varnish ao atualizar o cache do Commerce (também conhecido como *limpeza* do cache) no Admin ou usando a linha de comando.

Para atualizar o cache usando o Administrador, clique em **[!UICONTROL SYSTEM]** > Ferramentas > **Gerenciamento de Cache** e em **Limpar Cache do Magento** na parte superior da página. (Você também pode atualizar tipos de cache individuais.)

Para atualizar o cache usando a linha de comando, você geralmente usa o comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
