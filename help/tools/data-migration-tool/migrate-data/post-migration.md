---
title: Etapas de migração pós-dados
description: Saiba quais etapas seguir após usar o [!DNL Data Migration Tool] para migrar dados do Magento 1 para o Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Etapas de migração pós-dados

Após concluir sua migração e testar completamente seu novo site Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todas as atividades de Administrador

* Iniciar processos de cron do Magento 2

* [Liberar todos os tipos de cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos os indexadores do Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Altere o DNS e os balanceadores de carga para apontar para o hardware de produção do Magento 2
