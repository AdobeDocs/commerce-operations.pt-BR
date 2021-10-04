---
title: Otimização do desempenho AEM
description: Otimize sua configuração padrão do Adobe Experience Manager para suportar cargas altas no Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Otimização do desempenho AEM

O AEM dispatcher é um proxy reverso, que ajuda a fornecer um ambiente rápido e dinâmico. Funciona como parte de um servidor HTML estático, como o Apache HTTP Server, com o objetivo de armazenar (ou &quot;armazenar em cache&quot;) o máximo possível do conteúdo do site, na forma de recursos estáticos. Essa abordagem tem como objetivo minimizar a necessidade de acessar a funcionalidade de renderização da página de AEM e o serviço GraphQL do Adobe Commerce, tanto quanto possível. O resultado de servir grande parte das páginas como HTML estático, CSS e JS oferece benefícios de desempenho para os usuários e reduz os requisitos de infraestrutura no ambiente. Qualquer página ou consulta que provavelmente será repetida de forma idêntica de usuário para usuário deve ser considerada para armazenamento em cache.

As seções a seguir mostram em alto nível a área de foco técnico recomendada a ser revisada para permitir o armazenamento em cache efetivo em AEM em um ambiente de CIF/Adobe Commerce.

## Armazenamento em cache com base em TTL em AEM dispatchers

Armazenar em cache o máximo possível do site nos dispatchers é uma prática recomendada para qualquer projeto AEM. O uso da invalidação de cache com base em tempo armazenará em cache as páginas da CIF renderizadas do lado do servidor por um período definido e limitado. Depois que o tempo definido expirar, a próxima solicitação recriará a página do editor de AEM e do GraphQL do Adobe Commerce e a armazenará no cache do dispatcher novamente até a próxima invalidação.

O recurso de armazenamento em cache TTL pode ser configurado no AEM com o uso do componente &quot;Dispatcher TTL&quot; no pacote ACS AEM Commons e a configuração /enableTTL &quot;1&quot; no arquivo de configuração dispatcher.any.

Se estiver habilitado, o dispatcher avaliará os cabeçalhos de resposta do backend e, se eles contiverem uma data de max ou Expires do Cache-Control, um arquivo auxiliar vazio ao lado do arquivo de cache será criado, com o tempo de modificação igual à data de expiração. Quando o arquivo em cache é solicitado depois do tempo de modificação, ele é automaticamente solicitado novamente no back-end. Isso proporciona um mecanismo de armazenamento em cache eficaz, que não requer intervenção ou manutenção manual, uma vez que o TTL (Product Update delay, atraso de atualização do produto) tenha sido reconhecido e aceite pelas partes interessadas.

## Armazenamento em cache do navegador

A abordagem TTL do dispatcher acima reduzirá bastante as solicitações e o carregamento no editor, no entanto, há alguns ativos que provavelmente não serão alterados e, portanto, até mesmo as solicitações para o dispatcher podem ser reduzidas com o armazenamento de arquivos relevantes em cache localmente no navegador de um usuário. Por exemplo, o logotipo do site, que é exibido em cada página no site no modelo do site, não precisaria ser solicitado sempre para o dispatcher. Isso pode ser armazenado no cache do navegador do usuário. A redução nos requisitos de largura de banda para cada carregamento de página teria um grande impacto na capacidade de resposta do site e no tempo de carregamento de página.

O armazenamento em cache no nível do navegador é comumente feito através do &quot;Cache-Control: cabeçalho de resposta max-age=&quot; . A configuração de maxage informa ao navegador em quantos segundos ele deve armazenar o arquivo em cache antes de tentar &quot;revalidar&quot; ou solicitá-lo novamente ao site. Esse conceito de cache max-age é comumente chamado de &quot;Expiração do Cache&quot; ou TTL (&quot;Time to Live&quot;). Fornecer experiências comerciais em escala - Com o Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Algumas áreas de um site de comércio AEM/CIF/Adobe que podem ser configuradas para serem armazenadas em cache no navegador do cliente incluem:

