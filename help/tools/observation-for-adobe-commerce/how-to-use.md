---
title: Como usar o nerdlet  [!DNL Observation for Adobe Commerce]
description: Saiba como usar o nerdlet  [!DNL Observation for Adobe Commerce] .
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Como usar o nerdlet [!DNL Observation for Adobe Commerce]

## Abordagem geral para analisar problemas

Verifique os estados dos recursos do ambiente:

* Examine a % de **[!UICONTROL Storage Free and MySQL % free storage by node]** quadros.

   * Siga os links no cabeçalho do quadro se houver pouco armazenamento.

* Examine a % de **[!UICONTROL free system memory and Swap memory free in bytes]** quadros.

   * Se esses estados exibirem uma memória muito baixa, eles poderão causar problemas.

* Examine o quadro **[!UICONTROL Alerts during the timeframe]**.

   * O Adobe Commerce na infraestrutura em nuvem fornece [!DNL Managed alerts]. Você pode clicar no link no cabeçalho para ver [!DNL Support Knowledge Base] artigos que ajudarão a determinar ações de sua parte para alertas específicos.

* Examine o quadro **[!UICONTROL CPU % by host]**: se ele estiver apresentando alta utilização da CPU, verifique o artigo [!DNL Support Knowledge Base] no cabeçalho do quadro. Além disso, verifique se as importações/exportações ou os backups do banco de dados não estão sendo feitos durante períodos de pico de tráfego.

* Verifique o quadro **[!UICONTROL Web Traffic volume compared to one week ago]**: se o tráfego for muito maior do que a semana anterior durante o mesmo período, ele pode ser explicado (campanha de venda ou novos produtos que foram comercializados, por exemplo)?
   * Se um aumento no tráfego não puder ser explicado, verifique o Tempo médio de resposta (milissegundos) para o ambiente de produção. O tráfego mais alto está contribuindo para um tempo de resposta diferente do normal? Expanda o período para ver se é uma anomalia.
   * O aumento no tráfego está afetando as transações da Web? Verifique se há erros no quadro **[!UICONTROL Response Code]**. Se o site estiver inativo, você pode clicar no link `Site Down?` no cabeçalho do quadro. O quadro identificará quaisquer erros que estejam ocorrendo e sua frequência.
   * Alguém implantou alterações no seu site? O quadro **[!UICONTROL Deployment Log Entries]** indicará se alguma implantação foi feita durante o período de problema. Se o problema ocorrer imediatamente após a implantação, pode ser que as atividades de implantação estejam adicionando mais carga ao site (caches limpos, serviços reiniciados etc.).
   * Ocorreu um upsize ou downsize? Se o site foi submetido a upsizing temporariamente, ele pode ter retornado ao tamanho de cluster original. Se uma solicitação foi feita para aumentar a capacidade do site, talvez ocorra um upsize. Verifique o quadro **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Esse quadro às vezes detecta uma interrupção em um determinado nó. Se o tamanho diminuir, isso pode indicar um problema com um ou mais nós.

* A guia **[!UICONTROL IP Frequency]** identifica a frequência de solicitação de endereços IP feitos nos servidores de origem (o que significa que a solicitação não pôde ser atendida de [!DNL Fastly], pois 74 não foi armazenada em cache).

   * Para quaisquer problemas relacionados a [!DNL Fastly], verifique o quadro **[!UICONTROL Fastly Cache]** e selecione a faceta Erro para ver a porcentagem de solicitações que são erros. Eles podem indicar um problema de backend se coincidirem com um carregamento que não seja da Web.
   * Se a carga não parece ser devido ao tráfego da Web, pode haver erros ou um acúmulo de solicitações que não sejam da Web, como consultas lentas ou [!DNL crons].

* Verifique o quadro **[!UICONTROL Database Errors]** quanto a erros que podem coincidir com a linha do tempo de problema/problema.
* Verifique o quadro **[!UICONTROL Database mysql-slow.log]** para identificar instruções SQL que estão ocorrendo. Os comandos `INSERT`, `UPDATE` e `DELETE` podem demorar um pouco se a consulta não estiver otimizada. Mesmo instruções `SELECT` podem ser muito ineficientes se feitas em tabelas grandes.
* Os quadros **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** mostrarão possíveis problemas com o PHP. O quadro **[!UICONTROL PHP States]** mostrará terminações, inícios e quando o serviço atingir o estado pronto por nó. O quadro **[!UICONTROL PHP Errors]** pode ajudar a isolar onde o problema está com o PHP, como tamanho da memória, workers ou o número de servidores.
* Para ver a latência nas transações, a tabela Transações - Média, Máx, Mín. pode ser classificada por coluna para mostrar a duração da transação de execução mais longa. Um cluster sobrecarregado terá durações latentes nas transações, mas também mostrará anomalias que podem apontar um problema com um método ou [!DNL cron].
* O quadro **[!UICONTROL Cron error]** mostrará [!DNL cron] bloqueios, erros de SQL que podem estar associados a [!DNL cron] logs e ao preparo compartilhado [!DNL crons] que pode estar em execução em ambientes de produção quando há um ambiente de preparo dedicado.
* O quadro [!UICONTROL ElasticSearch Errors] mostra erros que podem indicar problemas graves com [!DNL Elasticsearch] consultas, dados ou índices.
