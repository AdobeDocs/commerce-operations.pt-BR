---
title: 'Alertas gerenciados no Adobe Commerce: alertas do MariaDB'
description: Este artigo fornece etapas de solução de problemas quando você recebe alertas MariaDB para Adobe Commerce no [!DNL New Relic]. Os alertas do MariaDB monitoram a alta carga de consultas, bem como o excesso de consultas DML (Data Manipulation Language). Ambos podem levar a uma experiência degradada do usuário ou até mesmo a um tempo de inatividade. Você pode receber dois tipos de alertas.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: ccf8b7c5ad1fbef2cfba05f65f05ab8af0375b4c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Alertas gerenciados no Adobe Commerce: alertas do MariaDB

Este artigo fornece etapas de solução de problemas quando você recebe alertas MariaDB para Adobe Commerce em [!DNL New Relic]. Os alertas do MariaDB monitoram a alta carga de consultas, bem como o excesso de consultas DML (Data Manipulation Language). Ambos podem levar a uma experiência degradada do usuário ou até mesmo a um tempo de inatividade. Você pode receber dois tipos de alertas:

* Aviso de Consultas DML
* Consultas DML Críticas

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta gerenciado em [!DNL New Relic] se tiver assinado [Alertas gerenciados para Adobe Commerce](managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

**Fazer!**

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) no Guia de Instalação do Commerce. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Encerre todos os scripts, como importações, que podem ser a causa do alerta se o desempenho do site for afetado.

**Não!**

* Execute indexadores ou crons adicionais que podem causar stress adicional no MariaDB.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

## Solução

**Consultas DML (consultas que modificam o banco de dados usando UPDATE, INSERT e DELETE)**

Se você receber um alerta Crítico de Consultas DML, comece na etapa um. Se você receber um alerta de Aviso de Consultas DML, comece na etapa dois.

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para ver as etapas, consulte nossa base de dados de conhecimento [Rastrear seus tíquetes de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). O suporte pode ter recebido um alerta de limite [!DNL New Relic], criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do Contato: selecione **[!UICONTROL New Relic MariaDB alert received]**.
   * Descrição do alerta.
   * [[!DNL New Relic] Link de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Para identificar a origem do problema, tente identificar as consultas DML:
   1. Revise suas operações de banco de dados usando etapas da [página Bancos de Dados](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) do New Relic.
   1. Classificar por **[!UICONTROL CALL COUNT]**, depois **[!UICONTROL OPERATION]**. Revise as operações `INSERT`, `DELETE` e `UPDATE`.
   1. Procure por AVG alta.
   1. Clique em para localizar chamadores de operação de banco de dados. Isso identificará as transações usando essa consulta por tempo.
   1. Procure otimizações de código ou otimizações operacionais:
      * Otimizações de código: procure otimizar consultas com inserções/atualizações em massa, minimizando o uso de índice ou limitando o código.
      * Otimizações operacionais: descarregamento de modificações de dados que consomem muitos recursos para diminuir os tempos de tráfego.
      * Otimizações adicionais: certifique-se de que você está na versão mais recente de ECE-Tools. Para ver as etapas, consulte [Atualizar versão das ferramentas ece](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) no Guia do Commerce na Nuvem.
