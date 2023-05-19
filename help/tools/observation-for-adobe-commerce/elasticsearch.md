---
title: A variável [!UICONTROL Elasticsearch] guia
description: Saiba mais sobre o [!UICONTROL Elasticsearch] guia de [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# A variável [!UICONTROL Elasticsearch] guia

## [!UICONTROL Cluster Status Summary]:

![Resumo de Status do Cluster](../../assets/tools/cluster-status-summary.jpg)

Durante o período selecionado, a variável **[!UICONTROL Cluster Status Summary]** quadro mostra os status de cor que o [!DNL Elasticsearch] cluster passou. Neste exemplo, durante o período selecionado, o cluster estava no status Verde uma vez e no status Amarelo uma vez durante o período selecionado.

## [!UICONTROL Active Primary Shards]

![Compartilhamentos principais ativos](../../assets/tools/active-primary-shards.jpg)

A variável **[!UICONTROL Active Primary Shards]** quadro mostra os números diferentes, dependendo do número de fragmentos principais ativos para a conta selecionada [!DNL Elasticsearch] serviço.

De [!DNL Elasticsearch]: o guia definitivo [2.x]:

&quot;No [Índices atualizáveis dinamicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), explicamos que um fragmento é um índice de Lucene e que um [!DNL Elasticsearch] index é uma coleção de fragmentos. Seu aplicativo se comunica com um índice e [!DNL Elasticsearch] O encaminha suas solicitações para os fragmentos apropriados. Um fragmento é a unidade de escala. O menor índice que você pode ter é um com um único fragmento. Isso pode ser mais do que suficiente para suas necessidades — um único fragmento pode conter muitos dados — mas limita sua capacidade de expansão.&quot;

Quando um índice é criado, há vários fragmentos criados com esse índice. Por padrão, cinco fragmentos principais são atribuídos a cada novo índice, o que significa que um índice pode ser distribuído entre cinco nós (um fragmento por nó). Há também fragmentos de réplicas. Elas se destinam principalmente ao failover. Fragmentos de réplica podem atender a solicitações de leitura.

## [!UICONTROL Active Shards in Cluster]

![Compartilhamentos ativos no cluster](../../assets/tools/active-shards-in-cluster.jpg)

A variável **[!UICONTROL Active Shards in Cluster]** mostra o número total de fragmentos primários e de réplicas em um [!DNL Elasticsearch] cluster.

## [!UICONTROL Index health - this will show the index name and color status]

![Integridade do índice](../../assets/tools/index-health.jpg)

Esse quadro mostra o nome do índice e a contagem de status da cor do índice. Ao rolar para baixo na tabela, você verá o mesmo nome de índice com os status de cores Amarelo e Vermelho. O número que segue o nome de índice 27 é a contagem da cor de status. Se for zero, não havia ocorrências do índice nesse status de cor durante os intervalos selecionados.

## [!UICONTROL Elasticsearch Status by node information]

![Status do Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

A variável **[!UICONTROL Elasticsearch Status by node information]** o quadro mostra o [!DNL Elasticsearch] status do cluster por cor e por nó. Isso ajuda a indicar qual nó no [!DNL Elasticsearch] o cluster está retornando qual status durante o período selecionado.

## [!UICONTROL Elasticsearch index information]

![informações do índice Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

A variável **[!UICONTROL Elasticsearch index information]** A tabela mostra o nome do índice, em que nó ele está, o número de documentos indexados, a integridade do índice e o tamanho do índice em MB em um determinado momento.

## [!UICONTROL Elasticsearch process CPU %]

![CPU do processo Elasticsearch](../../assets/tools/elasticsearch-process-cpu.jpg)

A variável **[!UICONTROL Elasticsearch process CPU %]** quadro mostra o percentual de CPU do processo pelo [!DNL Elasticsearch] durante o período selecionado.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Lixo de memória do Elasticsearch](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] é um processo Java. Se a memória alocada for insuficiente, ele iniciará a coleta de lixo para liberar memória. Se a coleta de lixo for frequente, isso indica que pode haver muitos índices ou fragmentos para a memória alocada. Pode haver uma oportunidade de limpar os índices e fragmentos ou [!DNL Elasticsearch] pode precisar de mais memória.

## [!UICONTROL Elasticsearch Index information]

![Informações do Índice Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

À medida que os índices são criados e atualizados, a integridade do índice pode mudar.

## [!UICONTROL Elasticsearch Index Size]

![Tamanho do índice de Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

A variável **[!UICONTROL Elasticsearch Index Size]** quadro indica o nome e o tamanho do índice no período selecionado. Isso pode indicar problemas com a forma como um site está indexando.

## [!UICONTROL Elasticsearch Errors]

![Erros de Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

A variável **[!UICONTROL Elasticsearch Errors]** quadro exibe erros com [!DNL Elasticsearch] como ficar sem espaço, alternar do status Amarelo para Vermelho, quando todos os fragmentos falharem, quando houver problemas de parâmetros com pesquisas, erros de versão e quando todos os nós estiverem indisponíveis.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Compartilhamentos não atribuídos do Elasticsearch](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Fragmentos não atribuídos farão com que um cluster mude do status Verde para o status Amarelo.
