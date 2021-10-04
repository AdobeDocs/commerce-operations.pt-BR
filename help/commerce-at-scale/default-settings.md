---
title: Otimização do desempenho do Adobe Commerce
description: Prepare seu projeto do Adobe Commerce para usar o Adobe Experience Manager as a CMS alterando algumas configurações padrão.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Otimização do desempenho do Adobe Commerce

## Localização geográfica da infraestrutura de AEM e Adobe Commerce

Para reduzir a latência entre o editor de AEM e o Adobe Commerce GraphQL ao criar páginas, o provisionamento inicial das duas infraestruturas separadas deve ser hospedado na mesma região AWS (ou Azure). A localização geográfica escolhida para ambas as nuvens também deve estar mais próxima da maioria da base de clientes, para que as solicitações GraphQL do lado do cliente sejam atendidas de um local geograficamente próximo à maioria dos clientes.

## Armazenamento em cache GraphQL no Adobe Commerce

Quando o navegador do usuário ou AEM editor chamar o GraphQL do Adobe Commerce, determinadas chamadas serão armazenadas em cache
em Fastly. Geralmente, os queries armazenados em cache são aqueles que contêm dados não pessoais e provavelmente não mudarão com frequência. Por exemplo: categorias, categoryList e produtos. Aquelas que não são explicitamente armazenadas em cache são aquelas que são alteradas regularmente e quando armazenadas em cache podem representar riscos para dados pessoais e operações do site, por exemplo, consultas como carrinho e customerPaymentTokens.

GraphQL permite fazer várias consultas em uma única chamada. É importante observar que, se você especificar até mesmo uma consulta que o Adobe Commerce não armazena em cache com muitas outras que não podem ser armazenadas em cache, o Adobe Commerce ignorará o cache para todas as consultas na chamada . Isso deve ser considerado pelos desenvolvedores ao combinar várias consultas para garantir que consultas potencialmente armazenáveis em cache não sejam ignoradas involuntariamente‡.

