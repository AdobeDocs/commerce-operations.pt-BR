---
title: Como usar o [!DNL Observation for Adobe Commerce] nerdlet
description: Saiba como usar o [!DNL Observation for Adobe Commerce] nerdlet.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Como usar o [!DNL Observation for Adobe Commerce] nerdlet

## Abordagem geral para analisar problemas

Verifique os estados dos recursos do ambiente:

* Examinar a % de **[!UICONTROL Storage Free and MySQL % free storage by node]** quadros.

   * Siga os links no cabeçalho do quadro se houver pouco armazenamento.

* Examinar a % de **[!UICONTROL free system memory and Swap memory free in bytes]** quadros.

   * Se esses estados exibirem uma memória muito baixa, eles poderão causar problemas.

* Examine o **[!UICONTROL Alerts during the timeframe]** quadro.

   * O Adobe Commerce na infraestrutura em nuvem oferece [!DNL Managed alerts]. Você pode clicar no link no cabeçalho para ver [!DNL Support Knowledge Base] artigos que ajudarão a determinar ações de sua parte para alertas específicos.

* Examine o **[!UICONTROL CPU % by host]** frame: se ele estiver exibindo alta utilização da CPU, verifique o [!DNL Support Knowledge Base] no cabeçalho do quadro. Além disso, verifique se as importações/exportações ou os backups do banco de dados não estão sendo feitos durante períodos de pico de tráfego.

* Verifique a **[!UICONTROL Web Traffic volume compared to one week ago]** quadro: se o tráfego for muito maior do que a semana anterior durante o mesmo período, ele pode ser explicado (campanha de venda ou novos produtos que foram comercializados, por exemplo)?
   * Se um aumento no tráfego não puder ser explicado, verifique o Tempo médio de resposta (milissegundos) para o ambiente de produção. O tráfego mais alto está contribuindo para um tempo de resposta diferente do normal? Expanda o período para ver se é uma anomalia.
   * O aumento no tráfego está afetando as transações da Web? Verifique a **[!UICONTROL Response Code]** quadro para erros. Se o site estiver inativo, você pode clicar no link `Site Down?` no cabeçalho do quadro. O quadro identificará quaisquer erros que estejam ocorrendo e sua frequência.
   * Alguém implantou alterações no seu site? A variável **[!UICONTROL Deployment Log Entries]** indicará se alguma implantação foi feita durante o período do problema. Se o problema ocorrer imediatamente após a implantação, pode ser que as atividades de implantação estejam adicionando mais carga ao site (caches limpos, serviços reiniciados etc.).
   * Ocorreu um upsize ou downsize? Se o site foi submetido a upsizing temporariamente, ele pode ter retornado ao tamanho de cluster original. Se uma solicitação foi feita para aumentar a capacidade do site, talvez ocorra um upsize. Verifique a **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** quadro. Esse quadro às vezes detecta uma interrupção em um determinado nó. Se o tamanho diminuir, isso pode indicar um problema com um ou mais nós.

* A variável **[!UICONTROL IP Frequency]** A guia identifica a frequência de solicitação de endereços IP feitos nos servidores de origem (o que significa que a solicitação não pôde ser atendida a partir do [!DNL Fastly] como 74, não foi armazenado em cache).

   * Para qualquer [!DNL Fastly] problemas relacionados, verifique a **[!UICONTROL Fastly Cache]** e selecione a faceta Erro para ver a porcentagem de solicitações que são erros. Eles podem indicar um problema de backend se coincidirem com um carregamento que não seja da Web.
   * Se a carga não parecer ser devido ao tráfego da Web, pode haver erros ou um acúmulo de solicitações que não sejam da Web, como consultas lentas ou [!DNL crons].

* Verifique a **[!UICONTROL Database Errors]** quadro para erros que podem coincidir com a linha do tempo de problema/problema.
* Verifique a **[!UICONTROL Database mysql-slow.log]** quadro para identificar instruções SQL que estão ocorrendo. `INSERT`, `UPDATE`, e `DELETE` Os comandos podem demorar um pouco se a consulta não for otimizada. Par `SELECT` as instruções podem ser muito ineficientes se feitas em tabelas grandes.
* **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** os quadros mostrarão possíveis problemas com o PHP. A variável **[!UICONTROL PHP States]** frame mostrará terminações de processo PHP, inicializações e quando o serviço atingir o estado pronto por nó. A variável **[!UICONTROL PHP Errors]** frame pode ajudar a isolar onde o problema está com o PHP, como tamanho da memória, workers ou o número de servidores.
* Para ver a latência nas transações, a tabela Transações - Média, Máx, Mín. pode ser classificada por coluna para mostrar a duração da transação de execução mais longa. Um cluster sobrecarregado terá durações latentes nas transações, mas também mostrará anomalias que podem apontar um problema com um método ou [!DNL cron].
* A variável **[!UICONTROL Cron error]** o quadro será exibido [!DNL cron] bloqueios, erros de SQL que podem estar associados a [!DNL cron] logs e estágios compartilhados [!DNL crons] que pode estar sendo executado em ambientes de produção quando há um ambiente de preparo dedicado.
* A variável [!UICONTROL ElasticSearch Errors] mostra erros que podem indicar problemas graves com [!DNL Elasticsearch] consultas, dados ou índices.
