---
title: Otimização do desempenho do AEM
description: Otimize sua configuração padrão do Adobe Experience Manager para oferecer suporte a cargas altas no Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# Otimização do desempenho do AEM

O Dispatcher do AEM é um proxy reverso, que ajuda a fornecer um ambiente rápido e dinâmico. Ele funciona como parte de um servidor de HTML estático, como o Apache HTTP Server, com o objetivo de armazenar (ou &quot;armazenar em cache&quot;) o máximo possível do conteúdo do site, na forma de recursos estáticos. Essa abordagem tem como objetivo minimizar a necessidade de acessar a funcionalidade de renderização de página do AEM e o serviço Adobe Commerce GraphQL o máximo possível. O resultado de servir grande parte das páginas como HTML estático, CSS e JS oferece benefícios de desempenho aos usuários e reduz os requisitos de infraestrutura no ambiente. Qualquer página ou consulta que provavelmente será repetida de forma idêntica de usuário para usuário deve ser considerada para armazenamento em cache.

As seções a seguir mostram em alto nível a área de enfoque técnico recomendada a ser revisada para permitir o armazenamento em cache eficaz do AEM em um ambiente da CIF/Adobe Commerce.

## Armazenamento em cache com base em TTL em dispatchers de AEM

O armazenamento em cache do máximo possível do site nos dispatchers é a prática recomendada para qualquer projeto AEM. A invalidação do cache com base no tempo armazenará em cache as páginas da CIF renderizadas do lado do servidor por um período limitado definido. Depois que o tempo definido expirar, a próxima solicitação recriará a página do editor de AEM e do Adobe Commerce GraphQL e a armazenará no cache do dispatcher novamente até a próxima invalidação.

O recurso de armazenamento em cache TTL pode ser configurado no AEM com o uso do componente &quot;TTL do Dispatcher&quot; no pacote ACS AEM Commons e a configuração /enableTTL &quot;1&quot; no arquivo de configuração dispatcher.any.

Se ativado, o Dispatcher avaliará os cabeçalhos de resposta do back-end e, se eles tiverem um max-age de Cache-Control ou uma data de expiração, um arquivo auxiliar e vazio ao lado do arquivo de cache será criado, com o tempo de modificação igual à data de expiração. Quando o arquivo em cache é solicitado depois do tempo de modificação, ele é automaticamente solicitado novamente no back-end. Isso proporciona um mecanismo de armazenamento em cache eficiente, que não requer intervenção ou manutenção manual, uma vez que o atraso na atualização do produto (TTL) tenha sido reconhecido e aceito pelas partes interessadas da empresa.

## Armazenamento em cache do navegador

A abordagem de TTL do dispatcher acima reduzirá bastante as solicitações e o carregamento no editor. No entanto, há alguns ativos que provavelmente não serão alterados e, portanto, até mesmo as solicitações ao dispatcher podem ser reduzidas armazenando arquivos relevantes em cache localmente no navegador de um usuário. Por exemplo, o logotipo do site, que é exibido em todas as páginas do site no modelo de site, não precisaria ser solicitado todas as vezes para o Dispatcher. Em vez disso, ele pode ser armazenado no cache do navegador do usuário. A redução nos requisitos de largura de banda para cada carregamento de página teria um grande impacto na capacidade de resposta do site e nos tempos de carregamento de página.

O armazenamento em cache no nível do navegador geralmente é feito por meio do cabeçalho de resposta &quot;Cache-Control: max-age=&quot;. A configuração maxage informa ao navegador por quantos segundos o arquivo deve ser armazenado em cache antes de tentar &quot;revalidar&quot; ou solicitá-lo do site novamente. Esse conceito de max-age do cache é comumente chamado de &quot;Expiração do cache&quot; ou TTL (&quot;Tempo de vida&quot;). Fornecer experiências de comércio em escala - Com o Adobe Experience Manager, a Commerce Integration Framework, o Adobe Commerce 7

