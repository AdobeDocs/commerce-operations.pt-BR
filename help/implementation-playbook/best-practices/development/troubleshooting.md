---
title: Práticas recomendadas de solução de problemas
description: Saiba como solucionar problemas de implementação do Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Práticas recomendadas de solução de problemas

Siga estas práticas recomendadas para obter uma solução eficaz de problemas do Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem

## Práticas recomendadas

| Tipo de problema | Práticas recomendadas | Recurso |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemas de implantação | **Siga as práticas recomendadas de implantação.** 13% dos tíquetes de suporte envolvem problemas de implantação. As práticas recomendadas foram atualizadas para incluir maneiras de evitar muitas dessas causas. | [Práticas recomendadas para builds e implantação](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) na documentação do desenvolvedor. |
| Problemas de inatividade do site | **Use a Solução de problemas do site para baixo.** Crons podem ser de longa duração e podem ultrapassar um ao outro. Elas são a origem de muitas paralisações e problemas de desempenho. | [Solução de problemas de site inativo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) e [Como redefinir trabalhos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) em nossa base de conhecimento de suporte. |
| Problemas de desempenho | **Se você não estiver usando o banner do Adobe Commerce, desative-o.** Quando o banner é ativado, mas não usado, os recursos são usados para fazer pesquisas no banco de dados quando não são necessários e causará problemas de desempenho. | [Desative a saída do banner do Adobe Commerce para melhorar o desempenho](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) em nossa base de conhecimento de suporte. |
| Pesquisar problemas | **O mecanismo de pesquisa do catálogo MySQL foi removido no Adobe Commerce 2.4.0.** Você deve ter o Elasticsearch host configurado antes de instalar a versão 2.4.0. Consulte Instalar e configurar o Elasticsearch na documentação do desenvolvedor. | [Configurar serviço Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) na documentação do desenvolvedor. |
| Erros personalizados | **Não implante em horários de pico.** Adicionar e remover usuários acionará uma implantação. | [Implantação sem tempo de inatividade](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) na documentação do desenvolvedor. |
| Erros e problemas do banco de dados | **Problemas de banco de dados causam implantação (problemas pós-gancho), desempenho e situações de inatividade do site.** Muitas envolvem erros ou alocação insuficiente de espaço no banco de dados. | [Códigos de erro do MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Gerenciar espaço de armazenamento](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (incluindo o banco de dados do ) em nossa documentação do desenvolvedor. |
| Problemas de configuração | **Indexar por agendamento em vez de indexar ao salvar.** Essa é a configuração de indexação mais eficiente. O índice ao salvar causará a reindexação completa. | [Configurar indexadores](../../../configuration/cli/manage-indexers.md#configure-indexers) na documentação do desenvolvedor. |
| Problemas de código personalizado | **Verifique seus logs de consulta lenta em busca de oportunidades para identificar e possivelmente eliminar processos que demoram muito para serem concluídos.** Consultas lentas podem causar bloqueios no banco de dados, resultando em interrupções no site e problemas de desempenho. | [Verificação de consultas e processos lentos que demoram muito no MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemas de extensão | **Use somente as extensões verificadas atualmente no Commerce Marketplace.** | [Extensões para o Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemas de recursos | **Monitore a memória e o espaço disponíveis e otimize o armazenamento.** Você pode ter espaço disponível antes de uma ação que consome recursos significativos (implantação, por exemplo). A otimização deficiente do armazenamento de arquivos (muitas imagens grandes e ricas, por exemplo) também pode contribuir para a insuficiência de espaço. Recursos baixos causam problemas de desempenho, sites inativos, implantações paralisadas e falhas de implantação. | [Gerenciar espaço em disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) na documentação do desenvolvedor; [Armazenamento de arquivos baixo/esgotado, cargas de página específicas são lentas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) em nossa base de conhecimento de suporte. |
