---
title: Métricas de suporte
description: Monitore os esforços de suporte e manutenção da implementação do Adobe Commerce usando métricas comuns.
exl-id: a8171a08-3583-4c6a-bb18-158161be42d1
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Métricas de suporte

O diagrama a seguir mostra métricas/KPIs típicos coletados e relatados para funções L1:

![Diagrama mostrando as métricas de SLA](../../assets/playbooks/sla-metrics.svg)

A medição e a emissão de relatórios dos serviços L2 (melhorias e serviços opcionais) são semelhantes aos projetos de desenvolvimento. O desempenho e o progresso das equipes L2 são medidos por métricas como velocidade, qualidade de código, eficácia de teste e produtividade.

| Medição de desempenho principal | Unidade de medida | Métricas relatadas |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| Velocity | Número | Não. dos pontos da história que a equipe conseguiu entregar para a primavera |
| Eficiência de Compromisso do Sprint | Porcentagem | Número total de pontos de história comprometidos vs entregues para um Sprint |
| Superexposição de Sprint | Número | Gráfico (Relatório, rastreia a conclusão do trabalho em toda a etapa) |
| Qualidade do código | Números, Porcentagem | Complexidade, LoC, Violações, Cobertura de código para impressão |
| Volatilidade do requisito | Número | Número de requisitos alteração/número total de requisitos para a fonte |
| Densidade de Defeito | Porcentagem | [Não. de defeitos válidos encontrados/Total n.o .of Casos de teste executados]*100 para a impressão |
| Eficácia do teste | Porcentagem | [Defeitos válidos levantados/(Defeitos válidos levantados + defeitos rejeitados)]*100 para a impressão |
| Produtividade | Número (tendência) | Pontos de história fornecidos por fonte/capacidade |
