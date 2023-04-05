---
title: Etapas da migração pós-dados
description: Saiba quais etapas seguir o uso da variável [!DNL Data Migration Tool] para migrar dados do Magento 1 para o Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Etapas da migração pós-dados

Depois de concluir a migração e testar completamente seu novo site do Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todas as atividades de Administração

* Inicie trabalhos do Magento 2 cron

* [Limpar todos os tipos de cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexe todos os indexadores Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Altere o DNS e balanceadores de carga para apontar para o hardware de produção do Magento 2
