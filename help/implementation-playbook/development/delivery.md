---
title: Metodologia de implementação do projeto
description: Familiarize-se com o funcionamento do Adobe Commerce Software Delivery.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metodologia de implementação do projeto

Agora que você tem uma ideia melhor das ferramentas envolvidas, vamos analisar nossos processos de entrega e teste.

## Integração contínua (CI)

Os trabalhos de integração contínua executam automaticamente as seguintes ações:

- Crie o código-fonte para verificar erros de compilação.
- Execute testes quando uma solicitação de pull for criada/atualizada. No momento, os testes de unidade do PHP são executados.

O trabalho publica seu status de execução na solicitação de pull. Os desenvolvedores podem exibir os detalhes da execução do trabalho para que possam corrigir ou melhorar o código existente.

## Entrega contínua (CD)

O Continuous Delivery (CD) implanta imediatamente o código-fonte no servidor depois que todos os testes forem bem-sucedidos. Os desenvolvedores podem verificar suas funções rapidamente e atribuir a tarefa à equipe de controle de qualidade para análise.

À medida que a build é executada no sistema de build, ela não apenas minimiza o tempo de inatividade da implantação, como também reduz a carga no servidor. Como resultado, as atividades de controle de qualidade, que estão acontecendo no servidor, são menos afetadas.

![Infográfico de entrega contínua](../../assets/playbooks/cicd.svg)

O processo de CI/CD no diagrama anterior pode ser descrito resumidamente da seguinte maneira:

- O Bitbucket hospeda o repositório Git.
- As imagens do Docker são replicadas das configurações da pilha de tecnologia de produção.
- Os contêineres Docker são usados para todos os ambientes de desenvolvimento e teste. Outros ambientes podem aproveitar essas configurações, se necessário.
- Os desenvolvedores executam uma finalização da ramificação de código relevante para cada nova tarefa/tíquete.
- Para todas as ramificações de confirmação, automaticamente:
   - Execute uma verificação de código padrão.
   - Execute um teste de compilação de código.
   - Executar uma verificação de código estático (por exemplo, SonarQube).
- Todas as confirmações de varredura passadas são mescladas com a ramificação de destino.
- Uma nova tag lançada é enviada para o AWS S3 para o pacote de preparação de implantação.
- A nova implantação é acionada pela equipe de engenharia de implantação.
   - Um trabalho de implantação implanta o novo pacote no ambiente de destino.
   - As atualizações de estrutura do banco de dados exigem uma pausa para aceitar novas solicitações do cliente.
- O processo de implantação termina com uma notificação por email/Slack/Equipes, enviada automaticamente pelo servidor para a equipe de engenharia de implantação.
