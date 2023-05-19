---
title: Práticas recomendadas de configuração para indexadores
description: Mantenha e otimize o desempenho do site seguindo as práticas recomendadas para a configuração do indexador.
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Práticas recomendadas para configuração do indexador

Para otimizar e manter o desempenho do site, revise e atualize a configuração do indexador usando as práticas recomendadas de desempenho descritas neste artigo.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Definir indexadores para atualizar de acordo com um agendamento

O Adobe Commerce tem dois tipos de modos indexadores: [!UICONTROL Update on Save] (configuração padrão) e [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** O modo atualiza os índices imediatamente sempre que o catálogo ou outros dados são alterados. Por exemplo, se um usuário administrador adicionar novos produtos a uma categoria, o índice de produtos da categoria será reindexado imediatamente quando a atualização for salva.

- **[!UICONTROL Update on Schedule]** O modo armazena informações sobre atualizações de dados, e as operações de reindexação e atualizações de índice são gerenciadas por um trabalho cron que é executado em segundo plano em intervalos programados.

Ter um grande armazenamento com vários Administradores trabalhando no back-end ou ter muitas importações e exportações aciona atualizações de índice frequentes. Se a configuração do índice do site estiver definida como [!UICONTROL Update on Save] , a reindexação frequente reduz o desempenho do banco de dados, o que torna o desempenho do site lento e causa longos atrasos no processo de reindexação, especialmente para grandes lojas.

Para maximizar o desempenho do site, siga estas práticas recomendadas para indexação:

- Revise a configuração do índice.
- Defina os indexadores como _[!UICONTROL Update on Schedule]_para sites grandes e sites com atualizações frequentes e tráfego intenso. Consulte [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Seguir [práticas recomendadas de desempenho](../../../performance/configuration.md) para gerenciar índices.

>[!IMPORTANT]
>
>A variável [!DNL Customer Grid] só pode ser reindexado usando o [!UICONTROL Update on Save] opção. Este índice não oferece suporte a `Update by Schedule` opção.

## Informações adicionais

- [Gerenciamento de índice para usuários administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gerenciamento de índice usando a CLI do Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Visão geral de indexação para desenvolvedores](https://developer.adobe.com/commerce/php/development/components/indexing/)
