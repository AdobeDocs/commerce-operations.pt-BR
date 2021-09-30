---
title: Contratos de nível de serviço
description: Saiba mais sobre os contratos de nível de serviço e como usá-los para dar suporte à implementação do Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# Contratos de nível de serviço (SLAs)

O SLA (Service-Level Agreement, contrato de nível de serviço) define o nível de serviço esperado por um cliente do provedor de serviços, com métricas simples pelas quais esse serviço é medido, bem como as soluções ou sanções, se houver, caso os níveis de serviço acordados não sejam atingidos.

Os SLAs para diferentes tipos de críticas de incidentes podem ser contratados, mantidos e medidos. Além disso, o tipo de resposta pode ter vários padrões (Gold, Platinum), com base no nível de serviço exigido pelo cliente.

A tabela a seguir descreve um detalhamento de métrica de SLA típico com vários níveis de serviço:

<table>
<thead>
  <tr>
    <th>Tipo de problema</th>
    <th>Impacto</th>
    <th>Exemplo</th>
    <th colspan="2">Tempo de resposta/restauração durante o horário comercial suportado</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Ouro</td>
    <td>Platina</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Impacto crítico</td>
    <td>Serviço desativado ou inutilizável</td>
    <td>1 hora / 4 horas</td>
    <td>1 hora / 4 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Serviço indisponível</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>O serviço não pode ser usado em toda a base de usuários finais</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Alto impacto</td>
    <td>Serviço gravemente comprometido</td>
    <td>2 horas / 12 horas</td>
    <td>2 horas / 8 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>O desempenho do serviço está degradado</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Serviço disponível, mas produzindo mensagens de erro significativas</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Impacto médio</td>
    <td>Serviço parcialmente danificado</td>
    <td>8 horas / 16 horas</td>
    <td>8 horas / 12 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Mensagens de erro geradas, sem impacto perceptível no usuário final</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Perguntas sobre os recursos usados no lançamento do cliente</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Opções de cobertura

As opções de cobertura para SLAs comprometidos variam com diferentes tipos de oferta. Normalmente, o escopo dos serviços de suporte Gold e Platinum é semelhante ao seguinte:

![Infográfico mostrando opções de cobertura de SLA](../../assets/playbooks/sla-coverage-options.svg)
