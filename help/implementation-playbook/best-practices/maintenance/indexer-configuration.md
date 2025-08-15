---
title: Práticas recomendadas de configuração para indexadores
description: Mantenha e otimize o desempenho do site seguindo as práticas recomendadas para a configuração do indexador.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
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
- Defina os indexadores como _[!UICONTROL Update on Schedule]_&#x200B;para sites grandes e sites com atualizações frequentes e tráfego intenso. Consulte [Gerenciamento de Índice](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Siga as [práticas recomendadas de desempenho](../../../performance/configuration.md) para gerenciar índices.

>[!IMPORTANT]
>
>O comportamento do indexador [!DNL Customer Grid] foi alterado na versão 2.4.8:
>
>- **Anterior a 2.4.8**: o indexador [!DNL Customer Grid] só pode ser reindexado usando a opção [!UICONTROL Update on Save] e não oferece suporte à opção [!UICONTROL Update by Schedule].
>- **2.4.8 e posterior**: o indexador [!DNL Customer Grid] oferece suporte aos modos [!UICONTROL Update on Save] e [!UICONTROL Update by Schedule] e o padrão é [!UICONTROL Update by Schedule].

## Informações adicionais

- [Gerenciamento de índice para usuários administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gerenciamento de Índice usando a CLI do Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=pt-BR)
- [Visão geral da indexação para desenvolvedores](https://developer.adobe.com/commerce/php/development/components/indexing/)
