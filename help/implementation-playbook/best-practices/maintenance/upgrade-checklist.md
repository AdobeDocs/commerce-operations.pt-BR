---
title: Práticas recomendadas da lista de verificação de atualização
description: Saiba como criar e usar uma lista de verificação de atualização para planejar sua estratégia de atualização do Adobe Commerce.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Práticas recomendadas da lista de verificação de atualização

Use essa lista de verificação durante suas conversas anuais e trimestrais com a equipe de comércio eletrônico. Muitas empresas trabalham com orçamentos e roteiros anuais. É fundamental, durante essas discussões anuais, que você fale sobre a saúde, a direção e a estratégia de atualização da sua plataforma para o ano, juntamente com como ela se encaixa nas metas gerais e KPIs da empresa. Durante as conversas trimestrais, verifique se o plano anual criado ainda está alinhado à sua situação atual ou dinâmico, se não estiver. A meta desta Lista de verificação do plano de atualização é ajudar você a planejar e agendar atualizações do Adobe Commerce para garantir um processo de atualização bem-sucedido durante o ano. Esta lista de verificação deve ser usada pelos seguintes públicos-alvo para planejamento anual e revisão trimestral:

- Director / TI do gerente
- Gerenciador de comércio eletrônico
- Parceiro/consultor de soluções

>[!NOTE]
>
>Para obter uma descrição detalhada das etapas técnicas para atualizar com êxito, consulte [Concluir pré-requisitos de atualização](../../../upgrade/prepare/prerequisites.md) na documentação do usuário.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

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

Use o [cronograma de lançamento](../../../release/schedule.md) do Adobe Commerce para planejar sua próxima atualização e se preparar antecipadamente.

Discutir qual versão você acha que adotará (completa ou somente segurança) com base nas necessidades previstas.

Separe um orçamento e a capacidade da equipe para a atualização.

## Integrações de terceiros

Revise as integrações atuais de terceiros da Adobe Commerce e suas janelas de manutenção do ano e considere alinhar o trabalho de atualização com sua programação de manutenção.

## Planejamento de escopo e implantação

Atividades de acesso antecipado

- Parceiro participa do [Beta](../../../release/beta.md)
- Revisão das notas de versão do Beta.

√ Concordo em orçamento, cronograma, escopo.

Executar a [Ferramenta de Compatibilidade de Atualização](../../../upgrade/upgrade-compatibility-tool/overview.md)

Considere usar a atualização para resolver problemas identificados pela [Ferramenta de análise abrangente do site](../../../tools/site-wide-analysis-tool/intro.md).

Dependências de documentos e quaisquer alterações técnicas de pilha necessárias, como PHP ou versões Elastic Search.

Reúna a equipe do projeto com certificações da Adobe Commerce.

Criar um plano de comunicação com as partes interessadas.

Janela de manutenção do plano se o tempo de inatividade for antecipado.

Revise e aprove a estratégia de testes; considere usar a [estrutura de testes](https://developer.adobe.com/commerce/testing/) do Adobe Commerce ou um conjunto de automação de terceiros.

Confirmar se todas as extensões e personalizações são compatíveis.

Revisar e atualizar o manual de pós-lançamento; para ser usado se problemas forem descobertos durante ou após a atualização.

## Implantação do Post

Monitorar o site em busca de problemas - desempenho, processamento de pedidos, análise e outros.

~ Execute uma [verificação de segurança](https://account.magento.com/scanner/dashboard/) do Adobe Commerce ou outra verificação de terceiros e revise possíveis vulnerabilidades de segurança.

Faça uma retrospectiva com todas as partes interessadas e documente o que deu certo e o que não deu e como melhorar.

Modifique seu plano para a próxima atualização com as lições aprendidas.
