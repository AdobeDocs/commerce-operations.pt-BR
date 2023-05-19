---
title: Dicas de desempenho para auto-hospedagem da Adobe Commerce
description: Saiba mais sobre as dicas de desempenho de auto-hospedagem, ideias e conceitos e práticas recomendadas a serem consideradas.
landing-page-description: Saiba mais sobre alguns conceitos e coisas a serem considerados sobre dicas de desempenho ao hospedar o Adobe Commerce por conta própria.
short-description: Conheça os conceitos de estratégias e dicas de desempenho para hospedar você mesmo o Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Dicas de desempenho do Adobe Commerce para auto-hospedagem

Usar uma plataforma de comércio eletrônico flexível e poderosa não significa que você precise sacrificar o desempenho. Houve várias melhorias no aplicativo principal desde o início da Adobe Commerce. Na versão 2.5.4, a equipe de engenharia do Adobe Commerce executou um teste definido para fazer o benchmark do aplicativo. Os resultados do teste demonstraram que o Adobe Commerce é capaz de lidar com um grande catálogo de mais de 240 milhões de SKUs, os tempos de solicitação de API são excepcionais, em média, 300 ms, e o número de exibições de página e pedidos feitos por hora é fenomenal, chegando a 2 milhões de exibições de página e 208.000 pedidos por hora.