- Imagens (no próprio modelo de AEM, por exemplo, o logotipo do site e as imagens de design de modelo - as imagens de produtos de catálogo seriam chamadas do Adobe Commerce via Fastly, o armazenamento dessas imagens em cache é discutido posteriormente)
- Arquivos HTML (para páginas alteradas raramente - página de termos e condições etc.)
- Arquivos CSS
- Todos os arquivos JavaScript do site, incluindo arquivos JavaScript da CIF

## Otimização do período de carência e do statfilelevel do Dispatcher

A configuração padrão do dispatcher usa a configuração /statfilelevel &quot;0&quot; - isso significa que um único arquivo &quot;.stat&quot; é colocado na raiz do diretório htdocs (diretório raiz do documento). Se uma alteração for feita em uma página ou arquivo no AEM, a hora de modificação desse único arquivo stat será atualizada até o momento da alteração. Se a hora for mais recente do que a hora de modificação do recurso, o dispatcher considerará que todos os recursos são invalidados e qualquer solicitação subsequente para um recurso invalidado acionará uma chamada para a instância de publicação. Portanto, basicamente, com essa configuração, cada ativação invalidará todo o cache.

Para qualquer site, especialmente sites de comércio com carga pesada, isso colocaria uma quantidade desnecessária de carga no nível de publicação do AEM para toda a estrutura do site para se tornar invalidada com apenas uma única atualização de página.

Em vez disso, a configuração statfilelevel pode ser modificada para um valor maior, correspondente à profundidade dos subdiretórios no diretório htdocs do diretório raiz do documento, de modo que, quando um arquivo localizado em um determinado nível for invalidado, somente os arquivos nesse nível de diretório .stat e abaixo serão atualizados.

Por exemplo: digamos que você tenha um modelo de página de produto em:

```
content/ecommerce/us/en/products/product-page.html
```

Cada nível de pasta teria &quot;nível de estatística&quot; - conforme mostrado na tabela acima.

| conteúdo (docroot) | comércio eletrônico | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

Nesse caso, se você tiver deixado a propriedade statfilelevel definida como padrão &quot;0&quot; e o modelo product-page.html for atualizado e ativado, acionando uma invalidação, cada arquivo .stat do docroot para o nível 4 será tocado, e os arquivos serão invalidados, causando uma nova solicitação das instâncias de publicação de AEM para todas as páginas no site (incluindo outros sites, países e idiomas) dessa única alteração.

No entanto, se a propriedade statfilelevel estiver definida como nível 4 e uma alteração for feita no product-page.html, somente o arquivo .stat no diretório de produtos desse site/país/idioma específico será tocado.

Observe que o nível de arquivo .stat não deve ser definido para um nível muito alto - exceder 20 pode ter impactos no desempenho. A execução de uma ativação de arquivo em massa durante a execução de um teste de desempenho deve fornecer o nível correto ao qual você deve ajustar o nível de stat.

Outra configuração do dispatcher a ser otimizada ao configurar o statfilelevel é a configuração caracteressPeriod. Isso define o número de segundos em que um recurso obsoleto e invalidado automaticamente ainda pode ser distribuído do cache após a última ativação. Os recursos invalidados automaticamente são invalidados por qualquer ativação (quando o caminho corresponde à seção dispatcher /invalidate e ao nível especificado na propriedade statfileslevel). A definição de período de carência como 2 segundos pode ser usada para impedir um cenário em que várias solicitações são enviadas continuamente para o editor, mesmo que o editor ainda esteja no processo de criar a nova página.

>[!NOTE]
>
> Leitura mais detalhada sobre esse tópico está disponível no repositório GitHub [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod).

## CIF - Armazenamento em cache GraphQL via componentes

