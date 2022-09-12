---
title: Etapas da migração pós-dados
description: Saiba quais etapas seguir o uso da variável [!DNL Data Migration Tool] para migrar dados do Magento 1 para o Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Etapas da migração pós-dados

Depois de concluir a migração e testar completamente seu novo site do Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todos [Administrador](https://glossary.magento.com/admin) atividades

* Inicie trabalhos do Magento 2 cron

* [Limpar todos os tipos de cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexe todos os indexadores Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Altere o DNS e balanceadores de carga para apontar para o hardware de produção do Magento 2
