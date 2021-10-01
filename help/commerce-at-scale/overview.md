---
title: Fornecer Experiências Em Escala
description: Saiba como fornecer experiências em escala com o Adobe Commerce e o Adobe Experience Manager.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Fornecer experiências em escala com o Adobe Commerce, Commerce Integration Framework e Adobe Experience Manager

Um padrão de integração recomendado entre o AEM e o Adobe Commerce usando a CIF como conector é o AEM de ser o proprietário da camada de apresentação (o &quot;vidro&quot;) e o Adobe Commerce para potencializar o backend comercial como um back-end &quot;sem periféricos&quot;. Essa abordagem de integração aproveita os pontos fortes de cada aplicativo: os recursos de criação, personalização e omnicanal de operações de AEM e comércio eletrônico do Adobe-Commerce.

Em um ambiente de comércio AEM/CIF/Adobe, os visitantes do site de comércio eletrônico chegarão inicialmente ao AEM. AEM verificará se a página solicitada está disponível em seu cache do dispatcher. Se a página existir, essa página em cache será veiculada ao visitante, e nenhum processamento adicional será necessário. Se o dispatcher não contiver a página solicitada ou tiver expirado, o dispatcher solicitará que o editor de AEM crie a página, com o editor chamando o Adobe Commerce para dados de comércio eletrônico para criar a página, se necessário. A página criada é então passada para o dispatcher para servir ao visitante e, em seguida, é armazenada em cache, evitando a necessidade de mais carga ser colocada nos servidores em solicitações subsequentes para a mesma página de outros visitantes.

![Diagrama geral da arquitetura do Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/overview.png)

Uma combinação de renderização do lado do servidor e renderização do lado do cliente pode ser usada no modelo de comércio AEM/CIF/Adobe: Renderização do lado do servidor para fornecer conteúdo estático e renderização do lado do cliente para fornecer conteúdo dinâmico pessoal ou em constante mudança, chamando diretamente o Adobe Commerce para componentes específicos
no navegador do usuário.

Um exemplo dos diferentes componentes em uma Página de detalhes do produto em um exemplo AEM loja de comércio eletrônico pode ser visto no exemplo abaixo:

![Diagrama geral da arquitetura do Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Renderização do lado do servidor

É improvável que as páginas de comércio eletrônico, como as PDPs (product detail pages) e as PLPs (Product listing pages) sejam alteradas com frequência e são adequadas para serem totalmente armazenadas em cache após serem renderizadas no lado do servidor, usando AEM Componentes principais da CIF. As páginas devem ser renderizadas no editor de AEM usando modelos genéricos criados no AEM. Esses componentes obtêm dados do Adobe Commerce por meio de APIs GraphQL. Essas páginas são criadas dinamicamente, renderizadas no servidor, armazenadas em cache no AEM dispatcher e, em seguida, entregues no navegador. Exemplos disso são mostrados nas caixas roxas do exemplo acima.

## Renderização do lado do cliente

Quando atributos mais dinâmicos, como níveis de estoque/disponibilidade ou preço, são exibidos, por exemplo, nas Páginas de detalhes do produto (PDPs), os componentes do lado do cliente podem ser usados. Embora a página de modelo possa ser criada e armazenada em cache no dispatcher usando a abordagem de renderização do lado do servidor acima, dentro da própria página estática pode haver componentes da Web dinâmicos do lado do cliente. Esses componentes dinâmicos podem buscar dados diretamente no navegador do cliente do Adobe Commerce por meio de APIs GraphQL para verificar, por exemplo, o preço atual ou o nível de estoque em tempo real na PDP. Isso garante que o conteúdo, normalmente crítico para ser exibido em tempo real, sempre seja buscado no carregamento da página. Exemplos disso são mostrados nas caixas vermelhas no exemplo acima.

Uma combinação de modelos de AEM e renderização no lado do cliente também pode ser usada durante o processo de finalização: os componentes do carrinho do lado do cliente renderizam o carrinho de compras, o formulário de check-out e a integração com o provedor de serviços de pagamento. Essa abordagem híbrida também pode ser usada para a funcionalidade de gerenciamento de conta do Adobe Commerce, como criar conta, entrar em conta e senha esquecida.
