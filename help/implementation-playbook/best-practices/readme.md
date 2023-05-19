---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# Práticas recomendadas: fluxo de trabalho de criação de conteúdo

Este documento descreve o fluxo de trabalho do usuário para solicitar alterações ou adições ao *[Práticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* conteúdo no *Manual de implementação do Adobe Commerce*.

## Quem pode criar uma solicitação?

O Adobe aceita solicitações de participantes internos e externos, incluindo, mas não limitado a, indivíduos nos seguintes grupos:

- Parceiros Adobe
- Adobe CTAG (Customer Technical Advisory Group), Suporte ao cliente, Sucesso do cliente, equipes de engenharia

## Como criar uma solicitação?

**Partes interessadas internas** O pode enviar solicitações abrindo um problema do Jira no projeto COMDOX. **Partes interessadas externas** pode enviar solicitações abrindo um [Problema do GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) neste repositório.

Você pode submeter os seguintes tipos de solicitações:

- Ideias para novo conteúdo
- Atualizações no conteúdo já publicado
- Publicar novo conteúdo fornecido pela parte interessada ou comunidade

## Qual é o processo geral?


**Criar um tíquete ou problema do Jira**—Partes interessadas internas criam um tíquete Jira no projeto COMDOX. Os participantes externos enviam um problema do GitHub. Inclua detalhes completos na Jira ou [Problema do GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) para ajudar a equipe a entender o contexto e priorizar a solicitação.

**A equipe do projeto Adobe avalia e prioriza a solicitação**— a equipe monitora regularmente as solicitações para determinar a prioridade e avaliar as alterações solicitadas para inclusão nas Práticas recomendadas do manual de implementação. Por exemplo, a equipe pode determinar que, em vez de criar um novo tópico de Práticas recomendadas, o conteúdo solicitado seja adicionado à documentação do produto existente no Experience League ou no site do Adobe Developer.

Se não houver informações suficientes em uma solicitação, a equipe solicitará informações adicionais ao solicitante. Se o solicitante não responder dentro de 14 dias, a equipe fechará a solicitação.

**Criar ou atualizar conteúdo**-O trabalho de criação de conteúdo é concluído após o processo documentado na [Guia do colaborador do Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Dependendo da solicitação, o trabalho pode incluir a conversão de novo conteúdo em markdown, a criação de um tópico ou a atualização de um tópico existente.

**Revisão, aprovação e publicação de conteúdo**-O conteúdo é revisado e editado durante a criação ou atualização do tópico usando [Solicitações de pull do GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Todo o conteúdo deve passar por revisão editorial. A revisão técnica é opcional e depende do conteúdo. Se nenhuma revisão técnica for necessária, o processo continuará somente com uma revisão editorial. Esse processo pode realizar várias iterações até que o conteúdo seja aprovado.

Depois que um artigo é aprovado, a solicitação de pull pode ser mesclada à ramificação de produção. A mesclagem deve ser feita pelo autor. Depois que um tópico é mesclado, ele pode ser publicado na produção imediatamente usando um processo manual ou automaticamente na próxima vez que o trabalho de publicação for executado. Os trabalhos de publicação normalmente são executados a cada duas horas.

**Nova notificação de conteúdo**-Adobe fornecerá um *Novidades* seção no [Visão geral das práticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) tópico para manter os usuários informados sobre tópicos publicados recentemente ou atualizados. O Adobe também promoverá novos conteúdos de práticas recomendadas usando os canais existentes, como marketing e comunicações internas.

## Backlog e Quadro Kanban

Para evitar duplicações, as solicitações que foram criadas e priorizadas estarão visíveis no backlog Jira do projeto COMDOX e [Projeto de problemas do GitHub](https://github.com/orgs/AdobeDocs/projects/6/views/1). As partes interessadas internas são incentivadas a colaborar com o sistema de votação na Jira para votar a favor dos pedidos que consideram necessários ou pertinentes. A votação também ajuda a equipe do projeto de Práticas recomendadas a entender o tipo de conteúdo que as partes interessadas esperam e valorizam. As solicitações com priorização e revisão pendentes são mostradas no backlog até serem movidas para as faixas ativas no quadro Kanban.

O quadro Kanban pode ser acessado por usuários internos para visualizar (e/ou monitorar) em qual conteúdo está sendo trabalhado e o progresso feito. Somente solicitações ativas serão exibidas neste quadro.
