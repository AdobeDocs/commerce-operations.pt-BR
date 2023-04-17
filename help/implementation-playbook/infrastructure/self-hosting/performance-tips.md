---
title: Dicas de desempenho da Adobe Commerce de auto-hospedagem
description: Saiba mais sobre dicas de desempenho de hospedagem própria, conceitos e práticas recomendadas.
landing-page-description: Saiba mais sobre alguns conceitos e coisas sobre dicas de desempenho ao hospedar o Adobe Commerce por conta própria.
short-description: Conheça estratégias e conceitos de dicas de desempenho para hospedar você mesmo o Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 66abe9f234aa44f7e07cc024607eeb6591a99d07
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---


# Dicas de desempenho da Adobe Commerce de auto-hospedagem

Usar uma plataforma de comércio eletrônico flexível e poderosa não significa que você tenha que sacrificar o desempenho. Desde o início do Adobe Commerce, houve várias melhorias no aplicativo principal. Na versão 2.5.4, a equipe de engenharia da Adobe Commerce realizou um teste de conjunto para fazer o benchmark do aplicativo. Os resultados do teste demonstraram que a Adobe Commerce é capaz de manipular um grande catálogo de mais de 240 milhões de SKUs, os tempos de solicitação da API são em média excepcional de 300 ms, e o número de exibições de página e pedidos feitos por hora são fenomenais chegando em 2 milhões de exibições de página e 208.000 pedidos por hora.

