---
title: A guia [!UICONTROL Elasticsearch]
description: Saiba mais sobre a guia [!UICONTROL Elasticsearch] do  [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# A guia [!UICONTROL Elasticsearch]

## [!UICONTROL Cluster Status Summary]:

![Resumo de Status do Cluster](../../assets/tools/cluster-status-summary.jpg)

Durante o período selecionado, o quadro **[!UICONTROL Cluster Status Summary]** mostra os status de cores pelos quais o cluster [!DNL Elasticsearch] passou. Neste exemplo, durante o período selecionado, o cluster estava no status Verde uma vez e no status Amarelo uma vez durante o período selecionado.

## [!UICONTROL Active Primary Shards]

![Compartilhamentos Primários Ativos](../../assets/tools/active-primary-shards.jpg)

O quadro **[!UICONTROL Active Primary Shards]** mostra os números diferentes, dependendo do número de fragmentos principais ativos para o serviço [!DNL Elasticsearch] da conta selecionada.

De [!DNL Elasticsearch]: o Guia definitivo [2.x]:

&quot;Em [Índices Atualizáveis Dinamicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), explicamos que um fragmento é um índice Lucene e que um índice [!DNL Elasticsearch] é uma coleção de fragmentos. Seu aplicativo se comunica com um índice e o [!DNL Elasticsearch] roteia suas solicitações para os fragmentos apropriados. Um fragmento é a unidade de escala. O menor índice que você pode ter é um com um único fragmento. Isso pode ser mais do que suficiente para suas necessidades — um único fragmento pode conter muitos dados — mas limita sua capacidade de expansão.&quot;

Quando um índice é criado, há vários fragmentos criados com esse índice. Por padrão, cinco fragmentos principais são atribuídos a cada novo índice, o que significa que um índice pode ser distribuído entre cinco nós (um fragmento por nó). Há também fragmentos de réplicas. Elas se destinam principalmente ao failover. Fragmentos de réplica podem atender a solicitações de leitura.

## [!UICONTROL Active Shards in Cluster]

![Compartilhamentos Ativos no Cluster](../../assets/tools/active-shards-in-cluster.jpg)

O quadro **[!UICONTROL Active Shards in Cluster]** mostra o número total de fragmentos primários e de réplica em um cluster [!DNL Elasticsearch].

## [!UICONTROL Index health - this will show the index name and color status]

![Integridade do índice](../../assets/tools/index-health.jpg)

Esse quadro mostra o nome do índice e a contagem de status da cor do índice. Ao rolar para baixo na tabela, você verá o mesmo nome de índice com os status de cores Amarelo e Vermelho. O número que segue o nome de índice 27 é a contagem da cor de status. Se for zero, não havia ocorrências do índice nesse status de cor durante os intervalos selecionados.

## [!UICONTROL Elasticsearch Status by node information]

![Status do Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

O quadro **[!UICONTROL Elasticsearch Status by node information]** mostra o status do cluster [!DNL Elasticsearch] por cor e por nó. Isso ajuda a indicar qual nó no cluster [!DNL Elasticsearch] está retornando qual status durante o período selecionado.

## [!UICONTROL Elasticsearch index information]

![Informações sobre o índice Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

A tabela **[!UICONTROL Elasticsearch index information]** mostra o nome do índice, em que nó ele está, o número de documentos indexados, a integridade do índice e o tamanho do índice em MB em um determinado momento.

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch processa CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

O quadro **[!UICONTROL Elasticsearch process CPU %]** mostra a porcentagem de CPU do processo [!DNL Elasticsearch] durante o período selecionado.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Lixo de memória do Elasticsearch](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] é um processo Java. Se a memória alocada for insuficiente, ele iniciará a coleta de lixo para liberar memória. Se a coleta de lixo for frequente, isso indica que pode haver muitos índices ou fragmentos para a memória alocada. Pode haver uma oportunidade de limpar os índices e fragmentos ou [!DNL Elasticsearch] pode precisar de mais memória.

## [!UICONTROL Elasticsearch Index information]

![Informações sobre o Índice Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

À medida que os índices são criados e atualizados, a integridade do índice pode mudar.

## [!UICONTROL Elasticsearch Index Size]

![Tamanho do Índice Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

O quadro **[!UICONTROL Elasticsearch Index Size]** indica o nome e o tamanho do índice no período selecionado. Isso pode indicar problemas com a forma como um site está indexando.

## [!UICONTROL Elasticsearch Errors]

![Erros do Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

O quadro **[!UICONTROL Elasticsearch Errors]** exibe erros com [!DNL Elasticsearch], como falta de espaço, alternando do status Amarelo para Vermelho, quando todos os fragmentos falham, quando há problemas de parâmetro com pesquisas, erros de versão e quando todos os nós estão indisponíveis.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Compartilhamentos não atribuídos da Elasticsearch](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Fragmentos não atribuídos farão com que um cluster mude do status Verde para o status Amarelo.
