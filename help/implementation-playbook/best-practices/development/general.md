---
title: Práticas recomendadas de desenvolvimento geral
description: Saiba mais sobre as práticas recomendadas gerais que desenvolvem projetos do Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Práticas recomendadas de desenvolvimento geral do Adobe Commerce

Este tópico descreve a linha de base para um processo de desenvolvimento saudável do Adobe Commerce. Ele descreve processos fundamentais, princípios de codificação e princípios de design de aplicativos para orientar os desenvolvedores.

>[!NOTE]
>
>Os arquitetos técnicos da Adobe usam essas práticas recomendadas como referência durante os contratos que envolvem desenvolvimento.

Essas práticas recomendadas foram desenvolvidas com base em anos de experiência no desenvolvimento e na entrega de projetos do Commerce. A Adobe recomenda que as iniciativas técnicas sigam essas práticas recomendadas e que você melhore os processos e o código existentes para alinhá-los.

## Convenções de texto

As palavras-chave &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHALL NOT&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;RECOMMENDED&quot;, &quot;MAY&quot; e &quot;OPTIONAL&quot; neste tópico devem ser interpretadas conforme descrito em [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Processo

1. Uma metodologia de projeto definida DEVE ser acordada antes do início das atividades do projeto. PODE ser Scrum, Waterfall ou qualquer outra metodologia ou combinação de metodologias, desde que esteja definida.
1. O desenvolvimento NÃO DEVE começar até que uma estratégia de ramificação para o sistema de controle de versão esteja disponível para a equipe de desenvolvimento.
1. O desenvolvimento NÃO DEVE começar até que as especificações técnicas, as histórias de usuários e os casos de uso sejam aprovados, e a aprovação em casos de teste esteja disponível para a equipe de desenvolvimento.
1. O desenvolvimento NÃO DEVE começar até que pelo menos um ambiente de desenvolvimento e controle de qualidade esteja disponível.
1. Os requisitos específicos do projeto que são obrigatórios para o início do desenvolvimento PODEM ser documentados num _Definição de Pronto_.
1. A aprovação DEVE ser feita por um representante do cliente autorizado a aprovar os resultados do projeto.
1. Nas metodologias de projetos Agile, requisitos adicionais PODEM vir após a aprovação. Esses requisitos DEVEM ser tratados como novos requisitos e DEVEM ser capturados, arquitetados e planejados de acordo.
1. Todo o desenvolvimento DEVE ser funcionalmente testado pelo desenvolvedor antes do envio.
1. Todo o desenvolvimento DEVE passar por testes automatizados antes de ser enviado para revisão do código. Isso PODE ser configurado como um processo automatizado após a criação da solicitação de pull.
1. Todo o desenvolvimento DEVE passar pela revisão manual do código por um arquiteto técnico ou desenvolvedor principal antes de ser enviado para o controle de qualidade.
1. Todo o desenvolvimento DEVE passar pela garantia de qualidade antes da entrega ao cliente.
1. Os requisitos específicos do projeto que são obrigatórios para entrega PODEM ser documentados em uma &quot;Definição de Concluído&quot;.

## Ambiente

1. Todos os desenvolvedores DEVEM usar o mesmo IDE. O PhpStorm é o IDE recomendado para o desenvolvimento do Adobe Commerce.
1. Todos os desenvolvedores DEVEM desenvolver e testar usando a mesma pilha de tecnologia usada nos (futuros) servidores de produção. As versões do software nesta pilha de tecnologia DEVEM corresponder às versões principal e secundária do software instalado nos servidores de produção. Consulte [requisitos do sistema](../../../installation/system-requirements.md) para obter detalhes sobre a pilha de tecnologia típica do Adobe Commerce.
1. O administrador do sistema ou arquiteto técnico PODE fornecer à equipe um ambiente de desenvolvimento local mantido centralmente para garantir e promover ambientes locais iguais e atualizados.
1. Os desenvolvedores e engenheiros de controle de qualidade DEVEM ter acesso à linha de comando, ao banco de dados e aos arquivos de registro do ambiente de controle de qualidade. Isso PODE exigir uma conexão VPN.

## Padrões de codificação

1. Todos os códigos DEVEM seguir as convenções de arquitetura, metodologia e padrões de codificação. A criatividade é desejada na função, não na forma.
1. Todos os códigos DEVEM estar em [Guia de arquitetura do Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Todos os códigos DEVEM aderir à [Padrões de codificação do Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/).
1. Todos os códigos DEVEM aderir à [Diretrizes técnicas do Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. Todos os códigos DEVEM implementar a [Práticas recomendadas do Adobe Commerce](../phases.md), se aplicável.
1. Todos os códigos DEVEM aderir à [Padrões do Grupo de interoperabilidade de estrutura PHP (FIG)](https://www.php-fig.org/).
1. Sempre que possível, RECOMENDA-SE a [Visões técnicas do Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/technical-vision/) conta.
1. Todas as integrações com sistemas externos DEVEM ter testes de integração que validem o processo de negócios.
1. Todos os módulos DEVEM ter cobertura de teste. O que testar exatamente DEVE ser determinado pela equipe de desenvolvimento, em colaboração com o arquiteto técnico ou o desenvolvedor principal. Essa determinação DEVE ser baseada em medidas qualitativas e não em medidas quantitativas; uma alta porcentagem de cobertura de código não é um indicador de sucesso, nem implica alta qualidade de código. Em vez disso, determine o risco de não cobrir uma parte do código avaliando a probabilidade e a gravidade das regressões nessa parte do programa.

## Controle de versão

As versões do módulo DEVEM aderir à [Versão semântica 2.0.0 padrão](https://semver.org/).
As dependências na base de código do Adobe Commerce DEVEM seguir o [Diretrizes de dependências de versão do módulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTROLE DE REVISÃO

As confirmações DEVEM ser acompanhadas por mensagens de confirmação significativas.

## Segurança

1. [Funções não seguras](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) NÃO DEVE ser usado.
1. [Estratégias de prevenção XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) DEVE ser aplicada.
1. [Políticas de segurança de conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) DEVE ser aplicada.
1. As novas instâncias do Adobe Commerce DEVEM ser entregues na versão de segurança mais recente de uma versão que ainda não atingiu a data de &quot;Fim das correções de segurança&quot;. Consulte [Política de ciclo de vida do software Adobe Commerce](../../../release/lifecycle-policy.md).
