---
title: Controle de qualidade
description: Saiba mais sobre os processos de controle de qualidade do Adobe Commerce relacionados a projetos de implementação.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Processo e ferramentas de controlo da qualidade

![Diagrama do processo de controle de qualidade](../../assets/playbooks/quality-control-diagram.svg)

O processo de controlo de qualidade no diagrama anterior pode ser descrito resumidamente da seguinte forma:

<table>
<thead>
  <tr>
    <th>Processo de desenvolvimento de software</th>
    <th>Fluxo de trabalho QC</th>
    <th>QC</th>
    <th>Líder QC</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Desenvolvimento</td>
    <td>Planejamento</td>
    <td></td>
    <td>Rever e contribuir para os planos de ensaio</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Criar especificações de teste (casos de teste/cenários de teste)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Preparar e adquirir dados de teste</td>
  </tr>
  <tr>
    <td></td>
    <td>Análise e design de teste</td>
    <td>Rever e contribuir para os planos de ensaio</td>
    <td>Iniciar a preparação, especificações</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Criar especificações de teste (casos de teste/cenários de teste)</td>
    <td>Escrever ou analisar uma estratégia de teste para o projeto</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preparar e adquirir dados de teste</td>
    <td> Líder, orientar e monitorar a análise e o design</td>
  </tr>
  <tr>
    <td>Teste interno</td>
    <td>Testar implementação e execução</td>
    <td>Implementa testes, executa e registra os testes</td>
    <td>Acompanhamento da execução e execução dos ensaios</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Verificar o desempenho e verificar a segurança - Avalie os resultados e os desvios dos resultados esperados</td>
    <td>Assegurar a rastreabilidade dos testes até à base de ensaio e controlar os bugs no sistema de controlo de bugs</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Postar bugs no sistema de rastreamento de bugs (Jira/Redmine/Trello)</td>
    <td>Priorizar/programar testes para alinhar-se ao planejamento do projeto definido pelo PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testar novamente (teste de confirmação) após a correção de erros</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Avaliação e criação de relatórios</td>
    <td>Reportar o progresso do teste para QC lead e PM</td>
    <td>Avaliação dos resultados e do progresso dos testes</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Escreva relatórios resumidos do teste com base nas informações coletadas durante o teste</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verificar Feedbacks de cliente ou Solicitações de alteração (CRs)</td>
    <td>Acompanhamento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realizar testes de redefinição e de regressão após alterar o código-fonte</td>
    <td>Controlar</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Atualizar especificações de teste</td>
    <td></td>
  </tr>
  <tr>
    <td>Manutenção</td>
    <td>Manutenção</td>
    <td>Rever e contribuir para tarefas</td>
    <td>Revisar e estimar o tempo de tarefas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Criar/atualizar especificações de teste</td>
    <td>Progressos dos testes de acompanhamento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Executar testes para essas tarefas</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Executar teste de regressão</td>
    <td></td>
  </tr>
</tbody>
</table>

Semelhante às [ferramentas](project-management-tools.md) que identificamos para o processo de desenvolvimento, selecionamos algumas soluções e plataformas de escolha que geralmente utilizamos para testes de controle de qualidade.

| Finalidade | Ferramenta |
|---------------------------|---------------------------------------------------|
| Índice de desempenho do site | Google PageSpeed, Webpagetest, JMeter |
| Segurança | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| Sistema de gestão de problemas | JIRA |
| Teste da interface do usuário | Pixel perfeito, BrowserStack |
| Teste de API | Postman, SoapUI |
| Teste de automação | Selênio |


## Índice de desempenho do site

O GooglePageSpeed relata o desempenho de uma página em dispositivos móveis e de desktop e fornece sugestões sobre como essa página pode ser melhorada.

WebPageTest é uma ferramenta de desempenho da Web que usa navegadores reais para acessar páginas da Web e coletar métricas de tempo.

O JMeter é um projeto do Apache que pode ser usado como uma ferramenta de teste de carga para analisar e medir o desempenho de uma variedade de serviços, com foco em aplicações Web.

## Segurança

O SonarQube e o ZAP foram introduzidos no processo de desenvolvimento, mas também estamos a incluí-los aqui com mais informações sobre a forma como estão envolvidos no processo de QC.

O SonarQube também é usado para inspeção contínua da qualidade do código para executar revisões automáticas com análise estática do código para detectar bugs, cheiros de código e vulnerabilidades de segurança.

O OWASPipAP (Zed Attack Proxy) deve ser usado por ambos os novos usuários para segurança de aplicativos, bem como por testadores profissionais de penetração. Alguns dos recursos incorporados incluem interceptação de servidor proxy, rastreadores Web tradicionais e AJAX, scanner automatizado, scanner passivo, navegação forçada, Fuzzier, suporte WebSocket, linguagens de script e suporte a Plug-n-Hack.

## Teste da interface do usuário

O Pixel perfeito permite que desenvolvedores e designers de marcação coloquem uma sobreposição de imagem semitransparente sobre o HTML desenvolvido e executem uma comparação perfeita em pixels entre eles.

O BrowserStack é uma plataforma de teste móvel e da Web em nuvem que permite aos desenvolvedores testar seus sites e aplicativos móveis em navegadores sob demanda, sistemas operacionais e dispositivos móveis reais.

## Teste de API

O Postman é a plataforma de colaboração para desenvolvimento de API. O Postman simplifica cada etapa da criação de uma API e simplifica a colaboração para que você possa criar APIs melhores.

SoapUI é um aplicativo de teste de serviço da Web de código aberto para SOAP (Simple Object Access Protocol) e REST (Representational State Transfer). A sua funcionalidade abrange a inspeção de serviços Web; invocar, desenvolver, simular e zombar; ensaio funcional; ensaio de carga e conformidade.

## Teste de automação

O Selenium é composto de vários componentes (API cliente Selenium, Selenium WebDriver), cada um assumindo uma função específica para ajudar o desenvolvimento da automação de teste de aplicações web.
