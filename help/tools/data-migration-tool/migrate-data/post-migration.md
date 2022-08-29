---
title: Etapas da migração pós-dados
description: Saiba quais etapas seguir o uso da variável [!DNL Data Migration Tool] para migrar dados do Magento 1 para o Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Etapas da migração pós-dados

Depois de concluir a migração e testar completamente seu novo site do Magento 2, execute as seguintes tarefas:

* Coloque o Magento 1 no modo de manutenção e pare permanentemente todos [Administrador](https://glossary.magento.com/admin) atividades

* Inicie trabalhos do Magento 2 cron

* [Limpar todos os tipos de cache Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [Reindexe todos os indexadores Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* Altere o DNS e balanceadores de carga para apontar para o hardware de produção do Magento 2
