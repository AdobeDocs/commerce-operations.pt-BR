---
title: Práticas recomendadas da lista de verificação de atualização
description: Saiba como criar e usar uma lista de verificação de atualização para planejar sua estratégia de atualização de Adobe Commerce e Magento Open Source.
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e02f300bb0b5601c653fdea1dd5b85f4e18ed9c
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Práticas recomendadas da lista de verificação de atualização

Use essa lista de verificação durante suas conversas anuais e trimestrais com a equipe de comércio eletrônico. Muitas empresas trabalham com orçamentos e roteiros anuais. É fundamental, durante essas discussões anuais, que você fale sobre a saúde, a direção e a estratégia de atualização da sua plataforma para o ano, juntamente com como ela se encaixa nas metas gerais e KPIs da empresa. Durante as conversas trimestrais, verifique se o plano anual criado ainda está alinhado à sua situação atual ou dinâmico, se não estiver. A meta desta Lista de verificação do plano de atualização é ajudar você a planejar e agendar atualizações do Adobe Commerce para garantir um processo de atualização bem-sucedido durante o ano. Esta lista de verificação deve ser usada pelos seguintes públicos-alvo para planejamento anual e revisão trimestral:

- Director / TI do gerente
- Gerenciador de comércio eletrônico
- Parceiro/consultor de soluções

>[!NOTE]
>
>Para obter uma descrição detalhada das etapas técnicas para uma atualização bem-sucedida, consulte [Concluir os pré-requisitos de atualização](../../../upgrade/prepare/prerequisites.md) em nossa documentação do usuário.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Metas

Revise os KPIs atuais e ajuste conforme necessário.

## Extensões e personalizações

Revise todas as extensões e personalizações atuais e garanta que elas ainda sejam necessárias com base nas necessidades dos negócios.

Considere a substituição de qualquer extensão que não tenha um bom registro de acompanhamento para manter-se atualizado com as versões do Adobe Commerce.

## Equipe

‖Certifique-se de ter a equipe certa em vigor com as certificações e os conjuntos de habilidades adequados da Adobe Commerce.

## Orçamento e tempo

Usar o Adobe Commerce [programação de lançamento](../../../release/schedule.md) para planejar sua próxima atualização e se preparar antecipadamente.

Discutir qual versão você acha que adotará (completa ou somente segurança) com base nas necessidades previstas.

Separe um orçamento e a capacidade da equipe para a atualização.

## Integrações de terceiros

Revise as integrações atuais de terceiros da Adobe Commerce e suas janelas de manutenção do ano e considere alinhar o trabalho de atualização com sua programação de manutenção.

## Planejamento de escopo e implantação

Atividades de acesso antecipado

- O parceiro participa de [Beta](../../../release/beta.md)
- Revisão da nota de versão beta.

√ Concordo em orçamento, cronograma, escopo.

Executar o [Ferramenta de compatibilidade de atualização](../../../upgrade/upgrade-compatibility-tool/overview.md)

Considere usar a atualização para resolver problemas identificados pelo [Ferramenta de análise do site](../../../tools/site-wide-analysis-tool/intro.md).

Dependências de documentos e quaisquer alterações técnicas de pilha necessárias, como PHP ou versões Elastic Search.

Reúna a equipe do projeto com certificações da Adobe Commerce.

Criar um plano de comunicação com as partes interessadas.

Janela de manutenção do plano se o tempo de inatividade for antecipado.

Revisar e aprovar a estratégia de testes; considere usar o Adobe Commerce [estrutura de teste](https://developer.adobe.com/commerce/testing/) ou um conjunto de automação de terceiros.

Confirmar se todas as extensões e personalizações são compatíveis.

Revisar e atualizar o manual de pós-lançamento; para ser usado se problemas forem descobertos durante ou após a atualização.

## Pós-implantação

Monitorar o site em busca de problemas - desempenho, processamento de pedidos, análise e outros.

Executar uma Adobe Commerce [verificação de segurança](https://account.magento.com/scanner/dashboard/) ou outra varredura de terceiros e análise de possíveis vulnerabilidades de segurança.

Faça uma retrospectiva com todas as partes interessadas e documente o que deu certo e o que não deu e como melhorar.

Modifique seu plano para a próxima atualização com as lições aprendidas.