>[!NOTE]
>
> Mais informações sobre consultas armazenáveis em cache e não armazenáveis em cache, consulte a documentação do desenvolvedor do Adobe Commerce [developer documentation](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Tabela plana do catálogo

Não se recomenda a utilização de tabelas fixas para produtos e categorias. O uso desse recurso obsoleto pode resultar em degradação de desempenho e problemas de indexação, portanto, o catálogo simples deve ser desativado por meio do administrador do Adobe Commerce, na seção da loja. Alguns módulos e personalizações de terceiros exigem tabelas simples para funcionar corretamente - é recomendável fazer uma avaliação para entender impactos e riscos associados à necessidade de usar tabelas simples ao escolher utilizar essas extensões ou personalizações.

## Proteção de origem rápida

Por padrão, a blindagem de origem Fastly não está ativada. O objetivo da proteção de origem da Fastly é reduzir o tráfego diretamente para a origem Adobe Commerce: quando uma solicitação é recebida, um local de borda Fastly (ou &quot;ponto de presença&quot; / POP) verifica se há conteúdo em cache e o fornece. Se não estiver em cache, ele continuará para o POP de blindagem para verificar se está em cache lá (se o conteúdo tiver sido solicitado anteriormente mesmo de outro POP global, ele será armazenado em cache). Por fim, se não for armazenado em cache no POP de blindagem, ele só seguirá para o servidor de Origem.

A proteção de origem rápida pode ser ativada nas configurações de back-end do administrador do Adobe Commerce Fastly. Você deve escolher um local de blindagem mais próximo do seu datacenter de origem do Adobe Commerce para obter o melhor desempenho.

## Otimização rápida de imagens

Quando a proteção de origem Fastly estiver ativada, você também poderá ativar o Fastly Image Otimizer. Quando as imagens do catálogo de produtos são armazenadas no Adobe Commerce, esse serviço permite descarregar todo o processamento intensivo de recursos e processamento de transformação de imagens do catálogo de produtos para Fastly e off da origem do Adobe Commerce. Os tempos de resposta do usuário final também são aprimorados para o tempo de carregamento da página, já que as imagens são transformadas no local da borda, o que elimina a latência ao reduzir o número de solicitações de volta à origem do Adobe Commerce.

A otimização de imagem rápida pode ser ativada por &quot;ativar otimização de imagem profunda&quot; na configuração Fastly na administração, embora somente depois que a proteção de origem for ativada. Mais detalhes sobre as configurações para otimização de imagem rápida estão disponíveis no Adobe Commerce [developer documentation](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Captura de tela das configurações de Otimização de imagem Fastly no Administrador do Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Desativar módulos não utilizados

Se o Adobe Commerce estiver em execução sem cabeçalho, o fornecimento de solicitações somente por meio do ponto de extremidade GraphQL e nenhuma página de armazenamento de front-end estiver sendo veiculada diretamente do Adobe Commerce, muitos módulos ficarão redundantes e não serão usados. Ao desabilitar módulos não utilizados, sua base de código do Adobe Commerce torna-se menor, menos complexa e, portanto, pode oferecer melhorias de desempenho. A desativação de módulos no Adobe Commerce pode ser gerenciada usando o composer. Os módulos que podem ser desativados dependem dos requisitos do site e, portanto, nenhuma lista recomendada pode ser fornecida, pois seria específica para a implementação de cada cliente do Adobe Commerce.

## Ativação de conexão MySQL e Redis

Por padrão, as conexões MySQL e Redis Slave não são ativadas no Adobe Commerce na nuvem. Isso ocorre porque essas configurações são adequadas apenas para clientes que esperam carga muito alta. A latência Cross-AZ (zonas de disponibilidade cruzada) é mais alta com as conexões escravas ativadas e, portanto, essa configuração na verdade reduz o desempenho de um Adobe Commerce na instância de nuvem caso a instância esteja recebendo apenas níveis de carga regulares.

Se a instância do Adobe Commerce estiver esperando uma carga extrema, a ativação de principal-subordinado para MySQL e Redis ajudará no desempenho, espalhando a carga no Banco de Dados do MySQL ou Redis em diferentes nós.

Como guia, em ambientes com carga normal, habilitar as Conexões Subordinadas reduzirá o desempenho em 10-15%. Mas em clusters com carga e tráfego intenso, há um aumento de desempenho de cerca de 10-15%. Portanto, é importante carregar para testar seu ambiente com os níveis de tráfego esperados para avaliar se essa configuração seria benéfica para os tempos de desempenho sob carga.

Para habilitar/desabilitar conexões escravas para mysql e redis, você deve editar seu arquivo `.magento.env.yaml` para incluir o seguinte:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Para a arquitetura dimensionada (arquitetura dividida - veja abaixo), as conexões escravas de Redis não devem ser ativadas, pois isso causará a exibição de erros. No caso de uma arquitetura dividida, recomenda-se implementar o armazenamento em cache L2 para Redis.

## Migração para um Adobe Commerce on cloud scale (split)

Se, após todas as configurações acima, os resultados do teste de carga ou a análise do desempenho da infraestrutura ativa ainda indicarem que os níveis de carga para o Adobe Commerce são de um nível que maça consistentemente a CPU e outros recursos do sistema, então uma mudança para uma arquitetura dimensionada (dividida) deve ser considerada.

Com uma arquitetura Pro padrão, há 3 nós, cada um com uma pilha de tecnologia completa. Ao converter em arquitetura de camada dividida, isso muda para um mínimo de 6 nós: 3 dos quais contêm Elasticsearch, MariaDB, Redis e outros serviços principais; os outros 3 para processamento do tráfego da Web contêm phpfpm e NGINX. Há maiores possibilidades de dimensionamento com nível dividido: Os nós principais que contêm bancos de dados podem ser dimensionados verticalmente; os nós da Web podem ser dimensionados horizontalmente e verticalmente, dando uma grande flexibilidade para expandir a infraestrutura sob demanda por um período definido de alta atividade de carga e em nós onde os recursos extras são necessários.

Se tiver sido tomada a decisão de alternar para uma arquitetura de camada dividida devido às grandes expectativas de carga do site, uma discussão deve ser realizada com o Gerente de sucesso do cliente sobre as etapas para habilitar isso.
