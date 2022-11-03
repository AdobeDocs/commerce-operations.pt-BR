---
title: Práticas recomendadas da lista de verificação de atualização
description: Saiba como criar e usar uma lista de verificação de atualização para planejar sua estratégia de atualização do Adobe Commerce e do Magento Open Source.
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 644970b350c7591896f7c00d4c94661c76495c73
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Práticas recomendadas da lista de verificação de atualização

Use essa lista de verificação durante suas conversas anuais e trimestrais com sua equipe de comércio eletrônico. Muitas empresas trabalham com orçamentos e roteiros anuais. É fundamental, durante essas discussões anuais, que você fale sobre a integridade, a direção e a estratégia de atualização da sua plataforma para o ano, juntamente com a forma como ela se encaixa nas metas gerais e KPIs dos negócios. Durante as conversas trimestrais, verifique se o plano anual criado ainda está alinhado com sua situação atual ou pivô, caso não esteja. O objetivo desta Lista de Verificação do Plano de Atualização é ajudar você a planejar e agendar atualizações da Adobe Commerce para garantir um processo de atualização bem-sucedido durante o ano. Esta lista de verificação deve ser utilizada pelos seguintes públicos-alvo para o planeamento anual e a análise trimestral:

- Director / Gerente de TI
- eCommerce Manager
- Parceiro/consultor de soluções

>[!NOTE]
>
>Para obter uma descrição detalhada das etapas técnicas para atualizar com êxito, consulte [Concluir pré-requisitos de atualização](../../../upgrade/prepare/prerequisites.md) na documentação do usuário.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Metas

▢ Analise os KPIs atuais e ajuste-os conforme necessário.

## Extensões e personalizações

▢ Revise todas as extensões e personalizações atuais e verifique se elas ainda são necessárias com base nos requisitos de negócios.

▢ Considere a substituição de extensões que não têm um bom registro de atualização das versões do Adobe Commerce.

## Equipe

▢ Certifique-se de ter a equipe certa em vigor com as certificações e conjuntos de habilidades adequados da Adobe Commerce.

## Orçamento e Tempo

▢ Usar a Adobe Commerce [cronograma de lançamento](../../../release/schedule.md) para planejar sua próxima atualização e se preparar com antecedência.

▢ Discuta qual versão você acha que adotará (completa ou somente para segurança) com base nas necessidades antecipadas.

▢ Defina um orçamento e a capacidade da equipe para a atualização.

## Integrações de terceiros

▢ Revise as integrações atuais de terceiros da Adobe Commerce e suas janelas de manutenção para o ano e considere alinhar o trabalho de atualização com sua programação de manutenção.

## Planejamento de Escopo e Implantação

▢ Atividades de acesso antecipado

- Parceiro participa do [Beta](../../../release/beta-program.md)
- Revisão da nota de versão beta.

▢ Concordar com orçamento, linha do tempo e escopo.

▢ Executar o [Ferramenta de compatibilidade de atualização](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Considere usar a atualização para solucionar os problemas identificados pela [Ferramenta de análise do site](../../../tools/site-wide-analysis-tool/intro.md).

▢ Dependências do documento e quaisquer alterações de pilha técnica necessárias, como versões PHP ou Elastic Search.

▢ Colete a equipe do projeto com certificações da Adobe Commerce.

▢ Criar plano de comunicação das partes interessadas.

▢ janela de manutenção do plano se o tempo de inatividade for antecipado.

▢ revisão e aprovação da estratégia de ensaio; considere usar a Adobe Commerce [estrutura de teste](https://developer.adobe.com/commerce/testing/) ou um conjunto de automação de terceiros.

▢ Confirme se todas as extensões e personalizações são compatíveis.

▢ e atualize o playbook após o lançamento; a ser usado se forem detectados problemas durante ou após a atualização.

## Pós-implantação

▢ monitore o site para problemas - desempenho, processamento de pedidos, análises e outros.

▢ Executar uma Adobe Commerce [verificação de segurança](https://account.magento.com/scanner/dashboard/) ou de outros terceiros, examinem possíveis vulnerabilidades de segurança.

▢ Realize uma retrospectiva com todas as partes interessadas e documente o que deu certo e o que não deu e como melhorar.

▢ Modifique seu plano para a próxima atualização com as lições aprendidas.
