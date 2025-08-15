---
title: Otimizar o desempenho de back-end
description: Saiba como otimizar o desempenho de back-end de sites do Adobe Commerce.
badge: label="Contribuição de objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: d884d434e696a911de626dc76983468556cf451f
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# Práticas recomendadas para otimizar o desempenho de back-end

Este tópico descreve as práticas recomendadas para investigar e otimizar o desempenho de back-end de sites do Adobe Commerce, com foco na otimização e no teste de bancos de dados. Os desenvolvedores podem usar essas informações para investigar o contexto exclusivo de cada projeto do Commerce e identificar oportunidades para otimizar a configuração e as operações de back-end a fim de melhorar o desempenho do site.

>[!NOTE]
>
>As recomendações e os exemplos são inspirados em processos que a objectsource segue em contratos de clientes reais para fornecer sites Adobe Commerce de alto desempenho em escala.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Otimizar o banco de dados para melhorar o desempenho

A otimização do banco de dados é uma maneira segura de aprimorar a experiência do usuário e aumentar as vendas. Ao otimizar o banco de dados, o backbone de um site do Commerce, você pode evitar o desempenho lento do site e eliminar tempos de carregamento longos que criam atrito para os clientes.

### Teste de esforço

Períodos de alto tráfego, como Black Friday, exigem que os sites da Commerce lidem com volumes maciços de tráfego. Em preparação para tais eventos, o teste de esforço é essencial para entender como um site opera sob aumentos exponenciais de carga.

Uma ferramenta que você pode usar para testes de estresse é o GTmetrix. Medir a disponibilidade do local para aumentos de carga configurando o Symmetrix para replicar e multiplicar o comportamento e as ações normais do visitante. Em seguida, execute testes para identificar e resolver problemas que podem afetar o desempenho e a disponibilidade do site durante eventos de compras importantes.

Saiba mais sobre como preparar projetos do Commerce para períodos de alto tráfego:

