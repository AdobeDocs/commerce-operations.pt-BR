---
title: Governança do projeto
description: Aplique nossas recomendações de governança de projeto à implementação do Adobe Commerce.
exl-id: adf53a2a-1673-441a-84d3-4cdda47d6aa5
feature: Best Practices
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Governança do projeto

A governança do projeto é uma função de supervisão alinhada à estrutura de governança da organização e abrange o ciclo de vida do projeto. Ele fornece ao gerente de projeto e à equipe estrutura, processos, modelos de tomada de decisão e ferramentas para gerenciar e controlar o projeto, enquanto também garante a entrega bem-sucedida do projeto. A governança de projetos é um elemento crucial, especialmente para projetos complexos e estratégicos.

O modelo de governança define, documenta e comunica práticas personalizadas e eficazes para fornecer um método abrangente de controle do projeto e fornecer visibilidade periódica em todos os níveis para garantir o sucesso. Ele contém uma estrutura para a tomada de decisões; define funções, responsabilidades e responsabilidades para a realização do projeto; e controla a eficácia. A estrutura de governança é acumulada desde a equipe de execução até a gerência executiva, definindo as atividades, a geração de relatórios, o escalonamento e o fluxo de informações.

![Infográfico de governança do projeto](../../assets/playbooks/project-governance.svg)

Em vários níveis, as equipes examinam métricas específicas de velocidade e projeto para entender o progresso e tomar medidas corretivas conforme necessário. Essas métricas de nível de velocidade podem incluir a velocidade e o burndown de cada velocidade.

## Detalhes da reunião regular

- Revisão trimestral dos negócios

   - Discutir as estratégias de escalonamento do crescimento

   - Destacar o sucesso e as metas atuais

   - Alinhe os resultados desejados para os próximos trimestres

- Comitê diretor mensal

   - Coordenar e revisar o progresso do projeto

   - Tomada de decisão sobre itens de grande impacto (se houver)

   - O Dentsuen garante a satisfação do cliente e as preocupações são registradas e abordadas

- Comitê de projeto semanal

   - Decidir objetivos, plano, organização da semana

   - Tome decisões sobre arquitetura conforme necessário

   - Revisar e agir nos relatórios de status do projeto

   - Demonstrações da plataforma e recursos

   - Escalonar solicitações/problemas/sugestões

- Reunião diária

   - Discutir e acompanhar itens de ação, incluindo sprint/quadros/tíquetes pendentes atuais

   - Monitorar o progresso do projeto

## KPIs de desempenho

Além das métricas de sprint, também é essencial medir KPIs de desempenho de projeto e qualidade. Isso não só ajuda a garantir o nível de qualidade ao longo do plano, como também mantém a equipe no caminho certo e evita que o projeto saia do trilho.

## Storyboard e velocidade

![Exemplo de quadro Kanban](../../assets/playbooks/kanban-board-chart.svg)

## Sprint e burndown de lançamento

![Exemplo de gráfico de sprint e burndown de lançamento](../../assets/playbooks/sprint-release-burndown.svg)

Desafios ou alterações ocorrem durante a duração de qualquer projeto. Capacitar as pessoas certas em sua organização com a capacidade de rastrear, medir e girar quando um desafio for atingido aumentará a probabilidade de você sair do projeto tendo atingido suas metas e estiver satisfeito com o resultado.

<table>
<thead>
  <tr>
    <th>Medição de desempenho principal</th>
    <th>Unidade de Medida</th>
    <th>Métricas relatadas</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Testar cobertura</td>
    <td>%</td>
    <td>Número de requisitos testáveis abrangidos por casos de teste VS Total de requisitos testáveis incluídos na linha de base</td>
  </tr>
  <tr>
    <td>Densidade do defeito</td>
    <td>%</td>
    <td>Nº de defeitos válidos encontrados VS Total de casos de teste executados</td>
  </tr>
  <tr>
    <td>Vazamento de defeitos em SIT/UAT/produção</td>
    <td>%</td>
    <td>Defeitos relatados na Produção VS Defeitos relatados na Produção + Defeitos relatados por QA+UAT</td>
  </tr>
  <tr>
    <td>Eficácia do teste</td>
    <td>%</td>
    <td>Defeitos Válidos gerados/Defeitos Válidos Emitidos Defeitos Rejeitados</td>
  </tr>
  <tr>
    <td>Qualidade do código</td>
    <td># + %</td>
    <td>Complexidade, LoC, violações, cobertura de código para o sprint</td>
  </tr>
</tbody>
</table>
