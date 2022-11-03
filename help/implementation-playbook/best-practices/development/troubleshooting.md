---
title: Práticas recomendadas de solução de problemas
description: Saiba como solucionar problemas de implementação do Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Práticas recomendadas de solução de problemas

Siga essas práticas recomendadas para obter uma solução de problemas eficaz do Adobe Commerce em problemas de infraestrutura em nuvem.

## Produtos e versões afetados

Adobe Commerce na infraestrutura de nuvem

## Práticas recomendadas

| Tipo de problema | Práticas recomendadas | Recurso |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemas de implantação | **Siga as práticas recomendadas de implantação.** 13% dos tíquetes de suporte envolvem problemas de implantação. As práticas recomendadas foram atualizadas para incluir maneiras de evitar muitas dessas causas. | [Práticas recomendadas para criações e implantação](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) na documentação do desenvolvedor. |
| Problemas de inatividade do site | **Use a Solução de problemas do Site Down.** Os Crons podem estar longe e podem se superar. Elas são a fonte de muitas paralisações e problemas de desempenho. | [Solução de problemas do Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) e [Como redefinir trabalhos do cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) na nossa base de conhecimento de apoio. |
| Problemas de desempenho | **Se você não estiver usando o banner do Adobe Commerce, desative-o.** Quando o banner é ativado, mas não é usado, os recursos são usados para fazer pesquisas no banco de dados quando não são necessárias e isso causará problemas de desempenho. | [Desative a saída do Adobe Commerce Banner para melhorar o desempenho](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html em nossa base de conhecimento de suporte. |
| Pesquisar problemas | **O mecanismo de pesquisa do catálogo MySQL foi removido no Adobe Commerce 2.4.0.** Você deve ter a configuração do host do Elasticsearch e configurada antes de instalar a versão 2.4.0. Consulte Instalar e configurar o Elasticsearch na documentação do desenvolvedor. | [Configurar o serviço Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) na documentação do desenvolvedor. |
| Erros personalizados | **Não implante durante os horários de pico.** Adicionar e remover usuários acionará uma implantação. | [Implantação de tempo de inatividade zero](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) na documentação do desenvolvedor. |
| Erros e problemas do banco de dados | **Os problemas do banco de dados causam situações de implantação (problemas pós-gancho), desempenho e inatividade do site.** Muitos envolvem erros ou alocação insuficiente do espaço do banco de dados. | [Códigos de erro do MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Gerenciar espaço de armazenamento](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (incluindo banco de dados) na documentação do desenvolvedor. |
| Problemas de configuração | **Indexar por Agendamento em vez de Índice em Salvar.** Essa é a configuração de indexação mais eficiente. O índice em Salvar causará a reindexação completa. | [Configurar indexadores](../../../configuration/cli/manage-indexers.md#configure-indexers) na documentação do desenvolvedor. |
| Problemas de código personalizado | **Verifique seus logs de consulta lentos quanto a oportunidades para identificar e possivelmente interromper processos demorando muito tempo para serem concluídos.** Consultas lentas podem causar bloqueios no banco de dados, resultando em problemas de desempenho e de detalhamento do site. | [Verificando consultas e processos lentos demorando muito no MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemas de extensão | **Use somente extensões verificadas atualmente no Commerce Marketplace.** | [Extensões para o Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemas de recursos | **Monitore a memória e o espaço disponíveis e otimize o armazenamento.** Você pode ter espaço disponível antes de uma ação que consome recursos significativos (implantação, por exemplo). A baixa otimização do armazenamento de arquivos (muitas imagens grandes e ricas, por exemplo) também pode contribuir para o espaço insuficiente. Os recursos baixos causam problemas de desempenho, site inativo, implantações travadas e falhas de implantação. | [Gerenciar espaço em disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) na documentação do desenvolvedor; [Armazenamento de arquivos baixo/esgotado, cargas de página específicas são lentas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) na nossa base de conhecimento de apoio. |