Os componentes individuais dentro do AEM podem ser definidos para serem armazenados em cache, o que significa que a solicitação GraphQL para o Adobe
O Commerce é chamado uma vez e as solicitações subsequentes, até o limite de tempo configurado, são recuperadas do cache de AEM e não colocam mais carga no Adobe Commerce. Os exemplos seriam uma navegação de site com base em uma árvore de categoria mostrada em cada página e opções em uma funcionalidade de pesquisa facetada - essas são apenas duas áreas que exigem a criação de consultas intensivas de recursos no Adobe Commerce, mas provavelmente não mudariam regularmente e, portanto, seriam boas opções para o armazenamento em cache. Dessa forma, por exemplo, mesmo quando um PDP ou PLP está sendo recriado pelo editor, a solicitação GraphQL com uso intenso de recursos para a build de navegação não atingiria o Adobe Commerce e poderia ser recuperada do cache GraphQL AEM CIF.

Um exemplo abaixo é para o componente de navegação ser armazenado em cache porque ele envia a mesma consulta GraphQL em todas as páginas do site. A solicitação abaixo armazena em cache as 100 entradas anteriores por 10 minutos para a estrutura de navegação:

```
venia/components/structure/navigation:true:100:600
```

O exemplo abaixo armazena em cache as 100 opções de pesquisa facetadas anteriores em uma página de pesquisa por 1 hora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

A solicitação, incluindo todos os cabeçalhos http personalizados e variáveis, deve corresponder exatamente para que o cache seja &quot;hit&quot; e para evitar uma chamada repetida para o Adobe Commerce. Observe que, uma vez definido, não há uma maneira fácil de invalidar manualmente esse cache. Isso pode significar, portanto, que se uma nova categoria for adicionada no Adobe Commerce, ela não começará a aparecer na navegação até que o tempo de expiração definido no cache acima tenha expirado e a solicitação GraphQL seja atualizada. O mesmo para aspectos de pesquisa. No entanto, tendo em conta os benefícios de desempenho a serem alcançados por este armazenamento em cache, este é geralmente um compromisso aceitável.

As opções de armazenamento em cache acima podem ser definidas usando o console de configuração OSGi AEM no &quot;Cliente GraphQL
Fábrica de configuração&quot;. Cada entrada de configuração de cache pode ser especificada com o seguinte formato:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Armazenamento em cache híbrido — solicitações GraphQL do lado do cliente em páginas do dispatcher em cache

Também é possível uma abordagem híbrida para o armazenamento de páginas em cache: é possível que uma página da CIF contenha componentes que sempre solicitem as informações mais recentes do Adobe Commerce diretamente do navegador do cliente. Isso pode ser útil para áreas específicas da página em um modelo, que são importantes para serem atualizadas com informações em tempo real: Preços do produto dentro de um PDP, por exemplo. Quando os preços são alterados com frequência devido à correspondência dinâmica de preços, essas informações podem ser configuradas para não serem armazenadas em cache no dispatcher, em vez de serem obtidas no lado do cliente, no navegador do cliente, a partir do Adobe Commerce diretamente por meio de APIs GraphQL com AEM componentes da Web da CIF.

Isso pode ser configurado através das configurações dos componentes do AEM - para informações de Preço em páginas de lista de produtos, isso pode ser configurado no modelo da lista de produtos, selecionando o componente de lista de produtos nas configurações da página e marcando a opção &quot;preços de carregamento&quot;. A mesma abordagem funcionaria para os níveis de existências.

Os métodos acima referidos só devem ser utilizados nos casos em que a informação em tempo real e constantemente atualizada constitua um requisito. No exemplo acima, com os preços, poderia ser acordado com as partes interessadas da empresa atualizar os preços somente diariamente em tempos de tráfego baixos e realizar a operação de liberação de cache em seguida. Isso removeria a necessidade de solicitações de informações de preço em tempo real e a carga extra subsequente no Adobe Commerce ao criar cada página exibindo informações de preço.

## Solicitações GraphQL inacessíveis