Algumas áreas de um site AEM/CIF/Adobe Commerce que podem ser definidas para armazenamento em cache no navegador do cliente incluem:

- Imagens (dentro do próprio modelo AEM, por exemplo, logotipo do site e imagens de design de modelo — imagens de produtos de catálogo seriam chamadas do Adobe Commerce pelo Fastly, o armazenamento dessas imagens em cache será discutido posteriormente)
- arquivos HTML (para páginas alteradas com pouca frequência - página de termos e condições etc.)
- Arquivos CSS
- Todos os arquivos JavaScript do site - incluindo arquivos JavaScript CIF

## Otimização do statfilelevel e do período de carência do Dispatcher

A configuração padrão do dispatcher usa a configuração /statfilelevel &quot;0&quot; - isso significa que um único arquivo &quot;.stat&quot; é colocado na raiz do diretório htdocs (diretório raiz do documento). Se uma alteração for feita em uma página ou arquivo no AEM, a hora de modificação desse único arquivo stat será atualizada para a hora da alteração. Se o tempo for mais recente que o tempo de modificação do recurso, o Dispatcher considerará que todos os recursos foram invalidados e qualquer solicitação subsequente para um recurso invalidado acionará uma chamada para a instância de publicação. Basicamente, com essa configuração, cada ativação invalidará todo o cache.

Para qualquer site, especialmente sites comerciais com carga pesada, isso colocaria uma quantidade desnecessária de carga no nível de publicação do AEM para que toda a estrutura do site fosse invalidada com apenas uma atualização de página.

Em vez disso, a configuração statfilelevel pode ser modificada para um valor maior, correspondente à profundidade dos subdiretórios no diretório htdocs do diretório raiz do documento para que, quando um arquivo localizado em um determinado nível for invalidado, somente os arquivos nesse nível de diretório .stat e abaixo dele sejam atualizados.

Por exemplo: digamos que você tenha um modelo de página de produto em:

```
content/ecommerce/us/en/products/product-page.html
```

Cada nível de pasta teria um &quot;nível stat&quot;, conforme mostrado detalhado na tabela acima.

| conteúdo (docroot) | comércio eletrônico | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

Nesse caso, se você tiver deixado a propriedade statfilelevel definida como &quot;0&quot; padrão e o modelo product-page.html for atualizado e ativado acionando uma invalidação, cada arquivo .stat, desde o docroot até o nível 4, será tocado, e os arquivos serão invalidados, causando uma solicitação adicional das instâncias de publicação do AEM para todas as páginas do site (incluindo outros sites, países e idiomas) a partir dessa única alteração.

No entanto, se a propriedade statfilelevel estiver definida como nível 4 e uma alteração for feita no product-page.html, somente o arquivo .stat no diretório products desse site/país/idioma específico será tocado.

Observe que o nível do arquivo .stat não deve ser definido como um nível muito alto - exceder 20 pode ter impacto no desempenho. A execução de uma ativação de arquivo em massa ao executar um teste de desempenho deve fornecer o nível correto para o qual você deve ajustar o nível de estado.

Outra configuração do dispatcher a ser otimizada ao configurar o statfilelevel é a configuração gracePeriod. Isso define o número de segundos em que um recurso obsoleto e invalidado automaticamente ainda pode ser enviado do cache após a última ativação. Os recursos invalidados automaticamente são invalidados por qualquer ativação (quando o caminho de cada um deles corresponde à seção /invalidate do Dispatcher e ao nível especificado na propriedade statfileslevel). Definir a configuração gracePeriod como 2 segundos pode ser usada para impedir um cenário em que várias solicitações são enviadas continuamente para o editor, mesmo enquanto o editor ainda está no processo de criação da nova página.

>[!NOTE]
>
> Uma leitura mais detalhada sobre este tópico está disponível na [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) Repositório GitHub.

## CIF - armazenamento em cache do GraphQL por meio de componentes