- [Disponibilidade para feriados](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [Análise de Compras de Feriado](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Aumento da Capacidade de Sobretensão](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Teste de carga

Também é possível usar o GTmetrix ou uma ferramenta semelhante para carregar projetos de teste do Commerce. Como precursor do teste de esforço, o teste de carga é uma prática essencial para sites de grande escala e de alto tráfego. Evite paralisações inesperadas do local, clientes frustrados e perdas financeiras, antecipando e atenuando problemas que afetam o desempenho do local em picos de carga.

Use o GTmetrix para simular tráfego intenso e analisar o desempenho do local para obter informações claras sobre a capacidade do local. Essa análise ajuda a identificar e solucionar gargalos e identificar oportunidades para otimização, garantindo que os sites da Commerce possam operar efetivamente com maior carga.

Saiba mais sobre como testar projetos do Adobe Commerce:

- [Orientação de teste](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) (infraestrutura em nuvem)
- [Teste de aplicativo](https://developer.adobe.com/commerce/testing/guide/)

### Identificar e resolver problemas de desempenho

Solucione problemas de desempenho usando várias ferramentas, como o New Relic e o Observation for Adobe Commerce, para detectar gargalos e otimizar sites do Commerce de maneira eficaz. A [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) está incluída com o Adobe Commerce na infraestrutura em nuvem e a [Observação para Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) está incluída para implantações na nuvem e locais.

Use essas ferramentas para analisar o desempenho do site e identificar problemas de desempenho relacionados a:

- Recursos de uso intensivo do CPU
- Configuração do gerenciamento de cache para consultas e operações de back-end
- Chamadas de API de terceiros
- Cronograma do Cron

Por exemplo, você pode examinar detalhadamente as transações com foco nos detalhes do produto e nas páginas de categoria. Identifique processos demorados que podem ser otimizados para melhorar o desempenho. Em um engajamento de cliente, o objectsource notou um problema de desempenho em uma página de detalhes do produto e encontrou uma chamada de API que estava consumindo 3,5% do tempo de desempenho. Com base nesse resultado, eles examinaram a hierarquia de execução do código para apontar e corrigir o problema que causava o gargalo.

Saiba mais sobre o gerenciamento do desempenho do site:

- [Monitoramento de desempenho](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (infraestrutura em nuvem)
- [Práticas recomendadas de configuração](/help/performance/configuration.md)
- [Observação para Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Otimizar o desempenho do MySQL

Solucionar problemas de desempenho do MySQL implementando a organização por clusters de bancos de dados e a otimização de consultas é uma abordagem eficaz para melhorar o desempenho antes e durante períodos de alto tráfego, como a Black Friday.

#### Implementando o clustering de banco de dados

Sites de alto tráfego geralmente enfrentam gargalos no banco de dados, causados principalmente pela dependência de um único servidor MySQL. Você pode resolver esses gargalos implementando o cluster de banco de dados, uma arquitetura distribuída que melhora o desempenho e garante alta disponibilidade.

O clustering de banco de dados minimiza o impacto de problemas relacionados ao banco de dados durante períodos de pico de tráfego, permitindo que vários nós da Web se conectem a vários servidores MySQL. Use ferramentas como o Cluster Galera para configurar o cluster de banco de dados para sites do Commerce. O Cluster Galera está incluído em [projetos Adobe Commerce implantados na infraestrutura de nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture).

#### Otimização de consultas MySQL

Normalmente, a infraestrutura da maioria dos sites do Adobe Commerce consiste em vários nós da Web conectados a um único servidor MySQL.

Nesta configuração, cada nó da Web front-end se conecta ao Cluster Galera, que permite vários servidores MySQL. O aumento do número de nós da Web front-end pode melhorar o desempenho do aplicativo, mas o único servidor MySQL permanece um gargalo.

Para otimizar o desempenho do servidor MySQL e minimizar os gargalos, é essencial identificar e reduzir consultas desnecessárias. Por exemplo, se você estiver enviando 1.000 consultas por segundo, mas apenas 200 forem necessárias, otimizar e diminuir a contagem de consultas pode melhorar significativamente o desempenho.

Saiba mais sobre como configurar e otimizar o MySQL:

- [Práticas recomendadas para a configuração do banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Replicação lenta para replicação do Galera DB](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Diretrizes gerais do MySQL](/help/installation/prerequisites/database/mysql.md)
- [Cache de consulta do MySQL](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Gerenciar trabalhos cron com eficiência: desempenho e tempo

Os trabalhos do Cron desempenham um papel vital no processamento de tarefas em segundo plano do site, como a geração de relatórios e a indexação de produtos. No entanto, a otimização de tarefas do cron requer uma consideração cuidadosa de seu impacto no desempenho geral. Os desenvolvedores devem avaliar a frequência de agendamento e determinar o tempo ideal com base em requisitos específicos.

Equilibrando desempenho e conveniência, geralmente é aconselhável agendar trabalhos cron durante períodos de tráfego baixo. No entanto, lidar com clientes em diferentes fusos horários pode apresentar desafios, exigindo uma abordagem ponderada para garantir uma experiência harmoniosa em várias regiões geográficas.

Se você for responsável por otimizar o desempenho e o tempo do cron, revise a configuração atual do cron com o administrador do Commerce e saiba mais sobre como configurar trabalhos do cron para projetos do Commerce.

Além disso, é possível usar a Observação para Adobe Commerce para exibir indicadores de desempenho relacionados ao cron. Essa ferramenta combina dados de log de várias fontes para ajudar você a gerenciar melhor o desempenho do site do Adobe Commerce e diagnosticar problemas.

Saiba mais sobre a implementação do Adobe Commerce cron:

- [Cron (tarefas agendadas)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) no _Guia do Usuário do Commerce Admin Systems_
- [Configuração do aplicativo - propriedade crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (infraestrutura em nuvem)
- [Configurar e executar crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (no local)
- [Observação para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (Consulte as guias [!UICONTROL Cron] e [!UICONTROL MySQL].)
