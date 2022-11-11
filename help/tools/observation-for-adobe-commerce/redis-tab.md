---
title: "O [!UICONTROL Redis] tab"
description: Saiba mais sobre o [!UICONTROL Redis] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: f4379d0b89a6ea6d2f2a5a02c505581d4d54708f
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# O [!DNL Redis] guia

## [!UICONTROL Redis Node summary]

![Resumo do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

O **[!UICONTROL Redis Node summary]** é inclusiva de todos os nós em um ambiente. O exemplo acima inclui os nós para armazenamento temporário compartilhado. Há um principal e dois secundários na produção e também um principal e dois secundários na preparação.

## [!UICONTROL Redis node detail]

![Detalhes do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

O **[!UICONTROL Redis node detail]** quadro indica o ambiente, [!DNL Redis] função, versão de software e tamanho do nó.

## [!UICONTROL Redis node roles timeline]

![Linha do tempo de funções do nó de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

O **[!UICONTROL Redis node roles timeline]** quadro indica a perda de [!DNL Redis] , em especial funções. Se uma linha diminuir, isso indica que a função específica que a linha representa perdeu um nó ou nós.

## [!UICONTROL Connection to Redis]

![Conexão com Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

O **[!UICONTROL Connection to Redis]** quadro exibe o valor net.connectedClients do [!DNL New Relic Redis] dados de amostra. Ele exibe a contagem de conexões por [!DNL New Relic] aplicativo (ambiente) e nó .

## [!UICONTROL Commands per second by node]

![Comandos por segundo por nó](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

O **[!UICONTROL Commands per second by node]** quadro mostra o [!DNL Redis] comandos por nó por segundo no período selecionado.

## [!UICONTROL Redis % of memory used]

![Redis % da memória utilizada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

O **[!UICONTROL Redis % of memory used]** quadro mostra a porcentagem de memória máxima usada pelo [!DNL Redis] servidores.

## [!UICONTROL Redis used memory]

![Redis memória usada](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

O **[!UICONTROL Redis used memory]** quadro mostra o uso de memória por nó em GB/MB.

## [!UICONTROL Redis changes since last db save]

![Redis alterações desde o último salvamento do db](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] é um residente de memória e salva as informações no armazenamento. O **[!UICONTROL Redis changes since last db save]** frame indica o número de alterações na memória que ocorreram desde que o último banco de dados foi salvo no armazenamento. Consulte [Persistência de Redis](https://redis.io/docs/manual/persistence/) para obter mais explicações sobre [!DNL Redis's] persistência.

## [!UICONTROL Redis synchronization from Log]

![Redis sincronização do Log](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

O **[!UICONTROL Redis synchronization from Log]** O quadro foca nos erros encontrados durante [!DNL Redis] sincronização ou erros que ocorrem devido a problemas de sincronização. Para obter mais informações sobre [!DNL Redis], consulte [[!DNL Redis] Documentação](https://redis.io/docs/).
