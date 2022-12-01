---
title: "O [!UICONTROL CDN] tab"
description: Saiba mais sobre o [!UICONTROL CDN] guia de [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# O [!UICONTROL CDN] guia

Essa guia tem informações focadas na variável [!DNL content delivery network (CDN)]. No caso da Adobe Commerce Cloud, essa é a variável [!DNL Fastly] serviço.

## [!UICONTROL HIT rate]

![Taxa de HIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

O **[!UICONTROL HIT rate]** quadro mostra o número de solicitações que podem ser armazenadas em cache [!UICONTROL HITS] no último minuto. Isso indica o armazenamento em cache bem-sucedido. A seta para a direita mostrará a porcentagem acima ou abaixo da mesma hora da semana.

## [!UICONTROL HIT Processing]

![Processamento de HIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Essa **[!UICONTROL HIT processing]** mostra o número de solicitações que podem ser armazenadas em cache [!UICONTROL HITS] durante a semana.

## [!UICONTROL MISS rate]

![Taxa MISS](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Essa **[!UICONTROL MISS rate]** mostra o número de falhas de solicitações em cache no último minuto. Um erro é quando a solicitação não é armazenada em cache e a solicitação deve ser passada para o servidor de origem para veicular o conteúdo. O valor à direita é a comparação do aumento/diminuição para o número de minutos por minuto uma semana antes.

## [!UICONTROL MISS time]

![Hora de MISS](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Taxa de OCORRÊNCIA](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Porcentagem de erro](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

O **[!UICONTROL Error Percentage]** exibe o valor da porcentagem de ERRO de solicitações e mostra o aumento/diminuição relativo em comparação ao mesmo tempo uma semana antes.

## [!UICONTROL Total Requests]

![Total de solicitações](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Taxa de erro](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Resposta Média de Cache Rápido para o período de tempo selecionado em segundos](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Esse quadro mostra a duração, em segundos, das solicitações que podem ser armazenadas em cache, o que significa que se um `cache_response` é um [!UICONTROL MISS], exibe a média de respostas em cache perdidas para o tempo selecionado.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Cache Fasto de Resposta Média para o período de tempo selecionado em segundos faceado pelo POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Largura de banda total (todos os POPs) durante o período de tempo selecionado, em comparação com há 1 semana (% de aumento/diminuição)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Solicitações - Desde o período selecionado em comparação com uma semana atrás](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Esse quadro é semelhante à caixa de resumo para [!UICONTROL Total Requests] na parte superior, mas mostra a contagem de solicitações de semanas anteriores. Estas são todas as solicitações, não apenas solicitações que podem ser armazenadas em cache (onde `is_cacheable` é verdadeiro).

## [!UICONTROL Response Count]

![Contagem de respostas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Largura de banda por POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![5 URLs principais (códigos de status 5xx ou 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

O **[!UICONTROL Top 5 URLs]** mostra os 5 principais URLs que estão apresentando respostas de erro 5xx ou 3xx. Devido à restrição de espaço, será necessário passar o mouse sobre o URL para ver o código de erro específico associado a esse URL. (exemplo na caixa vermelha da figura acima).

## [!UICONTROL Top 25 URLs (200 status)]

![25 URLs principais (status 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

O **[!UICONTROL Top 25 URLs]** frame mostra os URLs que retornaram um status 200 por contagem durante o período selecionado.

## [!UICONTROL Duration by Response Status]

![Duração por Status de Resposta](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

O **[!UICONTROL Duration by Response Status]** O gráfico exibe as respostas do erro por contagem durante o período de tempo selecionado, faceado pelo código de status do erro.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Duração por Status de Resposta, 25 urls principais](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

O **[!UICONTROL Duration by Response Status, top 25 URLs]** O gráfico mostra os 25 principais URLs pela duração da resposta em segundos. Talvez seja necessário passar o mouse sobre o URL para ver todo o caminho. Além disso, para remover todo o URL, exceto um, clique nesse URL. Você pode adicionar outros URLs novamente clicando neles individualmente. Se desejar remover URLs individuais, mantenha a tecla e clique em cada URL para removê-los do gráfico.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Duração por Status de Resposta, 25 principais status que não são 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

O **[!UICONTROL Duration by Response Status, top 25 non-200 status]** é semelhante ao último, exceto que o foco está em códigos de status não-200 ou códigos de status de erro. Ele mostrará o código de erro e, em seguida, o URL. Talvez seja necessário passar o mouse sobre o URL para ver todo o caminho. Além disso, para remover todo o URL, exceto um, clique nesse URL. Você pode adicionar outros URLs novamente clicando neles individualmente. Se desejar remover URLs individuais, mantenha a tecla e clique em cada URL para removê-los do gráfico.

## [!UICONTROL Error Count by POP timeline]

![Contagem de erros por linha do tempo POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

O **[!UICONTROL Error Count by POP timeline]** O gráfico exibe a contagem dos status de erro na linha do tempo do período selecionado, faceada pelo código de erro.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Duração por status de resposta, 25 principais IP de cliente, status não 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

O **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** O gráfico mostra os endereços IP pela duração média no período selecionado, em que havia códigos de erro de status.

## [!UICONTROL IP Frequency]

![Frequência de IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

O **[!UICONTROL IP Frequency]** O quadro conta os status (&#39;MISS&#39; e &#39;PASS&#39;) para cada IP a partir do [!DNL Fastly] logs. As solicitações da Web com esses status alcançarão o servidor de origem e adicionarão carga ao servidor. Ele mostra os vinte principais endereços com frequência. Esse quadro pode ser usado para detectar ataques de IP ou fontes de carga pesada em um site. Esse gráfico também está presente na guia de resumo e é colocado aqui para fácil comparação a mais detalhes sobre o [!DNL Fastly] informações de log exibidas nesta guia.
