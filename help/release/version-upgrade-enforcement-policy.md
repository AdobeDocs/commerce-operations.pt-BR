---
title: Política de Imposição de Atualização de Versão da Nuvem
description: Saiba mais sobre a imposição de atualização de versão do Adobe Commerce na nuvem — por que a Adobe impõe atualizações, datas de imposição, desativação e ações necessárias. Consulte a política de ciclo de vida para obter disposições transitórias e caminhos de migração.
nudge: true
source-git-commit: eacee993ec38cce7763d4c99b1bbb67a319d8c1a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Política de imposição de atualização de versão para Adobe Commerce na nuvem

Quando o suporte regular e o suporte estendido terminam para uma versão do Adobe Commerce, a Adobe se reserva o direito de desativar o Adobe Commerce em ambientes na nuvem que ainda estejam executando essa versão não compatível. A aplicação de atualização de versão se aplica somente a ambientes do Adobe Commerce na nuvem; os clientes locais gerenciam sua própria infraestrutura.

Você deve mudar para uma versão com suporte do Adobe Commerce ou migrar para o [!DNL Adobe Commerce as a Cloud Service] antes da data publicada de [fim do suporte estendido](lifecycle-policy.md#end-of-support-dates) para sua linha de lançamento.

As seções a seguir explicam por que o Adobe impõe atualizações, como as datas de imposição são calculadas e o que acontece na data de imposição. Para obter as datas de imposição específicas da versão, consulte a tabela [Fim das datas de suporte](lifecycle-policy.md#end-of-support-dates) na política de ciclo de vida.

>[!NOTE]
>
>Este tópico aborda somente a imposição de atualização da nuvem. Para obter definições de camada de suporte, a tabela [fim das datas de suporte](lifecycle-policy.md#end-of-support-dates), [disposições transitórias de segurança](lifecycle-policy.md#security-only-transitional-period), [dependências de software de terceiros](lifecycle-policy.md#platform-dependencies), [fim da vida útil do PHP e conformidade com o PCI](lifecycle-policy.md#php-end-of-life-and-pci-compliance) e [opções de atualização e migração](lifecycle-policy.md#upgrade-and-migration-options), consulte a [política de ciclo de vida](lifecycle-policy.md). Além de atualizar para uma versão compatível do Adobe Commerce, a Adobe também exige que você mantenha as dependências de software de terceiros em versões ativamente compatíveis.

## Por que a Adobe está introduzindo esta política

A Adobe é responsável pela segurança e conformidade da infraestrutura de plataforma hospedada em que os clientes do Adobe Commerce na nuvem são executados. Isso inclui manter todas as dependências de software subjacentes atualizadas, aplicar patches de segurança e atender aos padrões de conformidade, como o PCI, dos quais os clientes dependem.

Quando o suporte de segurança para dependências de software subjacentes é oficialmente encerrado pelos fornecedores, a Adobe não pode mais fornecer o nível necessário de cobertura de segurança e suporte à plataforma. Continuar a administrar lojas em infraestruturas não compatíveis coloca os clientes, seus compradores e a Adobe em riscos inaceitáveis. Portanto, o Adobe está introduzindo uma política formal de aplicação de atualização de versão que define quando os ambientes do Adobe Commerce na nuvem que executam versões do Commerce não compatíveis serão descontinuados.

## Como as datas de imposição de atualização são calculadas

Para cada linha de versão do Adobe Commerce, a data de imposição da atualização é calculada da seguinte maneira:

**Data de imposição da atualização** = Data de disponibilidade geral + 3 anos de suporte regular + até 1 ano de suporte estendido

O suporte estendido é anunciado próximo ao fim do suporte regular para cada linha de versão.

## O que acontece na data de imposição de atualização da versão

Na data de imposição de atualização publicada, o Adobe interromperá a manutenção de todos os ambientes do Adobe Commerce na nuvem que ainda estejam executando a versão de lançamento afetada e reservará o direito de desativá-los. Você receberá notificações antecipadas em marcos importantes até a data de imposição de atualização da versão. O Adobe fornecerá uma janela de exportação de dados antes da desativação do ambiente para que você possa recuperar os dados.

A primeira data de imposição sob esta política é **1º de junho de 2027**, para linhas de versão que atingem o fim do suporte estendido antes dessa data. Consulte a tabela [Fim das datas de suporte](lifecycle-policy.md#end-of-support-dates) para obter as datas de imposição específicas da versão.
