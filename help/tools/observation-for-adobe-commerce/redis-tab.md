---
title: A guia [!UICONTROL Redis]
description: Saiba mais sobre a guia [!UICONTROL Redis] do [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%
---
# A guia [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Resumo do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

O **[!UICONTROL Redis Node summary]** inclui todos os nós em um ambiente. O exemplo acima inclui os nós para preparo compartilhado. Há um primário e dois secundários na produção e também um primário e dois secundários no preparo.

## [!UICONTROL Redis node detail]

![Redefine as métricas de desempenho do servidor e os detalhes de configuração do nó](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

O quadro **[!UICONTROL Redis node detail]** indica o ambiente, a função [!DNL Redis], a versão do software e o tamanho do nó.

## [!UICONTROL Redis node roles timeline]

![Linha do tempo de funções do nó Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

O quadro **[!UICONTROL Redis node roles timeline]** indica a perda do serviço [!DNL Redis] em funções específicas. Se uma linha cair, isso indica que a função específica que a linha representa perdeu um ou mais nós.

## [!UICONTROL Connection to Redis]

![Conexão com Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

O quadro **[!UICONTROL Connection to Redis]** exibe o valor net.connectedClients dos dados de amostra [!DNL New Relic Redis]. Ele exibe a contagem de conexões por [!DNL New Relic] aplicativo (ambiente) e nó.

## [!UICONTROL Commands per second by node]

![Comandos por segundo pelo nó](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

O quadro **[!UICONTROL Commands per second by node]** mostra os comandos [!DNL Redis] por nó por segundo durante o período selecionado.

## [!UICONTROL Redis % of memory used]

![Redis % de memória usada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

O quadro **[!UICONTROL Redis % of memory used]** mostra a porcentagem de memória máxima usada pelos servidores [!DNL Redis].

## [!UICONTROL Redis used memory]

![Redis usou memória](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

O quadro **[!UICONTROL Redis used memory]** mostra o uso de memória do nó em GB/MB.

## [!UICONTROL Redis changes since last db save]

![Redis altera desde o último salvamento do banco de dados](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] reside na memória e salva as informações no armazenamento. O quadro **[!UICONTROL Redis changes since last db save]** indica o número de alterações na memória ocorridas desde que o último banco de dados foi salvo no armazenamento. Consulte [Persistência de Redis](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) para obter mais explicações sobre a persistência [!DNL Redis's].

## [!UICONTROL Redis synchronization from Log]

![Sincronização Redis do Log](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

O quadro **[!UICONTROL Redis synchronization from Log]** focaliza os erros encontrados durante a sincronização de [!DNL Redis] ou erros que ocorrem devido a problemas de sincronização. Para obter mais informações sobre [!DNL Redis], consulte [[!DNL Redis] Documentação](https://redis.io/docs/).
