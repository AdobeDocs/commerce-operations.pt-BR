---
title: Otimização de desempenho do Adobe Commerce
description: Prepare seu projeto do Adobe Commerce para usar o Adobe Experience Manager as a CMS alterando algumas configurações padrão.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Otimização do desempenho do Adobe Commerce

## Localização geográfica da infraestrutura do AEM e do Adobe Commerce

Para reduzir a latência entre o editor do AEM e o Adobe Commerce GraphQL ao criar páginas, o provisionamento inicial das duas infraestruturas separadas deve ser hospedado na mesma região do AWS (ou Azure). A localização geográfica escolhida para ambas as nuvens também deve ser a mais próxima da maioria de sua base de clientes, para que as solicitações do GraphQL do lado do cliente sejam atendidas a partir de um local geograficamente próximo da maioria dos clientes.

## Armazenamento em cache do GraphQL no Adobe Commerce

Quando o navegador do usuário ou o editor de AEM chama o GraphQL da Adobe Commerce, determinadas chamadas são armazenadas em cache no Fastly. As consultas armazenadas em cache geralmente são aquelas que contêm dados não pessoais e têm pouca probabilidade de serem alteradas com frequência. Por exemplo: categories, categoryList e products. Aqueles que não são explicitamente armazenados em cache são aqueles que mudam regularmente e, se armazenados em cache, podem representar riscos para dados pessoais e operações do site, por exemplo, consultas como cart e customerPaymentTokens.

O GraphQL permite fazer várias consultas em uma única chamada. É importante observar que, se você especificar até mesmo uma consulta que o Adobe Commerce não armazena em cache com muitas outras que não podem ser armazenadas em cache, o Adobe Commerce ignorará o cache para todas as consultas na chamada. Isso deve ser considerado pelos desenvolvedores ao combinarem várias consultas para garantir que as consultas potencialmente armazenáveis em cache não sejam ignoradas involuntariamente‡.