Componentes individuais no AEM podem ser definidos para serem armazenados em cache, o que significa que a solicitação do GraphQL para o Adobe Commerce AEM é chamada uma vez e, em seguida, as solicitações subsequentes, até o limite de tempo configurado, são recuperadas do cache do e não colocam mais carga no Adobe Commerce. Os exemplos seriam uma navegação do site com base em uma árvore de categoria mostrada em cada página e opções em uma funcionalidade de pesquisa facetada: essas são apenas duas áreas que exigem consultas com muitos recursos no Adobe Commerce para serem criadas, mas seria improvável alterar regularmente e, portanto, seriam boas opções de armazenamento em cache. Dessa forma, por exemplo, mesmo quando um PDP ou PLP está sendo recriado pelo editor, a solicitação intensiva de recursos do GraphQL para o build de navegação não atingiria o Adobe Commerce e poderia ser recuperada do cache do GraphQL no CIF do AEM.

Um exemplo abaixo serve para que o componente de navegação seja armazenado em cache, pois envia a mesma consulta do GraphQL em todas as páginas do site. A solicitação abaixo armazena em cache as últimas 100 entradas por 10 minutos para a estrutura de navegação:

```
venia/components/structure/navigation:true:100:600
```

O exemplo abaixo armazena em cache as últimas 100 opções de pesquisa facetada em uma página de pesquisa por 1 hora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

A solicitação, incluindo todos os cabeçalhos http personalizados e variáveis, deve corresponder exatamente para que o cache seja uma &quot;ocorrência&quot; e para evitar uma chamada repetida para o Adobe Commerce. Deve ser observado que, uma vez definido, não há uma maneira fácil de invalidar manualmente esse cache. Isso pode significar que, se uma nova categoria for adicionada no Adobe Commerce, ela não começará a aparecer na navegação até que o tempo de expiração definido no cache acima tenha expirado e a solicitação do GraphQL seja atualizada. O mesmo para os aspectos de pesquisa. No entanto, dados os benefícios de desempenho que esse armazenamento em cache deve obter, esse compromisso geralmente é aceitável.

As opções de armazenamento em cache acima podem ser definidas usando o console de configuração do OSGi do AEM em &quot;GraphQL Client Configuration Fatory&quot;. Cada entrada de configuração de cache pode ser especificada com o seguinte formato:

