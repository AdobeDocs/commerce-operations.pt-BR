---
title: Implementação de atualização
description: Saiba mais sobre as diferentes fases da implementação de atualização para projetos do Adobe Commerce.
source-git-commit: 5e02f300bb0b5601c653fdea1dd5b85f4e18ed9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---


# Atualizar implementação

A implementação do upgrade consiste em cinco fases:

- Análise de atualização
- Desenvolvimento e garantia da qualidade (QA)
- Teste de aceitação do usuário (UAT) e preparação para o lançamento
- Launch
- Pós-lançamento

## Análise de atualização

A análise é, sem dúvida, a parte mais importante do processo de atualização. Uma análise bem executada economiza tempo e limita surpresas no futuro. O resultado dessa fase deve ser uma lista de verificação de atualização detalhada e um documento com todas as dependências.

A seguir estão itens que talvez você queira incluir em uma análise completa:

- **Escopo da versão de destino**—Documentação sobre [Experience League](../../release/release-notes/overview.md) As informações dos webinars de lançamento do parceiro fornecem todos os detalhes que você deve saber sobre a atualização do target.

- **[!DNL Upgrade Compatibility Tool]resultados**— Essa ferramenta agiliza e facilita a atualização por meio da comparação do código atual com o código da versão de destino e da produção de um relatório de todos os problemas que precisam ser solucionados. Consulte a [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Os principais detalhes do relatório incluem:

   - Versão instalada atual
   - Atualizar versão de destino
   - Número e detalhes de erros críticos encontrados

- Atualização de serviços para suportar a versão de destino. Use o modelo de tabela a seguir para mapear quais serviços você deve atualizar. Use o [requisitos do sistema](../../installation/system-requirements.md) para determinar o que adicionar à variável _Atualizar para_ coluna.


   | Serviço | Versão atual | Atualizar para | Notas |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.4 | 8.1 |  |
   | Redis | 6.0 | 6.2 |  |
   | [!DNL RabbitMQ] | 3.8 | 3.9 | Não está sendo usado no momento, mas devemos considerá-lo |
   | MariaDB (Nuvem) | 10.4 | 10.6 |  |
   | MySQL | 8.0 | -/-/ |  |
   | Compositor | 1.9.2 | 2.2 |  |
   | Elasticsearch | 7.10 | 7.17 |  |

- **Extensões e módulos de terceiros**—Use esse template de tabela para entender o status de suas extensões e personalizações, de modo que possa tomar decisões estratégicas e definir ações. Esta é uma oportunidade de substituir quaisquer extensões que possam ser nativas do Adobe Commerce ou do Magento Open Source para minimizar a complexidade do seu projeto. Use o `bin/magento module:status` para ver uma lista de módulos e extensões.

   | # | Extensão/<br>nome do módulo | Pacote do compositor | Fornecedor | Versão atual | Funcionalidade | Compatível com o mais recente<br>Versão do Commerce? | Problemas | Nativo do Commerce? | Ação | Notas |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nome da extensão e link | extensão/<br>extensionx-magento-2 | Nome do fornecedor | Versão instalada | Requisitos comerciais | Sim/Não | Lista de problemas identificados com essa extensão | Sim/Não | Manter/Substituir/<br>Remover |  |

- **Módulos personalizados**—Semelhante à tabela de módulos de terceiros, esse modelo ajuda a rastrear e entender o status e as ações necessárias para atualizar módulos personalizados.

   | # | Nome do módulo | Funcionalidade | Obrigatório? | Nativo do Commerce? | Ação | Notas |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nome do módulo | Requisitos comerciais | Sim/Não | Sim/Não | Manter/Substituir/Remover |  |

- **Pacotes do compositor e dependências no composer.json que exigem uma atualização.**

Além disso, os parceiros [Versões beta do Adobe Commerce](../../release/beta.md) e usar oportunidades de pré-lançamento para obter acesso antecipado ao código para uma versão futura. Obter acesso ao código antecipadamente ajuda os desenvolvedores a se prepararem com tempo suficiente para concluir a atualização até a data de Disponibilidade Geral (GA). O código beta geralmente é lançado cinco semanas antes da data de GA e os pré-lançamentos são lançados com duas semanas de antecedência.

## Desenvolvimento e controle de qualidade

Os testes são a fase de uma atualização que requer mais tempo. Como resultado, esse processo deve ser o mais automatizado possível. A variável _[Guia de teste do aplicativo](https://developer.adobe.com/commerce/testing/guide/)_ A seção fornece detalhes sobre como configurar e usar ferramentas de teste da plataforma e do sistema para garantir a qualidade com mais rapidez. Use um ambiente de preparo para testar e validar sua atualização antes de passar para a produção.

## UAT e preparação para lançamento

O UAT é um dos últimos estágios da atualização que requer a revisão e validação do site. Você também deve decidir quando implantar e se precisa de uma página de manutenção. Fazer planos para processos cron e mensagens de terceiros.

À medida que a data de implantação se aproxima, a comunicação é essencial. Se mais pessoas souberem sobre a mudança no horizonte, como ela as afeta e como elas devem lidar com isso, então você estará mais propenso a ter um lançamento bem-sucedido. Não tenha medo de se comunicar em excesso a cada passo do caminho, isso aumenta a probabilidade de análises brilhantes de todos os envolvidos assim que você entra ao vivo!

## Launch

Conclua a atualização implantando em extensões de produção e atualizando. Certifique-se de testar os fluxos de caminho críticos com pedidos simulados. Confira estes [práticas recomendadas](../prepare/best-practices.md) para obter algumas dicas sobre como iniciar o com problemas mínimos.

Siga seu plano de comunicação e verifique se todas as partes interessadas estão cientes da atualização e são totalmente treinadas para apoiá-la.

Por fim, informe-se com sua equipe para determinar as lições aprendidas e as armadilhas. Essa retrospectiva ajuda a melhorar o processo na próxima vez.

## Pós-lançamento

Depois que o site for iniciado, verifique os dados de análise, o Google Search Console e outros recursos para garantir que não haja problemas inesperados e que tudo funcione conforme esperado.

É sempre uma boa ideia acompanhar o desempenho por meio de ferramentas de monitoramento bem projetadas. Há muitas ferramentas e meios de monitorar o desempenho do site, portanto, escolha um que se pareça bem com a sua organização. Recomendamos que os clientes da Adobe Commerce que usam nosso sistema de gerenciamento de infraestrutura em nuvem aproveitem serviços como [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) para monitorar o desempenho do site.