>[!NOTE]
>
> Mais informações sobre consultas que podem ou não ser armazenadas em cache, consulte o Adobe Commerce [documentação do desenvolvedor](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Tabela plana do catálogo

Não se recomenda a utilização de mesas planas para produtos e categorias. O uso desse recurso obsoleto pode resultar em degradação de desempenho e problemas de indexação. Portanto, o catálogo simples deve ser desativado por meio do administrador do Adobe Commerce, na seção de vitrine eletrônica. Alguns módulos e personalizações de terceiros exigem tabelas planas para funcionar corretamente. Recomenda-se fazer uma avaliação para entender os impactos e riscos associados à necessidade de usar tabelas planas ao optar por utilizar essas extensões ou personalizações.

## Blindagem de origem Fastly

Por padrão, a blindagem de origem do Fastly não é ativada. O objetivo da blindagem de origem do Fastly é reduzir o tráfego diretamente para a origem do Adobe Commerce: quando uma solicitação é recebida, um local de borda do Fastly (ou &quot;ponto de presença&quot; / POP) verifica o conteúdo em cache e o fornece. Se não for armazenado em cache, ele continuará para o POP de escudo para verificar se está armazenado em cache lá (se o conteúdo tiver sido solicitado anteriormente, mesmo de outro POP global, ele será armazenado em cache). Por fim, se não for armazenado em cache no POP de escudo, ele só continuará para o servidor de origem.

A blindagem de origem do Fastly pode ser ativada nas configurações do back-end de configuração do Fastly no administrador do Adobe Commerce. Você deve escolher um local de blindagem mais próximo ao datacenter de origem da Adobe Commerce para obter o melhor desempenho.

## Otimização rápida de imagens

Quando a blindagem de origem do Fastly estiver ativada, você também poderá ativar o Fastly Image Otimizer. Quando as imagens do catálogo de produtos são armazenadas no Adobe Commerce, esse serviço oferece a capacidade de transferir todo o processamento de transformação de imagens do catálogo de produtos que consome muitos recursos para o Fastly e para o OFF da origem do Adobe Commerce. Os tempos de resposta do usuário final também são aprimorados para tempos de carregamento de página, já que as imagens são transformadas no local da borda, o que elimina a latência ao reduzir o número de solicitações de volta à origem do Adobe Commerce.

A otimização de imagem do Fastly pode ser ativada por &quot;ativar a otimização de imagem profunda&quot; na configuração do Fastly no admin, embora somente após a ativação do origin shield. Mais detalhes sobre as configurações para a otimização do Fastly Image estão disponíveis no Adobe Commerce [documentação do desenvolvedor](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Captura de tela das configurações de otimização de imagem do Fastly no Administrador do Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Desativar módulos não utilizados

Se o Adobe Commerce for executado sem periféricos, as solicitações serão atendidas somente pelo endpoint do GraphQL e nenhuma página de armazenamento de front-end será atendida diretamente pelo Adobe Commerce. Em seguida, muitos módulos serão redundantes e não serão usados. Ao desativar módulos não utilizados, sua base de código Adobe Commerce se torna menor, menos complexa e, portanto, pode oferecer melhorias de desempenho. A desativação de módulos no Adobe Commerce pode ser gerenciada usando o composer. Quais módulos podem ser desabilitados dependem dos requisitos do site, portanto, nenhuma lista recomendada pode ser fornecida, pois seria específica para a implementação do Adobe Commerce de cada cliente.

## Ativação de conexão MySQL e Redis

Por padrão, as conexões MySQL e Redis Slave não são ativadas no Adobe Commerce na nuvem. Isso ocorre porque essas configurações só são adequadas para clientes que estão esperando uma carga muito alta. A latência entre AZ (zonas de disponibilidade cruzada) é mais alta com conexões escravas ativadas e, portanto, essa configuração reduz o desempenho de uma instância do Adobe Commerce na nuvem caso a instância esteja recebendo apenas níveis de carga regulares.

Se a instância do Adobe Commerce estiver esperando carga extrema, a ativação do master-slave para MySQL e Redis ajudará no desempenho, distribuindo a carga no banco de dados MySQL ou Redis em diferentes nós.

Como guia, em ambientes com carga normal, ativar Conexões Escravas reduzirá o desempenho em 10-15%. Mas em clusters com carga e tráfego pesados, há um aumento de desempenho de cerca de 10 a 15%. Portanto, é importante testar a carga do seu ambiente com os níveis de tráfego esperados para avaliar se essa configuração seria benéfica para os tempos de desempenho sob carga.

Para ativar/desativar conexões subordinadas para mysql e redis, edite as `.magento.env.yaml` para incluir o seguinte:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Para arquitetura escalonada (arquitetura dividida - veja abaixo), as conexões slave do Redis não devem ser ativadas, pois isso causará a exibição de erros. No caso de uma arquitetura dividida, é recomendável implementar o cache L2 para Redis.

## Migrar para uma Adobe Commerce em arquitetura em escala de nuvem (dividida)

Se, depois de todas as configurações acima, os resultados dos testes de carga ou a análise do desempenho da infraestrutura ativa ainda indicar que os níveis de carga para o Adobe Commerce são de um nível que maximiza consistentemente a CPU e outros recursos do sistema, então uma mudança para uma arquitetura escalonada (dividida) deve ser considerada.

Com uma arquitetura Pro padrão, existem 3 nós, cada um contendo uma pilha de tecnologia completa. Ao converter para arquitetura de camada dividida, isso muda para um mínimo de 6 nós: 3 dos quais contêm Elasticsearch, MariaDB, Redis e outros serviços principais; os outros 3 para processamento de tráfego da web contêm phpfpm e NGINX. Há maiores possibilidades de dimensionamento com a camada dividida: os nós principais que contêm bancos de dados podem ser dimensionados verticalmente; os nós da Web podem ser dimensionados horizontal e verticalmente, oferecendo uma grande quantidade de flexibilidade para expandir a infraestrutura sob demanda para um período definido de atividade de alta carga e em nós onde os recursos extras são necessários.

Se for tomada a decisão de mudar para uma arquitetura de nível dividido devido a grandes expectativas de carga para o seu site, uma discussão deverá ser realizada com a Equipe de conta do Adobe sobre as etapas para habilitar isso.