```
* NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Armazenamento em cache híbrido — solicitações do GraphQL do lado do cliente em páginas do Dispatcher armazenadas em cache

Também é possível uma abordagem híbrida para o armazenamento em cache de páginas: é possível que uma página da CIF contenha componentes que sempre solicitariam as informações mais recentes da Adobe Commerce diretamente do navegador do cliente. Isso pode ser útil para áreas específicas da página em um modelo, que são importantes para serem mantidas atualizadas com informações em tempo real: por exemplo, os preços dos produtos em um PDP. Quando os preços estão mudando com frequência devido à correspondência dinâmica de preços, essas informações podem ser configuradas para não serem armazenadas em cache no dispatcher, em vez disso, os preços podem ser obtidos no lado do cliente no navegador do cliente diretamente do Adobe Commerce por meio de APIs do GraphQL com componentes da Web CIF do AEM.

Isso pode ser configurado por meio das configurações de componentes do AEM. Para obter informações sobre preços nas páginas de listas de produtos, isso pode ser configurado no modelo de lista de produtos, selecionando o componente de lista de produtos nas configurações da página e marcando a opção &quot;carregar preços&quot;. A mesma abordagem funcionaria para os níveis de estoque.

Os métodos acima só devem ser utilizados nos casos em que seja exigida informação em tempo real e constantemente atualizada. No exemplo acima, com relação a preços, poderia ser acordado com as partes interessadas da empresa atualizar os preços somente diariamente em horários de tráfego baixo e, em seguida, executar a operação de liberação de cache. Isso eliminaria a necessidade de solicitações de informações de preços em tempo real e a carga extra subsequente na Adobe Commerce ao criar cada página que exibe informações de preços.

## Solicitações GraphQL não armazenáveis em cache

Componentes de dados dinâmicos específicos nas páginas não devem ser armazenados em cache e sempre exigirão uma chamada do GraphQL para o Adobe Commerce, como para o carrinho de compras e chamadas em todas as páginas de check-out. Essas informações são específicas de um usuário e mudam constantemente devido à atividade do cliente no site, por exemplo, adicionando produtos ao carrinho de compras.

Os resultados da consulta do GraphQL não devem ser armazenados em cache para clientes conectados se o design do site fornecer respostas diferentes com base na função do usuário. Por exemplo, você pode criar vários grupos de clientes e configurar preços de produtos diferentes ou visibilidade de categoria de produto diferente para cada grupo. O armazenamento desses resultados em cache pode fazer com que os clientes vejam os preços de outro grupo de clientes ou tenham categorias incorretas sendo exibidas.

## Ignorando parâmetros de rastreamento no cache do Dispatcher do AEM

Sites de comércio eletrônico podem direcionar tráfego para seu site usando anúncios de pesquisa PPC ou campanhas de mídia social.

O uso desses meios significará que uma ID de rastreamento será adicionada ao link de saída dessa plataforma. Por exemplo, o Facebook adicionará uma ID de clique do Facebook (fbclid) ao URL, o Google Adverts adicionará uma ID de clique do Google AEM (gclid). Isso fará com que os links recebidos para o seu front-end do apareçam conforme mostrado abaixo, por exemplo:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

O gclid e o fbclid serão alterados a cada usuário que clicar no anúncio, isso é destinado a fins de rastreamento, mas com suas configurações padrão, o AEM veria cada solicitação como uma página exclusiva, o que ignoraria o dispatcher e geraria carga extra desnecessária no editor e no Adobe Commerce.

Durante um evento de sobretensão, isso pode fazer com que os editores de AEM fiquem sobrecarregados e sem resposta. Quando um parâmetro é definido para ser ignorado para uma página, a página é armazenada em cache na primeira vez que a página é solicitada. As solicitações subsequentes da página são enviadas para a página em cache, independentemente do valor do parâmetro na solicitação.

>[!NOTE]
>
>Uma leitura mais aprofundada sobre a importância `ignoreUrlParams` está disponível no [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) Repositório GitHub.

Portanto, ela deve ser configurada para ignorar todos os parâmetros por padrão em &quot;ignoreUrlParams&quot;, exceto quando um parâmetro GET é usado, o que alteraria a estrutura HTML de uma página. Um exemplo disso seria com uma página de pesquisa em que o termo de pesquisa está no URL como parâmetro GET; nesse caso, você deve configurar manualmente ignoreUrlParams para ignorar parâmetros como gclid, fbclid e quaisquer outros parâmetros de rastreamento que seus canais de publicidade estejam usando, deixando os parâmetros GET necessários para operações normais do site não afetados.

## Limites de trabalhadores MPM em despachantes

As configurações dos trabalhadores do MPM são uma configuração avançada do servidor HTTP Apache que exigiria testes completos para otimizar com base na CPU e na RAM disponíveis no Dispatcher. No entanto, no escopo deste informe oficial, sugerimos que o ServerLimit e o MaxRequestWorkers sejam aumentados para um nível que a CPU e a RAM disponíveis do servidor suportariam, e então o MinSpareThreads e o MaxSpareThreads sejam aumentados para um nível que corresponda ao MaxRequestWorkers.

Essa configuração deixaria o Apache HTTP em uma &quot;configuração de prontidão total&quot;, que é uma configuração de alto desempenho para servidores com RAM significativa e vários núcleos de CPU. Essa configuração produzirá os melhores tempos de resposta possíveis do Apache HTTP ao manter conexões abertas persistentes prontas para atender às solicitações e removerá qualquer atraso na geração de novos processos em resposta a picos de tráfego repentinos, como durante vendas flash.