Veja os resultados de benchmark mais recentes passando para [Experience League - Adobe Commerce - Playbook de implementação - Benchmarks](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Para manter as coisas o máximo possível, siga esses padrões ao adicionar personalizações e complexidade adicional ao seu projeto.

As seções a seguir abordam tópicos a serem considerados e conselhos sobre como otimizar sua implementação de hospedagem própria.

## Verniz

Varnish é proxy reverso HTTP com cache. Por mais complicado que isso pareça, o resultado são respostas rápidas para ajudar a garantir que as solicitações sejam retornadas mais rápido do que se tivesse que buscar o item da origem. Executar um site do Adobe Commerce sem alguma versão do Varnish resultará em carregamentos de página mais lentos e outras métricas principais. O verniz pode ser um pouco difícil de se configurar e gerenciar, no entanto temos esse tópico na Experience League [Configurar Varnês](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} para obter uma melhor compreensão do uso com o Adobe Commerce. Uma alternativa é usar uma solução baseada em nuvem. Embora haja muitos a serem considerados, o Fastly foi escolhido como a solução para o Adobe Commerce na nuvem. É uma versão do Fastly, baseada em nuvem, que usa VCLs e muitas facetas de verniz.

Encontrar uma solução que melhor se adapte às suas habilidades técnicas, de configuração, orçamento e de aplicativos é difícil de fazer. O uso de uma opção baseada em nuvem faz com que todas as peças rígidas desapareçam na medida em que são considerados o gerenciamento, a configuração, os servidores e outros componentes da infraestrutura. Ele foi escolhido pela equipe do Adobe Commerce na nuvem como solução devido ao desempenho, escalabilidade, taxa de transferência e muitas outras métricas principais.

Ao escolher uma boa solução para seu projeto em relação à Varnish, você está se configurando para obter o melhor desempenho para seus clientes e salvando o aplicativo de comércio de funcionar mais do que deveria.

## CDN

Além da Varnish ser um ativo valioso para seu projeto do Adobe Commerce, em seguida uma linha é uma CDN. Juntamente com a sua Varnish, uma CDN pode fornecer instâncias em cache para seu CSS, ativos de página, como imagens, para ajudar a reduzir a largura de banda que chega ao seu aplicativo Adobe Commerce. Ele pode armazenar em cache as respostas da GraphQL, aumentando os benefícios de um site sem periféricos do Adobe Commerce. Algumas CDNs fornecem otimização de imagem, um firewall de aplicativo da Web e outros recursos.

O Adobe Commerce na nuvem optou por usar Fastly para seu cache Varnish, mas também como CDN. Essa solução única fornece vários recursos para proporcionar uma excelente experiência para os clientes do Adobe Commerce na nuvem. Você pode ler a visão geral do Fastly Services no Experience League [Visão geral dos serviços com rapidez](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Um CDN fornece conteúdo de entrega otimizado e seguro para o projeto do Adobe Commerce. Sempre que isso não for um componente necessário para o seu projeto, ele deve ser considerado à medida que o seu site amadurece e a quantidade de visitantes aumenta. Ao fornecer uma CDN, você pode atrasar a adição de hardware adicional à infraestrutura ou o dimensionamento da infraestrutura existente devido à carga removida de cada solicitação.

## Desativar Módulos

Desabilitar um módulo que não seja utilizado deve ser considerado, mas não levado de leve. Essa técnica reduz algumas despesas gerais e o tempo de processamento de algumas solicitações, mas há efeitos colaterais que devem ser considerados. Muitas vezes, quando um desenvolvedor faz uma suposição de que um módulo está disponível ao criar a funcionalidade. Isso geralmente é seguro, a menos que optem por usar algumas classes encontradas em um módulo que estava desativado.

Desativar um módulo como o &quot;boletim informativo&quot; nativo é um evento bastante comum. Isso é verdade especialmente quando o proprietário da loja tem uma empresa de terceiros que gerencia seu boletim informativo. Onde isso pode ser um problema é quando um módulo de terceiros é instalado e, por algum motivo, eles decidiram usar uma classe do boletim informativo. Essa dependência acidental provavelmente será detectada durante alguma instalação e teste iniciais, mas você será forçado a decidir se deseja manter esse módulo de terceiros, ativar o boletim informativo e, em seguida, testar a regressão no site procurando por qualquer comportamento estranho introduzido. Ou você encontra uma substituição para esse módulo de terceiros. Ambas as decisões vêm com risco, tempo e possivelmente erros.

Antes de desabilitar os módulos não utilizados, verifique se você não tem testes, como unidade, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} testes de carregamento ou solicitações de API que podem ser afetadas.

## Exigir que os padrões de codificação Adobe Commerce e PHP sejam seguidos para cada solicitação de pull

O Adobe Commerce tem um conjunto de [Padrões de codificação](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Isso ajuda a garantir que um padrão, estilo e design esperado semelhantes sejam seguidos, independentemente do tipo de desenvolvimento de software. Sempre que isso for um requisito de solução a ser seguido é ao contribuir com a base de código do Adobe Commerce. No entanto, seguir essa metodologia para o desenvolvimento personalizado também cria uma base sólida para que todos os desenvolvedores, atuais e futuros, esperem. Ao exigir que todas as solicitações de pull passem um padrão de código, o ajuda a garantir que todos possam entender e esperar os mesmos padrões de desenvolvimento consistentes.

Para acompanhar os padrões de codificação Adobe Commerce, a outra base usada são os padrões básicos de codificação PHP. Ele deve ser claramente definido nos guias do desenvolvedor, quais padrões devem ser seguidos e quaisquer desvios são aceitáveis. No entanto, um fallback deve ser para o guia mantido publicamente em [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Uma posição firme sobre o seguinte PSR-1 e PSR-12. Garantir que os desenvolvedores que contribuem para o projeto sigam essas regras ajuda a garantir que não haja arquivos e padrões estranhamente estruturados. Isso também ajuda a garantir que os desenvolvedores futuros possam ler e entender rapidamente o código que estão revisando. Quanto mais próximo você seguir esses padrões e padrões de codificação, mais fácil será ler e mais rápido será implementar os futuros esforços de desenvolvimento.

## Executar testes de carga após cada implantação

A execução de um teste de carga após cada implantação pode parecer excessiva. No entanto, se essa metodologia for seguida, a oportunidade de novos recursos introduzidos que causam uma diminuição no desempenho poderá ser rastreada e atenuada.

Além de detectar a degradação no desempenho do novo código, ter uma referência histórica das métricas principais do site pode ajudar a fornecer informações sobre quando uma nova ferramenta ou infraestrutura de alteração está ativada. Por exemplo, antes de pagar a empresa de hospedagem para dimensionar seu ambiente e esperar que você esteja obtendo o aumento de desempenho esperado, você pode configurar um ambiente de preparo com as novas configurações e executar um teste de carregamento para ver qual seria o resultado real.

Esses testes podem ser automatizados e parte do pipeline de CI/CD. Devido a isso, também é possível ter regras em vigor que obtêm os resultados e possivelmente bloqueiam a mesclagem do recurso se ocorrer muito desvio em relação à norma. O número de casos de uso para esses dados é ilimitado, mas sem iniciar esse processo você pode nunca realizar seu potencial.

A Adobe Commerce tem um bom texto sobre esse tópico encontrado no Experience League [Dicas para testes de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
