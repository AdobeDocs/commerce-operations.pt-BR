---
title: "O [!UICONTROL Elasticsearch] tab"
description: Saiba mais sobre o [!UICONTROL Elasticsearch] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: b3cc9033eb9445af3edafd8c7ae9809dbb8174fc
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# O [!UICONTROL Elasticsearch] guia

## [!UICONTROL Cluster Status Summary]:

![Resumo do Status do Cluster](../../assets/tools/cluster-status-summary.jpg)

Durante o período de tempo selecionado, a variável **[!UICONTROL Cluster Status Summary]** quadro mostra os status de cor que a variável [!DNL Elasticsearch] O cluster foi aprovado. Neste exemplo, durante o período de tempo selecionado, o cluster estava em status Verde uma vez e em status Amarelo uma vez durante o período de tempo selecionado.

## [!UICONTROL Active Primary Shards]

![Compartilhamentos Primários Ativos](../../assets/tools/active-primary-shards.jpg)

O **[!UICONTROL Active Primary Shards]** quadro mostra os números diferentes dependendo do número de fragmentos primários ativos para a conta selecionada [!DNL Elasticsearch] serviço.

De [!DNL Elasticsearch]: O guia definitivo [2.x]:

&quot;Em [Índices Atualizáveis Dinamicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), explicamos que um compartilhamento é um índice Lucene e que um [!DNL Elasticsearch] index é uma coleção de fragmentos. Seu aplicativo lida com um índice e [!DNL Elasticsearch] encaminha suas solicitações para os fragmentos apropriados. Um fragmento é a unidade de escala. O menor índice que você pode ter é um com um único compartilhamento. Isso pode ser mais do que suficiente para suas necessidades — um único compartilhamento pode conter muitos dados — mas limita sua capacidade de dimensionar.&quot;

Quando um índice é criado, há vários fragmentos criados com esse índice. Por padrão, cinco fragmentos primários são alocados para cada novo índice, o que significa que um índice pode ser distribuído por cinco nós (um fragmento por nó). Também há fragmentos de réplica. Eles são principalmente para failover. Os compartilhamentos de réplica podem servir solicitações de leitura.

## [!UICONTROL Active Shards in Cluster]

![Compartilhamentos Ativos no Cluster](../../assets/tools/active-shards-in-cluster.jpg)

O **[!UICONTROL Active Shards in Cluster]** quadro mostra o número total de compartilhamentos primários e de réplicas em um [!DNL Elasticsearch] cluster.

## [!UICONTROL Index health - this will show the index name and color status]

![Integridade do índice](../../assets/tools/index-health.jpg)

Este quadro mostra o nome do índice e a contagem do status da cor do índice. Ao rolar a tabela para baixo, você verá o mesmo nome de índice com status de cor Amarelo e Vermelho. O número após o nome do índice 27 é a contagem da cor do status. Se for zero, não houve instâncias do índice sendo exibido nesse status de cor durante os intervalos de tempo selecionados.

## [!UICONTROL Elasticsearch Status by node information]

![Status do Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

O **[!UICONTROL Elasticsearch Status by node information]** quadro mostra o [!DNL Elasticsearch] status do cluster por cor e por nó. Isso ajuda a indicar qual nó na variável [!DNL Elasticsearch] O cluster está retornando qual status durante o período selecionado.

## [!UICONTROL Elasticsearch index information]

![Informações do índice Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

O **[!UICONTROL Elasticsearch index information]** a tabela mostra o nome do índice, em que nó ele está, o número de documentos indexados, a integridade do índice e o tamanho do índice em MB em um horário específico.

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch processar CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

O **[!UICONTROL Elasticsearch process CPU %]** quadro mostra o percentual da CPU do processo de acordo com a variável [!DNL Elasticsearch] processar durante o período selecionado.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch Memory Garbage](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] O é um processo Java. Se estiver com pouca memória alocada, a coleta de lixo será iniciada para liberar memória. Se a coleta de lixo for frequente, isso indica que pode haver muitos índices ou fragmentos para a memória alocada. Pode haver oportunidade de limpar os índices e fragmentos ou [!DNL Elasticsearch] pode precisar de mais memória.

## [!UICONTROL Elasticsearch Index information]

![Informações do Índice de Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

À medida que os índices são criados e atualizados, a integridade do índice pode mudar.

## [!UICONTROL Elasticsearch Index Size]

![Tamanho do índice de Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

O **[!UICONTROL Elasticsearch Index Size]** frame indica o nome e o tamanho do índice no período selecionado. Isso pode indicar problemas na indexação de um site.

## [!UICONTROL Elasticsearch Errors]

![Erros de Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

O **[!UICONTROL Elasticsearch Errors]** quadro exibe erros com [!DNL Elasticsearch] como ficar sem espaço, alternar do status Amarelo para Vermelho, quando todos os fragmentos falharem, quando houver problemas de parâmetro com pesquisas, erros de versão e quando todos os nós estiverem indisponíveis.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Sombreamentos não atribuídos ao Elasticsearch](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Os fragmentos não atribuídos farão com que um cluster mova do status Verde para o status Amarelo.
