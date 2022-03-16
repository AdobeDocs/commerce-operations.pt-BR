---
title: Metodologia de implementação do projeto
description: Familiarize-se com o funcionamento da entrega de software Adobe Commerce.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metodologia de execução do projeto

Agora que você tem uma ideia melhor das ferramentas que estão envolvidas, nós vamos analisar nossos processos de entrega e teste.

## Integração contínua (CI)

Os trabalhos de integração contínua executam automaticamente as seguintes ações:

- Crie o código-fonte para verificar erros de compilação.
- Execute testes quando uma solicitação de pull for criada/atualizada. Atualmente, os testes de unidade PHP são executados.

A tarefa posta seu status de execução na solicitação de pull. Os desenvolvedores podem visualizar os detalhes da execução do trabalho para que possam corrigir ou melhorar o código existente.

## Delivery contínuo (CD)

O Continuous Delivery (CD) implanta imediatamente o código fonte no servidor depois que todos os testes forem bem-sucedidos. Os desenvolvedores podem verificar suas funções rapidamente e, em seguida, atribuir a tarefa à equipe de controle de qualidade para análise.

Como a build é executada no sistema de build, ela não apenas minimiza o tempo de inatividade da implantação, como também reduz a carga no servidor. Como resultado, as atividades de controle de qualidade, que estão acontecendo no servidor, são menos afetadas.

![Informações de delivery contínuo](../../assets/playbooks/cicd.svg)

O processo de CI/CD no diagrama anterior pode ser descrito resumidamente da seguinte forma:

- O bucket hospeda o repositório Git.
- Imagens docking são replicadas das configurações de pilha da tecnologia de produção.
- Os containers Docker são usados para todos os ambientes de desenvolvimento e teste. Outros ambientes podem aproveitar essas configurações, se necessário.
- Os desenvolvedores realizam uma finalização da ramificação de código relevante para cada nova tarefa/tíquete.
- Para todas as ramificações de confirmação, automaticamente:
   - Execute uma verificação de código padrão.
   - Execute um teste de compilação de código.
   - Execute uma verificação de código estático (por exemplo, SonarQube).
- Todas as confirmações de varredura passadas são mescladas com a ramificação de destino.
- Uma nova tag lançada é enviada para o AWS S3 para o pacote de preparação da implantação.
- A nova implantação é acionada pela equipe de engenharia de implantação.
   - Um trabalho de implantação implanta o novo pacote no ambiente de destino.
   - As atualizações da estrutura do banco de dados exigem uma pausa para receber novas solicitações do cliente.
- O processo de implantação termina com uma notificação email/Slack/Teams, enviada automaticamente pelo servidor para a equipe de engenharia de implantação.
