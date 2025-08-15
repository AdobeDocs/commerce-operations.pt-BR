---
title: Etapas de migração pós-dados
description: Saiba quais etapas seguir depois de usar o [!DNL Data Migration Tool]  para migrar dados do Magento 1 para o Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Etapas de migração pós-dados

Após concluir sua migração e testar completamente seu novo site do Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todas as atividades de administrador

* Iniciar trabalhos cron do Magento 2

* [Limpar todos os tipos de cache do Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos os indexadores do Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Altere o DNS e os balanceadores de carga para apontar para o hardware de produção do Magento 2
