---
title: Práticas recomendadas de configuração para indexadores
description: Mantenha e otimize o desempenho do site seguindo as práticas recomendadas para a configuração do indexador.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 153cf3bae74a78d7a41176e0216203d354d2513b
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Práticas recomendadas para configuração do indexador

Para otimizar e manter o desempenho do site, revise e atualize a configuração do indexador usando as práticas recomendadas de desempenho descritas neste artigo.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Definir indexadores para atualizar de acordo com um agendamento

O Adobe Commerce tem dois tipos de modos indexadores: [!UICONTROL Update on Save] e [!DNL Update on Schedule].

- O modo **[!UICONTROL Update on Save]** atualiza os índices imediatamente sempre que o catálogo ou outros dados são alterados. Por exemplo, se um usuário administrador adicionar novos produtos a uma categoria, o índice de produtos da categoria será reindexado imediatamente quando a atualização for salva.

- O modo **[!UICONTROL Update on Schedule]** armazena informações sobre atualizações de dados, e as operações de reindexação e atualizações de índice são gerenciadas por um trabalho cron que é executado em segundo plano em intervalos agendados. O trabalho cron nem sempre executa uma reindexação toda vez que é executado. Ele reindexa somente quando há novas entradas nos logs de alteração do indexador (por exemplo, há um backlog nos indexadores).

Ter um grande armazenamento com vários Administradores trabalhando no back-end ou ter muitas importações e exportações aciona atualizações de índice frequentes. Se a configuração do índice do site estiver definida para o modo [!UICONTROL Update on Save], a reindexação frequente prejudicará o desempenho do banco de dados, o que atrasará o desempenho do site e causará longos atrasos no processo de reindexação, especialmente em grandes lojas.

Para maximizar o desempenho do site, siga estas práticas recomendadas para indexação:

- Revise a configuração do índice.
- Defina os indexadores como _[!UICONTROL Update on Schedule]_para sites grandes e sites com atualizações frequentes e tráfego intenso. Consulte [Gerenciamento de Índice](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Siga as [práticas recomendadas de desempenho](../../../performance/configuration.md) para gerenciar índices.

>[!IMPORTANT]
>
>O [!DNL Customer Grid] só pode ser reindexado usando a opção [!UICONTROL Update on Save]. Este índice não dá suporte à opção `Update by Schedule`.

## Informações adicionais

- [Gerenciamento de índice para usuários administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gerenciamento de índice usando a CLI do Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Visão geral da indexação para desenvolvedores](https://developer.adobe.com/commerce/php/development/components/indexing/)