Veja os resultados mais recentes do benchmark por título para [Experience League - Adobe Commerce - Manual de implementação - Benchmarks](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Para manter as coisas o melhor possível, siga esses padrões ao adicionar personalizações e complexidade adicional ao seu projeto.

As seções a seguir abordam tópicos a serem considerados e conselhos sobre como otimizar a implementação de auto-hospedagem.

## Verniz

O verniz é um proxy reverso HTTP com cache. Por mais complicado que isso pareça, o resultado são respostas rápidas para ajudar a garantir que as solicitações sejam retornadas mais rapidamente do que se tivesse que buscar o item na origem. A execução de um site do Adobe Commerce sem alguma versão do Verniz resultará em carregamentos de página mais lentos e outras métricas principais. O verniz pode ser um pouco difícil de configurar e gerenciar a si mesmo, no entanto, temos este tópico no Experience League [Configurar verniz](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} para entender melhor seu uso com o Adobe Commerce. Uma alternativa é usar uma solução baseada em nuvem. Embora existam muitos a serem considerados, o Fastly foi escolhido como a solução para o Adobe Commerce na nuvem. É uma versão do Fastly, baseado em nuvem, que usa VCLs e muitas facetas do verniz.

Encontrar uma solução que melhor se adapte aos seus aplicativos, configurações, orçamentos e habilidades técnicas é difícil. Usar uma opção baseada em nuvem faz com que todas as partes rígidas desapareçam, desde que o gerenciamento, a configuração, os servidores e outros componentes da infraestrutura sejam considerados. Ele foi escolhido pela equipe do Adobe Commerce na nuvem como sua solução devido ao desempenho, escalabilidade, taxa de transferência e muitas outras métricas principais.

Ao escolher uma boa solução para seu projeto em relação ao Verniz, você está se configurando para o melhor desempenho para seus clientes e evitando que o aplicativo de comércio trabalhe mais do que deve.

## CDN

Além de o verniz ser um ativo valioso para seu projeto do Adobe Commerce, o próximo na linha é um CDN. Junto com seu Verniz, um CDN pode fornecer instâncias em cache para o CSS, ativos de página, como imagens, para ajudar a reduzir a largura de banda que chega ao aplicativo do Adobe Commerce. Ele pode armazenar em cache as respostas do GraphQL, aumentando os benefícios de um site headless do Adobe Commerce. Algumas CDNs fornecem otimização de imagem, um firewall de aplicativo da Web e outros recursos.

O Adobe Commerce na nuvem optou por usar o Fastly como cache Varnish, mas também como CDN. Essa solução única oferece uma variedade de recursos para proporcionar uma ótima experiência para a Adobe Commerce em clientes na nuvem. Você pode ler a visão geral dos serviços Fastly no Experience League [Visão geral dos serviços Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Uma CDN fornece conteúdo de entrega otimizado e seguro para o projeto do Adobe Commerce. Quando esse não for um componente obrigatório do seu projeto, deverá ser considerado à medida que o site amadurecer e a quantidade de visitantes aumentar. Ao fornecer um CDN, você pode atrasar a adição de hardware adicional à infraestrutura ou o dimensionamento da infraestrutura existente devido à carga removida de cada solicitação.

## Desativar módulos

A desativação de um módulo que não é usado deve ser considerada, mas não deve ser levada a sério. Essa técnica não reduz a sobrecarga e o tempo de processamento de algumas solicitações, mas há efeitos colaterais que devem ser considerados. Geralmente, há momentos em que um desenvolvedor assume que um módulo está disponível ao criar a funcionalidade. Isso geralmente é seguro, a menos que optem por usar algumas classes encontradas em um módulo que foi desativado.

Desativar um módulo, como o &quot;boletim informativo&quot; nativo, é um evento bastante comum. Isso é verdade especialmente quando o proprietário da loja tem uma empresa de terceiros que gerencia seu boletim informativo. Isso pode ser um problema quando um módulo de terceiros é instalado e, por algum motivo, eles decidiram usar uma classe do informativo. Essa dependência acidental provavelmente será capturada durante alguma instalação inicial e teste, mas você será forçado a decidir se deseja manter esse módulo de terceiros, ativar o boletim informativo e testar a regressão no site procurando por qualquer comportamento estranho introduzido. Ou você encontra uma substituição para esse módulo de terceiros. Ambas as decisões vêm com risco, tempo e possivelmente bugs.

Antes de desativar módulos não utilizados, certifique-se de que você não tenha nenhum teste, como unidade, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} testes de carga ou solicitações de API que podem ser afetadas.

## Exigir que os padrões de codificação Adobe Commerce e PHP sejam seguidos para cada solicitação pull

O Adobe Commerce tem um conjunto de [Padrões de codificação](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Isso ajuda a garantir que um padrão, estilo e design esperado semelhantes sejam seguidos, independentemente do tipo de desenvolvimento de software. Ao contribuir para a base de código do Adobe Commerce, isso é um requisito. No entanto, se você optar por seguir essa metodologia para o desenvolvimento personalizado, o estabelecerá uma base sólida para todos os desenvolvedores, atuais e futuros. Ao solicitar que todas as solicitações de pull passem por um padrão de código, você ajuda a garantir que todos possam entender e esperar os mesmos padrões de desenvolvimento consistentes.

Para acompanhar os padrões de codificação do Adobe Commerce, a outra base usada é os padrões básicos de codificação do PHP. Os guias do desenvolvedor devem definir claramente quais padrões você deve seguir e quaisquer desvios aceitáveis. No entanto, um fallback deve ser para o guia mantido publicamente encontrado em [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Uma posição firme sobre o seguimento da PSR-1 e da PSR-12. Garantir que os desenvolvedores que contribuem para o projeto sigam essas etapas ajuda a garantir que não haja arquivos e padrões estranhamente estruturados. Isso também ajuda a garantir que os futuros desenvolvedores possam ler e entender rapidamente o código que estão revisando. Quanto mais próximos você seguir esses padrões e padrões de codificação, os esforços de desenvolvimento futuros deverão ser mais fáceis de ler e mais rápidos de implementar.

## Executar testes de carga após cada implantação

A execução de um teste de carga após cada implantação pode parecer excessiva. No entanto, se essa metodologia for seguida, a oportunidade de recursos recém-introduzidos que causam uma queda no desempenho poderá ser rastreada e atenuada.

Além de detectar a degradação do desempenho pelo novo código, ter uma referência histórica de métricas principais do seu site pode ajudar a fornecer informações sobre quando uma nova ferramenta ou infraestrutura de alteração é ativada. Por exemplo, antes de pagar à empresa de hospedagem para aumentar seu ambiente e esperar que você obtenha o aumento de desempenho esperado, é possível configurar um ambiente de preparo com as novas configurações e executar um teste de carga para ver qual seria o resultado real.

Esses testes podem ser automatizados e fazer parte do pipeline de CI/CD. Devido a isso, você também pode ter regras em vigor que obtenham os resultados e potencialmente bloqueiem a mesclagem de recursos se ocorrer um desvio excessivo em relação à norma. O número de casos de uso para esses dados é ilimitado, mas sem iniciar esse processo, você pode nunca realizar seu potencial.

A Adobe Commerce tem um bom writeup sobre este tópico encontrado no Experience League [Dicas para testes de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
