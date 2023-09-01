---
title: Fase de manutenção da implementação
description: Saiba mais sobre as práticas recomendadas de implementação para a fase de manutenção de projetos do Adobe Commerce.
exl-id: bd052412-a41c-4dbd-9aba-ba2fcac31f2d
feature: Best Practices
source-git-commit: aad06c1c2def87a319426860b47b8e5ff5e96780
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Fase de manutenção

A fase de manutenção inclui as seguintes atividades:

- Correção de erros
- Gerenciamento de catálogo
- Configuração
- Aprimoramentos de recursos
- Indexação
- Managed Services
- Monitoramento do site
- Atualizações

As seções a seguir incluem informações de práticas recomendadas para a fase de manutenção.

## Correções de erros

| Prática recomendada | Descrição |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [[!DNL Quality Patches Tool] uso](../../../tools/quality-patches-tool/usage.md) | Aplique, reverta e exiba informações gerais sobre todos os patches do Adobe Commerce. |

## Gerenciamento de catálogo

| Prática recomendada | Descrição |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [Gerenciamento do catálogo de produtos](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/2eea2782fc874047a020391000519f8b/watch?source=CHANNEL) | Gravação de comércio e café que descreve estratégias para gerenciar catálogos de produtos. |

## Configuração

| Prática recomendada | Descrição |
|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| [Agendando atualizações de administrador em sites de produção](scheduling-admin-updates-in-production.md) | Gerencie atualizações críticas do Adobe Commerce para evitar desempenho lento e paralisações. |

## Gerenciamento de banco de dados

| Prática recomendada | Descrição |
|----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Resolver problemas de desempenho do banco de dados&#x200B;](resolve-database-performance-issues.md) | Correção de problemas de banco de dados que retardam o desempenho em sites Adobe Commerce implantados na infraestrutura em nuvem. |
| [Pré-requisitos de atualização do Adobe Commerce 2.3.5 para MariaDB&#x200B;](commerce-235-upgrade-prerequisites-mariadb.md) | Prepare seu banco de dados MariaDB para uma atualização. |

## Aprimoramentos de recursos

| Prática recomendada | Descrição |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| [Personalização](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/e218545a77de490fb5102eca07d0580a/watch?source=CHANNEL) | Gravação de comércio e café que descreve estratégias de personalização. |
| [Tendências do comércio eletrônico](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/9a772468d7b64409a3d5dff4d67e656d/watch?source=CHANNEL) | Gravação de comércio e café que descreve as tendências do comércio eletrônico. |
| [Automação de IA](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/27ae23699c2847be981a23ca098e548f/watch?source=CHANNEL) | Gravação de comércio e café que descreve possibilidades de personalização com inteligência artificial e automação. |

## Indexação

| Prática recomendada | Descrição |
|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Como reindexar](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) | Use trabalhos cron ou a ferramenta CLI para executar a reindexação. |
| [Configurar indexadores&#x200B;](indexer-configuration.md) | Otimize o desempenho do site seguindo as práticas recomendadas para a configuração do indexador. |
| [Processamento do pedido](order-processing-configuration.md) | Melhore o desempenho do processamento de pedidos e check-out. |

## Monitoramento do site

| Prática recomendada | Descrição |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Auditoria de desempenho de front-end](frontend-performance.md) | Identificar e solucionar problemas que afetam negativamente o desempenho do site usando ferramentas de desempenho da Web. |
| [Pronto, Definir, Manter](https://business.adobe.com/blog/basics/ready-set-maintain) | Dicas para manter seus sites do Adobe Commerce a fim de maximizar o valor comercial e o tempo de atividade. |
| [Use o [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Veja insights importantes sobre seu site do Adobe Commerce em um só lugar. |
| [Monitorar desempenho, espaço em disco e registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) | Use o New Relic para monitorar os principais insights de desempenho sobre o seu Adobe Commerce no site de infraestrutura em nuvem. |

### Atualizações

| Prática recomendada | Descrição |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [Patches em escala](patching-at-scale.md) | Saiba como o patch centralizado para o Adobe Commerce pode ajudar você a gerenciar projetos empresariais. |
| [Atualizar serviços e componentes para a versão mais recente&#x200B;](update-services.md) | mantenha sua pilha de tecnologia Adobe Commerce on cloud infrastructure atualizada. |
| [Lista de verificação de atualização do Adobe Commerce&#x200B;](upgrade-checklist.md) | Crie e use uma lista de verificação de atualização para planejar sua estratégia de atualização do Adobe Commerce. |
