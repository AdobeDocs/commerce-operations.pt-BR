---
title: Atualizar implementação
description: Saiba mais sobre as diferentes fases de implementação de atualização para projetos Adobe Commerce e Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 1%

---


# Atualizar implementação

A implementação de atualização consiste em cinco fases:

- Análise de atualização
- Desenvolvimento e garantia de qualidade (QA)
- Teste de aceitação do usuário (UAT) e preparação para o lançamento
- Launch
- Pós-lançamento

## Análise de atualização

A análise é provavelmente a parte mais importante do processo de atualização. Uma análise bem executada economiza tempo e limita surpresas no futuro. O resultado dessa fase deve ser uma lista de verificação de atualização detalhada e um documento com todas as dependências.

A seguir estão itens que você pode incluir em uma análise completa:

- **Escopo da versão do target**—Documentação sobre [DevDocs do Commerce](https://devdocs.magento.com) Os webinários de versão do e do parceiro fornecem todos os detalhes que você precisa saber sobre a atualização do target.

- **Atualizar resultados da Ferramenta de Compatibilidade**—Essa ferramenta facilita e agiliza qualquer atualização, comparando seu código atual ao código da versão de destino e produzindo um relatório de todos os problemas que precisam ser resolvidos. Consulte a [Ferramenta de compatibilidade de atualização](../upgrade-compatibility-tool/overview.md). Os principais detalhes do relatório incluem:

   - Versão atual instalada
   - Atualizar a versão de destino
   - Número e detalhes de erros críticos encontrados

- Atualização de serviços para oferecer suporte à versão de destino. Use o modelo de tabela a seguir para mapear quais serviços você deve atualizar. Use o [requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) para determinar o que será adicionado ao _Atualizar para_ coluna.


   | Serviço | Versão atual | Atualizar para | Notas |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.2.33 | 8,1 |  |
   | Redis | 5,05 | 6,0 |  |
   | RabbitMQ | 3,7 | 3,8 | Não está a ser utilizado, mas devemos considerar a sua utilização |
   | MariaDB (nuvem) | 10.2.33 | 10,4 |  |
   | MySQL | 8,0 |  |  |
   | Composer | 1.9.2 | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Extensões e módulos de terceiros**—Use este modelo de tabela para ajudá-lo a entender o status de suas extensões e personalizações, para que você possa tomar decisões estratégicas e definir ações. Essa é uma oportunidade de substituir qualquer extensão que possa ser nativa do Adobe Commerce ou do Magento Open Source para minimizar a complexidade do seu projeto. Use o `bin/magento module:status` para ver uma lista de módulos e extensões.

   | # | Extensão/<br>nome do módulo | Pacote do compositor | Fornecedor | Versão atual | Funcionalidade | Compatível com a mais recente<br>Versão comercial? | Problemas | Nativo do Commerce? | Ação | Notas |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nome e link da extensão | extensão/<br>extensionx-magento-2 | Nome do fornecedor | Versão instalada | Requisitos de empresa | Sim/Não | Listar problemas identificados com esta extensão | Sim/Não | Manter/Substituir/<br>Remover |  |

- **Módulos personalizados**—Semelhante à tabela de módulos de terceiros, esse modelo ajuda a rastrear e compreender o status e as ações necessárias para atualizar módulos personalizados.

   | # | Nome do módulo | Funcionalidade | Obrigatório? | Nativo do Commerce? | Ação | Notas |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nome do módulo | Requisitos de empresa | Sim/Não | Sim/Não | Manter/Substituir/Remover |  |

- **Pacotes do Composer e dependências no composer.json que exigem uma atualização.**

Além disso, os parceiros podem participar da [Programa Adobe Commerce Beta](https://devdocs.magento.com/release/beta-program.html) e usar oportunidades de pré-lançamento para obter acesso antecipado ao código para uma versão futura. Obter acesso ao código antecipadamente ajuda os desenvolvedores a se prepararem com tempo suficiente para concluir a atualização até a data da Disponibilidade Geral (GA). O código beta normalmente é lançado cinco semanas antes da data da disponibilidade geral e os pré-lançamentos são lançados duas semanas antes. Para a versão 2.4.4, o Adobe começou a lançar o código beta cinco meses antes da data da disponibilidade geral (8 de março de 2022), para que os parceiros possam começar a se preparar para essa atualização agora em [inscrever-se para o programa](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Desenvolvimento e controle de qualidade

O teste é a fase de uma atualização que requer mais tempo. Consequentemente, este processo deve ser tão automatizado quanto possível. O _[Guia de teste de aplicativo](https://devdocs.magento.com/guides/v2.4/test/testing.html)_ O fornece detalhes sobre como configurar e usar ferramentas de teste de plataforma e sistema para garantir um controle de qualidade mais rápido. Use um ambiente de preparo para testar e validar sua atualização antes de migrar para a produção.

## UAT e preparação para o lançamento

O UAT é um dos últimos estágios da atualização que requer a revisão e validação do site. Você também deve decidir quando implantar e se precisa de uma página de manutenção. Faça planos para processos cron e mensagens de terceiros.

À medida que a data de implantação se aproxima, a comunicação é essencial. Se mais pessoas souberem sobre a mudança no horizonte, como ela afeta elas e como elas devem lidar com isso, então é mais provável que você tenha um lançamento bem-sucedido. Não tenha medo de comunicar em demasia todas as etapas do caminho, isso aumenta a probabilidade de as revisões serem brilhantes de todos os envolvidos serem ativados!

## Launch

Conclua a atualização implantando em produção e atualizando extensões. Teste os fluxos de caminho críticos com pedidos simulados. Veja estes [práticas recomendadas](../prepare/best-practices.md) para algumas dicas sobre inicialização com problemas mínimos.

Siga seu plano de comunicação e garanta que todos os participantes estejam cientes da atualização e sejam totalmente treinados para apoiá-la.

Por fim, faça um resumo com sua equipe para determinar as lições aprendidas e as armadilhas. Essa retrospectiva ajuda você a melhorar o processo da próxima vez.

## Pós-lançamento

Depois que seu site for iniciado, verifique os dados de análise, o Console de pesquisa do Google e outros recursos para garantir que não haja problemas inesperados e que tudo esteja funcionando conforme o esperado.

É sempre uma boa ideia acompanhar o desempenho através de ferramentas de monitoramento bem projetadas. Há muitas ferramentas e meios de monitorar o desempenho de seu site, portanto, certifique-se de escolher um que pareça bem com sua organização. Recomendamos que os clientes da Adobe Commerce que usam nosso sistema de gerenciamento de infraestrutura em nuvem aproveitem serviços como [Novo Relic](https://devdocs.magento.com/cloud/project/new-relic.html) para monitorar o desempenho do site.
