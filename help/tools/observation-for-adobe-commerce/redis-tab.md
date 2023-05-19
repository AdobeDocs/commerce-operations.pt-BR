---
title: A variável [!UICONTROL Redis] guia
description: Saiba mais sobre o [!UICONTROL Redis] guia de [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# A variável [!DNL Redis] guia

## [!UICONTROL Redis Node summary]

![Resumo do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

A variável **[!UICONTROL Redis Node summary]** O inclui todos os nós em um ambiente. O exemplo acima inclui os nós para preparo compartilhado. Há um primário e dois secundários na produção e também um primário e dois secundários no preparo.

## [!UICONTROL Redis node detail]

![Detalhes do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

A variável **[!UICONTROL Redis node detail]** quadro indica o ambiente, [!DNL Redis] função, versão do software e tamanho do nó.

## [!UICONTROL Redis node roles timeline]

![Linha do tempo de funções do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

A variável **[!UICONTROL Redis node roles timeline]** quadro indica a perda de [!DNL Redis] serviço em funções específicas. Se uma linha cair, isso indica que a função específica que a linha representa perdeu um ou mais nós.

## [!UICONTROL Connection to Redis]

![Conexão com o Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

A variável **[!UICONTROL Connection to Redis]** quadro exibe o valor net.connectedClients do [!DNL New Relic Redis] dados de exemplo. Ele exibe a contagem de conexões por [!DNL New Relic] aplicativo (ambiente) e nó.

## [!UICONTROL Commands per second by node]

![Comandos por segundo por nó](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

A variável **[!UICONTROL Commands per second by node]** o quadro mostra o [!DNL Redis] por nó por segundo durante o período selecionado.

## [!UICONTROL Redis % of memory used]

![Redis % de memória usada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

A variável **[!UICONTROL Redis % of memory used]** quadro mostra a porcentagem de memória máxima usada pelo [!DNL Redis] servidores.

## [!UICONTROL Redis used memory]

![Memória usada Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

A variável **[!UICONTROL Redis used memory]** O quadro mostra o uso de memória do nó em GB/MB.

## [!UICONTROL Redis changes since last db save]

![Resgata as alterações desde o último salvamento do banco de dados](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] O reside na memória e salva as informações no armazenamento. A variável **[!UICONTROL Redis changes since last db save]** quadro indica o número de alterações na memória ocorridas desde que o último banco de dados foi salvo no armazenamento. Consulte [Persistência de Redis](https://redis.io/docs/manual/persistence/) para obter mais explicações sobre [!DNL Redis's] persistência.

## [!UICONTROL Redis synchronization from Log]

![Redefinir sincronização do Log](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

A variável **[!UICONTROL Redis synchronization from Log]** o quadro focaliza os erros encontrados durante [!DNL Redis] sincronização ou erros que ocorrem devido a problemas de sincronização. Para obter mais informações sobre [!DNL Redis], consulte [[!DNL Redis] Documentação](https://redis.io/docs/).
