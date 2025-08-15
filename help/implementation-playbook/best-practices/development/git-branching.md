---
title: Práticas recomendadas de ramificação Git
description: Saiba mais sobre as diferentes estratégias de ramificação para o gerenciamento de código-fonte.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Práticas recomendadas de ramificação Git

O código do Source passa por várias fases de estabilidade durante o processo de desenvolvimento:

- Desenvolvimento ativo
- Integração inicial do código
- Integração de código para controle de qualidade (QA)
- Integração de código para teste de aceitação final do usuário (UAT)
- Integração final do código para versões de produção

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Gerenciamento de filial

Cada fase de desenvolvimento deve ter uma ramificação correspondente no Git para rastrear alterações no código e facilitar o processo de implantação:

- **Ramificação da tarefa** — Onde os desenvolvedores confirmam suas alterações de código individuais ao implementarem tarefas específicas, como recursos e correções de erros.
- **Ramificação de desenvolvimento** — Onde vários desenvolvedores mesclam as alterações de suas ramificações de tarefas individuais em uma única ramificação de desenvolvimento para testes de integração automatizados. Essa ramificação é implantada em um ambiente de desenvolvimento.
- **Ramificação de controle de qualidade** — Onde os desenvolvedores mesclam as alterações após a conclusão do desenvolvimento e o código passa em todos os testes de integração automatizada e na revisão do código. Essa ramificação é implantada no ambiente de QA para testes manuais de QA.
- **Ramificação estável/UAT** — Em que o código é mesclado depois de passar no teste de controle de qualidade manual. Essa ramificação é implantada em um ambiente UAT para testes de aceitação do usuário.
- **Ramificação de produção/liberação** — Em que o código é mesclado após passar pelo UAT. Essa ramificação é implantada na produção para uma versão.

>[!TIP]
>
>O Adobe Commerce em projetos de infraestrutura em nuvem contém ramificações específicas que correspondem a ambientes diferentes. Consulte o [Fluxo de trabalho do projeto Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=pt-BR) e o [Fluxo de trabalho do projeto inicial](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=pt-BR) no _Guia da Nuvem_.

## Estratégias de ramificação

Há várias estratégias de ramificação que podem ser usadas. Escolha uma estratégia que funcione melhor para sua equipe de desenvolvimento e para a complexidade do seu projeto.

Para obter mais informações, consulte os seguintes recursos externos:

- [Fluxos de trabalho de ramificação](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Fluxos de trabalho distribuídos](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Padrões para gerenciar ramificações de código-fonte](https://martinfowler.com/articles/branching-patterns.html)
- [Um modelo de ramificação Git bem-sucedido](https://nvie.com/posts/a-successful-git-branching-model/)
- [Fluxo do GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Fluxo do GitLab](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
