---
title: Etapas de migração pós-dados
description: Saiba quais etapas seguir depois de usar o [!DNL Data Migration Tool] para migrar dados da Magento 1 para a Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%
---
# Etapas de migração pós-dados

Depois de concluir sua migração e testar completamente seu novo site Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todas as atividades de administrador

* Iniciar trabalhos do Magento 2 cron

* [Liberar todos os tipos de cache do Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos os indexadores do Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Altere o DNS e os balanceadores de carga para apontar para o hardware de produção do Magento 2
