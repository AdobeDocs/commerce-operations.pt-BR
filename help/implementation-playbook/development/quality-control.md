---
title: Controle de qualidade
description: Saiba mais sobre os processos de controle de qualidade do Adobe Commerce relacionados aos projetos de implementação.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Processo e ferramentas de controlo da qualidade

![Diagrama do processo de controle de qualidade](../../assets/playbooks/quality-control-diagram.svg)

O processo de controle de qualidade no diagrama anterior pode ser descrito resumidamente da seguinte maneira.

<table>
<thead>
  <tr>
    <th>Processo de desenvolvimento de software</th>
    <th>Fluxo de trabalho de QC</th>
    <th>QC</th>
    <th>Líder de controle de qualidade</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Desenvolvimento</td>
    <td>Planejamento</td>
    <td></td>
    <td>Revisar e contribuir com planos de teste</td>
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
    <td>Análise e projeto de teste</td>
    <td>Revisar e contribuir com planos de teste</td>
    <td>Iniciar a preparação, especificações</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Criar especificações de teste (casos de teste/cenários de teste)</td>
    <td>Escrever ou revisar uma estratégia de teste para o projeto</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preparar e adquirir dados de teste</td>
    <td> Liderar, orientar e monitorar a análise, o design</td>
  </tr>
  <tr>
    <td>Teste interno</td>
    <td>Implementação e execução de teste</td>
    <td>Implementa testes, executa e registra os testes</td>
    <td>Acompanhamento da implementação e execução dos testes</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Verificar o desempenho e a segurança da verificação - Avalie os resultados e os desvios dos resultados esperados</td>
    <td>Garantir a rastreabilidade dos testes para a base de teste e rastrear os bugs no sistema de rastreamento de bugs</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Publicar bugs no sistema de rastreamento de erros (Jira/Redmine/Trello)</td>
    <td>Priorizar/programar testes para alinhar-se ao planejamento do projeto definido pelo PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Repetir o teste (teste de confirmação) após a correção de erros</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Avaliação e geração de relatórios</td>
    <td>Relatar o progresso do teste ao lead e PM do QC</td>
    <td>Avaliar os resultados e o progresso do teste</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Escrever relatórios de resumo de teste com base nas informações coletadas durante o teste</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verificar Comentários do Cliente ou Solicitações de Alteração (CRs)</td>
    <td>Acompanhamento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realizar novos testes e testes de regressão após alterar o código-fonte</td>
    <td>Controlando</td>
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
    <td>Revisar e contribuir com tarefas</td>
    <td>Revisar e estimar o tempo para tarefas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Criar/atualizar especificações de teste</td>
    <td>Progresso do teste de acompanhamento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Executar testes para estas tarefas</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realizar teste de regressão</td>
    <td></td>
  </tr>
</tbody>
</table>

Semelhante ao [ferramentas](project-management-tools.md) identificamos para o processo de desenvolvimento, selecionamos algumas soluções e plataformas de escolha que costumamos utilizar para testes de controle de qualidade.

| Finalidade | Ferramenta |
|---------------------------|---------------------------------------------------|
| Índice de desempenho do site | Google PageSpeed, Webpagetest, JMeter |
| Segurança | Ferramenta de verificação de segurança Adobe Commerce, SonarQube, ZAP |
| Sistema de gerenciamento de problemas | JIRA |
| Teste da interface do usuário | Perfect Pixel, Pilha de navegador |
| Teste de API | Postman, SoapUI |
| Teste de automação | Selênio |


## Índice de desempenho do site

O GooglePageSpeed relata o desempenho de uma página em dispositivos móveis e desktop e fornece sugestões sobre como essa página pode ser melhorada.

WebPageTest é uma ferramenta de desempenho da Web que usa navegadores reais para acessar páginas da Web e coletar métricas de tempo.

JMeter é um projeto Apache que pode ser usado como uma ferramenta de teste de carga para analisar e medir o desempenho de uma variedade de serviços, com foco em aplicações web.

## Segurança

SonarQube e ZAP foram introduzidos no processo de desenvolvimento, mas também estamos incluindo-o aqui com mais informações sobre como ele está envolvido no processo de QC.

O SonarQube também é usado para inspeção contínua da qualidade do código para executar revisões automáticas com análise estática do código para detectar bugs, code smells e vulnerabilidades de segurança.

OWASPZAP (Zed Attack Proxy) é destinado a ser usado por aqueles novos na segurança de aplicativos, bem como testadores de penetração profissional. Alguns dos recursos incorporados incluem interceptação de servidor proxy, rastreadores da Web tradicionais e AJAX, scanner automatizado, scanner passivo, navegação forçada, Fuzzier, suporte a WebSocket, linguagens de script e suporte a Plug-n-Hack.

## Teste da interface do usuário

O Perfect Pixel permite que desenvolvedores e designers de marcação coloquem uma sobreposição de imagem semitransparente sobre o HTML desenvolvido e executem uma comparação pixel-perfeita entre eles.

BrowserStack é uma plataforma de teste móvel e da Web em nuvem que permite aos desenvolvedores testar seus sites e aplicativos móveis em navegadores sob demanda, sistemas operacionais e dispositivos móveis reais.

## Teste de API

O Postman é a plataforma de colaboração para o desenvolvimento de API. O Postman simplifica cada etapa da criação de uma API e simplifica a colaboração para que você possa criar APIs melhores.

O SoapUI é um aplicativo de teste de serviço Web de código aberto para SOAP (Simple Object Access Protocol) e REST (Representational State Transfer). Sua funcionalidade abrange inspeção de serviços da Web; invocação, desenvolvimento, simulação e zombaria; teste funcional; teste de carga e conformidade.

## Teste de automação

O Selenium é composto por vários componentes (API do cliente Selenium, Selenium WebDriver), cada um assumindo uma função específica em ajudar no desenvolvimento da automação de testes de aplicações Web.
