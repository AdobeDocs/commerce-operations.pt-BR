---
title: Visão geral da auto-hospedagem
description: Saiba mais sobre as práticas recomendadas de hospedagem própria a serem consideradas. Os tópicos vão desde elementos de segurança, até desastres, recuperam muito mais. Estes tópicos estão aqui para ajudar uma empresa que decidiu hospedar sua própria versão do Adobe Commerce. Os itens apresentados não são todos inclusivos, mas devem fornecer uma boa variedade de conceitos para promover um site seguro, estável e resiliente.
landing-page-description: Saiba mais sobre alguns conceitos e coisas a serem considerados ao hospedar o Adobe Commerce por conta própria.
short-description: Saiba mais sobre as estratégias e os conceitos para hospedar o Adobe Commerce por conta própria.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# Visão geral da Adobe Commerce de auto-hospedagem

Ao considerar a mudança para uma plataforma de comércio eletrônico como a Adobe Commerce, você tem o luxo de opções. No entanto, com estas opções, vêm custos, riscos e responsabilidades adicionais a serem considerados. A hospedagem de um site de Comércio pode ser feita usando uma solução em pacote, como [Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, em que a infraestrutura, os servidores, o email, os certificados SSL e muitos outros são pré-configurados e prontos para uso. Encontrar uma boa solução de hospedagem, como o Adobe Commerce na infraestrutura em nuvem, facilita todo o processo, há motivos convincentes para auto-hospedar seu site do Commerce. Nas páginas de acompanhamento, há muitos tópicos que fornecem insight e orientação sobre os serviços, técnicas e conceitos fornecidos pela hospedagem própria. As informações aqui não são exaustivas e não é esperado que você implemente todas as sugestões. No entanto, esses artigos podem ajudá-lo a entender as ideias e os conceitos que podem tornar a hospedagem própria do Adobe Commerce tão estável e segura quanto possível.

Quando você não está usando o Adobe Commerce na infraestrutura de nuvem, os termos usados são auto-hospedagem ou no local, ou até mesmo no local. No local não se trata apenas de um centro de dados de um edifício de uma empresa. Esse termo representa qualquer coisa que não é gerenciada pelo Adobe Commerce em sua infraestrutura. Há empresas de hospedagem que atendem à Adobe Commerce e também são consideradas hospedagem própria ou no local.

Com relação ao Adobe Commerce e ao Magento Open-source, a maioria das recomendações e dicas fornecidas funciona em qualquer versão. Mesmo que não o afirme diretamente, a expectativa é que seja aplicável para ambos. Dentro desse tópico de opções de hospedagem própria para o Adobe Commerce, ambas as versões são consideradas. E finalmente, a maioria dos tópicos são relevantes para [Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} é selecionado como o provedor de hospedagem.

## Conjunto de níveis de terminologia

Os termos a seguir geralmente são usados em artigos do Experience League, ao conversar com a equipe DevOps e ao trabalhar com o suporte da empresa:

* **DevOps** é um termo usado para descrever as equipes que lidam com a configuração, a gestão, os certificados SSL e tudo o mais sobre os servidores e serviços reais usados para executar um site da Adobe Commerce. Esse termo é usado para ajudar a designar quando a responsabilidade de um desenvolvedor normalmente termina e onde começa a triagem e o suporte de uma equipe de infraestrutura.

* **Conceitos de segurança** Abrange vários tópicos e considerações para tornar a base de código, os arquivos e o sistema de arquivos do Adobe Commerce nos servidores e quaisquer configurações ou atualizações que reduzam a superfície do ataque para muitos padrões de exploração conhecidos.

* **Ferramentas de monitoramento** O aborda algumas ferramentas e serviços existentes que monitoram os sites da Adobe Commerce. Essas ferramentas às vezes podem fornecer dicas sobre como melhorar as coisas, ou descobrir problemas e vulnerabilidades de segurança.

* **Recuperação de desastres** ajuda a fornecer alguns conceitos e considerações para o caso infeliz de um projeto danificado ou explorado.

* **Dicas de desempenho** forneça algumas dicas pro e orientações para fazer com que o aplicativo Adobe Commerce seja o mais eficiente possível.

* **Mau ator** é o termo usado para uma pessoa ou equipe que está tentando fazer algo mal-intencionado ou não autorizado. Não está limitado ao aplicativo comercial, mas também se estende à infraestrutura ou a qualquer componente relacionado ao site.

* **Firewall do Aplicativo Web** (WAF) ajuda ao assistir a cada cabeçalho de solicitação no aplicativo de comércio e bloquear padrões e explorações conhecidos. Geralmente, um WAF é usado junto com filtros e regras personalizados para ajudar a gerenciar ataques de DDOS.

* **Negação de Serviço Distribuída** (DDoS) é um método de ataque para forçar os servidores que executam o site a serem consumidos com solicitações falsas com volume suficiente que eles não podem mais responder a solicitações legítimas.

## O que está por vir?

Esses tópicos não estão em nenhuma ordem ou sequência especial. Elas têm o objetivo de fornecer pontos de conversa com um engenheiro DevOps, o Arquiteto de Comércio, e qualquer outra pessoa envolvida em tomar essa importante decisão de onde e como hospedar o Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
