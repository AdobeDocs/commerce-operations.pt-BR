---
title: Práticas recomendadas de configuração para indexadores
description: Mantenha e otimize o desempenho do site seguindo as práticas recomendadas para a configuração do indexador.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Práticas recomendadas para a configuração do indexador

Para otimizar e manter o desempenho do site, revise e atualize a configuração do indexador usando as práticas recomendadas de desempenho descritas neste artigo.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Definir indexadores para atualizar de acordo com uma programação

O Adobe Commerce tem dois tipos de modos de indexador: [!UICONTROL Update on Save] (configuração padrão) e [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** O modo atualiza os índices imediatamente sempre que o catálogo ou outros dados são alterados. Por exemplo, se um usuário administrador adicionar novos produtos a uma categoria, o índice de produtos da categoria será reindexado imediatamente quando a atualização for salva.

- **[!UICONTROL Update on Schedule]** O modo armazena informações sobre atualizações de dados, e as operações de reindexação e atualizações de índice são gerenciadas por um trabalho cron que é executado em segundo plano em intervalos agendados.

Ter uma grande loja com vários administradores trabalhando no backend ou ter muitas importações e exportações aciona atualizações de índice frequentes. Se a configuração do índice do site estiver definida como [!UICONTROL Update on Save] o modo , a reindexação frequente degrada o desempenho do banco de dados, o que retarda o desempenho do site e causa longos atrasos no processo de reindexação, especialmente para grandes lojas.

Para maximizar o desempenho do site, siga estas práticas recomendadas para indexação:

- Revise a configuração do índice.
- Defina os indexadores como _[!UICONTROL Update on Schedule]_para sites grandes e sites com atualizações frequentes e tráfego pesado. Consulte [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Seguir [práticas recomendadas de desempenho](../../../performance/configuration.md) para gerenciar índices.

## Informações adicionais

- [Gerenciamento de índice para usuários administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gerenciamento de índice usando a CLI do Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Visão geral de indexação para desenvolvedores](https://developer.adobe.com/commerce/php/development/components/indexing/)
