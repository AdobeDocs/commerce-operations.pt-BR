---
title: Visão geral da auto-hospedagem
description: Saiba mais sobre as práticas recomendadas de auto-hospedagem a serem consideradas. Os tópicos variam de elementos de segurança a recuperação de desastres. Estes tópicos estão aqui para ajudar uma empresa que decidiu hospedar sua própria versão do Adobe Commerce. Os itens apresentados não são todos inclusivos, mas devem fornecer uma boa gama de conceitos para promover um site seguro, estável e resiliente.
landing-page-description: Saiba mais sobre alguns conceitos e coisas a serem considerados ao hospedar o Adobe Commerce por conta própria.
short-description: Conheça as estratégias e os conceitos para hospedar o Adobe Commerce sozinho.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Visão geral do Adobe Commerce de auto-hospedagem

Ao considerar a mudança para uma plataforma de comércio eletrônico como o Adobe Commerce, você tem o luxo de opções. No entanto, com essas opções, há custos, riscos e responsabilidades adicionais a serem considerados. A hospedagem de um site do Commerce pode ser feita usando uma solução em pacote, como [Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, onde a infraestrutura, os servidores, o e-mail, os certificados SSL e muitos outros estão pré-configurados e prontos para uso. Encontrar uma boa solução de hospedagem, como o Adobe Commerce na infraestrutura em nuvem, facilita todo o processo. Há motivos convincentes para auto-hospedar seu site do Commerce. Nas páginas de acompanhamento, há muitos tópicos que fornecem insight e orientação sobre os serviços, técnicas e conceitos que a auto-hospedagem oferece. As informações aqui fornecidas não são exaustivas e não se espera que você implemente todas as sugestões. No entanto, esses artigos podem ajudá-lo a entender as ideias e conceitos que podem tornar a auto-hospedagem do Adobe Commerce o mais estável e segura possível.

Quando você não está usando o Adobe Commerce na infraestrutura em nuvem, os termos usados são auto-hospedagem, no local ou até mesmo no local. Local não significa apenas um data center em um prédio de propriedade de uma empresa. Esse termo representa tudo o que não é suporte gerenciado pela Adobe Commerce em sua infraestrutura. Há empresas de hospedagem que atendem ao Adobe Commerce, mas elas também são consideradas como de auto-hospedagem ou no local.

No que diz respeito ao Adobe Commerce e ao Magento Open-source, a maioria dos conselhos e dicas fornecidos funciona em ambas as versões. Mesmo que não diga diretamente, a expectativa é que seja aplicável para ambos. Neste tópico de opções de auto-hospedagem para o Adobe Commerce, ambas as versões são consideradas. Por fim, a maioria dos tópicos é relevante para [Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} está selecionado como o provedor de hospedagem.

## Conjunto de nível de terminologia

Os termos a seguir são comumente usados em todos os artigos do Experience League, ao conversar com a equipe do DevOps e trabalhar com o suporte da empresa:

* **DevOps** é um termo usado para descrever as equipes que lidam com a configuração, gerenciamento, certificados SSL e tudo o mais sobre os servidores e serviços reais usados para executar um site do Adobe Commerce. Esse termo é usado para ajudar a designar quando a responsabilidade de um desenvolvedor normalmente termina e onde a triagem e o suporte de uma equipe de infraestrutura começam.

* **Conceitos de segurança** O abrange vários tópicos e considerações para criar a base de código, os arquivos e o sistema de arquivos do Adobe Commerce nos servidores e quaisquer configurações ou atualizações que reduzam a superfície de ataque para muitos padrões de exploração conhecidos.

* **Ferramentas de monitoramento** O aborda algumas ferramentas e serviços existentes que monitoram os sites da Adobe Commerce. Às vezes, essas ferramentas fornecem dicas sobre como melhorar o sistema ou descobrir problemas e vulnerabilidades de segurança.

* **Recuperação de desastres** O ajuda a fornecer alguns conceitos e considerações para o evento infeliz de um projeto danificado ou explorado.

* **Dicas de desempenho** forneça algumas dicas profissionais e orientação para tornar o aplicativo do Adobe Commerce o mais eficiente possível.

* **Ator inválido** é o termo usado para uma pessoa ou equipe que está tentando fazer algo mal-intencionado ou não autorizado. Não se limita ao aplicativo comercial, mas também se estende à infraestrutura ou a qualquer componente relacionado ao site.

* **Firewall de Aplicativo Web** O (WAF) ajuda observando cada solicitação enviada ao aplicativo de comércio e bloqueia padrões e explorações conhecidos. Geralmente, um WAF é usado em conjunto com regras e filtros personalizados para ajudar a gerenciar ataques de DDOS.

* **Negação de serviço distribuída** (DDoS) é um método de ataque para forçar os servidores que executam o site a serem consumidos com solicitações falsas com volume suficiente para que eles não possam mais responder a solicitações legítimas.

## O que está por vir?

Esses tópicos não estão em nenhuma ordem ou sequência especial. Eles devem fornecer pontos de discussão a um engenheiro de DevOps, ao arquiteto de comércio e a qualquer outra pessoa envolvida na tomada dessa importante decisão sobre onde e como hospedar o Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