Os componentes de dados dinâmicos específicos nas páginas não devem ser armazenados em cache e sempre exigirão uma chamada GraphQL para o Adobe Commerce, como para o carrinho de compras e chamadas em todas as páginas de check-out. Essas informações são específicas de um usuário e são alteradas constantemente devido à atividade do cliente no site, por exemplo, ao adicionar produtos ao carrinho de compras.

Os resultados da consulta GraphQL não devem ser armazenados em cache para clientes conectados se o design do site fornecer respostas diferentes com base na função do usuário. Por exemplo, você pode criar vários grupos de clientes e configurar diferentes preços do produto ou diferentes visibilidade da categoria do produto para cada grupo. O armazenamento em cache de resultados como esses pode fazer com que os clientes vejam os preços de outro grupo de clientes ou tenham categorias incorretas exibidas.

## Ignorando parâmetros de rastreamento no cache AEM dispatcher

Os sites de comércio eletrônico podem direcionar tráfego para seu site usando anúncios de pesquisa PPC ou campanhas de mídia social.

O uso dessas mídias significa que uma ID de rastreamento é adicionada ao link de saída dessa plataforma. Por exemplo, o Facebook adicionará uma ID de clique do Facebook (fbclid) ao URL; os Google Adverts adicionarão uma ID de clique do Google (gclid); isso fará com que os links de entrada na sua frente do AEM sejam exibidos como os abaixo, como exemplo:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

A gclid e a fbclid serão alteradas com cada usuário que clicar no anúncio, isso se destina ao rastreamento, mas com suas configurações padrão, AEM veria cada solicitação como uma página exclusiva, o que ignoraria o dispatcher e geraria carga extra desnecessária no publicador e no Adobe Commerce.

Durante um evento de aumento, isso pode fazer com que os editores de AEM fiquem sobrecarregados e sem resposta. Quando um parâmetro é definido para ser ignorado para uma página, ela é armazenada em cache na primeira vez que a página é solicitada. As solicitações subsequentes da página são enviadas para a página em cache, independentemente do valor do parâmetro na solicitação.

>[!NOTE]
>
>Mais leituras sobre a importância da configuração `ignoreUrlParams` estão disponíveis no repositório GitHub [aem-dispatcher-Experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams).

Portanto, ela deve ser configurada para ignorar todos os parâmetros por padrão em &quot;ignoreUrlParams&quot;, exceto quando um parâmetro GET é usado, o que alteraria a estrutura HTML de uma página. Um exemplo disso seria com uma página de pesquisa em que o termo de pesquisa está no URL como parâmetro de GET. Nesse caso, você deve configurar manualmente ignoreUrlParams para ignorar parâmetros como gclid, fbclid e quaisquer outros parâmetros de rastreamento que seus canais de publicidade estejam usando, deixando os parâmetros de GET necessários para operações normais do site inalterados.

## Limites de trabalhadores do MPM em despachantes

As configurações de trabalhadores do MPM são uma configuração avançada do servidor HTTP Apache que requer testes completos para otimizar com base na CPU e na RAM disponíveis do Dispatcher. No entanto, no escopo desse whitepaper, sugerimos que ServerLimit e MaxRequestWorkers sejam aumentados para um nível que a CPU e a RAM disponíveis do servidor sejam compatíveis e que, em seguida, MinSpareThreads e MaxSpareThreads sejam aumentados para um nível que corresponda a MaxRequestWorkers.

Essa configuração deixaria o Apache HTTP em uma &quot;configuração de disponibilidade total&quot; que é uma configuração de alto desempenho para servidores com RAM significativa e vários núcleos de CPU. Essa configuração produzirá os melhores tempos de resposta possíveis do Apache HTTP, mantendo conexões abertas persistentes prontas para atender às solicitações, e removerá qualquer atraso na geração de novos processos em resposta a aumentos repentinos de tráfego, como durante as vendas em flash.
