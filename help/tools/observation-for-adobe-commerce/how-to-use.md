---
title: '"Como usar o [!DNL Observation for Adobe Commerce] nerdlet"'
description: Saiba como usar o [!DNL Observation for Adobe Commerce] nerdlet.
source-git-commit: 69bcb755c3c1f9a820856ac69ce12eb85c686213
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Como usar o [!DNL Observation for Adobe Commerce] nerd

## Abordagem geral para analisar questões

Verifique os estados dos recursos do ambiente:

* Examine a % de **[!UICONTROL Storage Free and MySQL % free storage by node]** quadros.

   * Siga os links no cabeçalho do quadro, caso veja pouco armazenamento.

* Examine a % de **[!UICONTROL free system memory and Swap memory free in bytes]** quadros.

   * Se eles exibirem estados de memória muito baixos, eles podem ser contribuidores para problemas.

* Examine a **[!UICONTROL Alerts during the timeframe]** quadro.

   * O Adobe Commerce na infraestrutura de nuvem fornece [!DNL Managed alerts]. Você pode clicar no link no cabeçalho para ver [!DNL Support Knowledge Base] artigos que ajudarão a determinar ações de sua parte para alertas específicos.

* Examine a **[!UICONTROL CPU % by host]** quadro: Se estiver exibindo alto uso da CPU, verifique a [!DNL Support Knowledge Base] artigo no cabeçalho do quadro. Além disso, verifique se as importações/exportações ou backups do banco de dados não estão sendo realizados durante os períodos de pico de tráfego.

* Verifique a **[!UICONTROL Web Traffic volume compared to one week ago]** quadro: Se o tráfego for muito maior do que a semana anterior durante o mesmo período, pode ser explicado (campanha de venda ou novos produtos que foram comercializados, por exemplo)?
   * Se um aumento no tráfego não puder ser explicado, verifique o Tempo médio de resposta (milissegundos) para o ambiente de produção. O tráfego maior está contribuindo para um tempo de resposta diferente do normal? Expanda o período para ver se é uma anomalia.
   * O aumento no tráfego afeta as transações da Web? Verifique a **[!UICONTROL Response Code]** quadro para erros. Se o site estiver inativo, você pode clicar no link *[!UICONTROL Site Down?]* link no cabeçalho do quadro. O quadro identificará os erros que estão ocorrendo e sua frequência.
   * Alguém implantou alterações em seu site? O **[!UICONTROL Deployment Log Entries]** O quadro indicará se alguma implantação foi feita durante o período de problema. Se o problema for imediatamente após a implantação, pode ser que as atividades de implantação estejam adicionando carga adicional ao site (caches limpos, serviços reiniciados, etc.).
   * Ocorreu um tamanho de atualização ou de inatividade? Se seu site foi atualizado temporariamente, ele pode ter retornado ao tamanho original do cluster. Se uma solicitação foi feita para aumentar a capacidade do site, pode ocorrer um aumento. Verifique a **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** quadro. Esse quadro às vezes detecta uma interrupção em um nó específico. Se o tamanho diminuir, isso pode indicar um problema com um ou mais nós.

* O **[!UICONTROL IP Frequency]** A guia identifica a frequência da solicitação de endereços IP que são feitos em relação aos servidores de origem (o que significa que a solicitação não pôde ser veiculada [!DNL Fastly] como 74, ele não foi armazenado em cache).

   * Para qualquer [!DNL Fastly] problemas relacionados, verifique a **[!UICONTROL Fastly Cache]** e selecione a faceta Erro para ver a porcentagem de solicitações que são erros. Eles podem indicar um problema de backend se coincidirem com uma carga que não é da Web.
   * Se a carga não parecer ser devido ao tráfego da Web, pode haver erros ou uma build de solicitações que não sejam da Web, como consultas lentas ou crons.

* Verifique a **[!UICONTROL Database Errors]** quadro para erros que podem coincidir com a linha do tempo do problema/problema.
* Verifique a **[!UICONTROL Database mysql-slow.log]** quadro para identificar instruções SQL que estão ocorrendo. `INSERT`, `UPDATE`e `DELETE` os comandos podem levar algum tempo se o query não estiver otimizado. Mesmo `SELECT` instruções podem ser muito ineficientes se feitas em tabelas grandes.
* **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** os quadros mostrarão possíveis problemas com o PHP. O **[!UICONTROL PHP States]** o quadro mostrará terminações do processo PHP, inicializações e quando o serviço atingir o estado pronto por nó. O **[!UICONTROL PHP Errors]** pode ajudar a isolar onde o problema está no PHP, como tamanho da memória, trabalhadores ou o número de servidores.
* Para ver a latência nas transações, a tabela Transactions - Avg, Max, Min pode ser classificada por coluna para mostrar a duração da transação mais longa. Um cluster sobrecarregado terá durações latentes em transações, mas também mostrará anomalias que podem apontar um problema com um método ou cron.
* O **[!UICONTROL Cron error]** o quadro mostrará bloqueios de cron, erros de SQL que podem ser associados a logs de cron e crons de preparo compartilhados que podem estar sendo executados em ambientes de produção quando houver um ambiente de preparo dedicado.
* O [!UICONTROL ElasticSearch Errors] o quadro mostra erros que podem indicar grandes problemas com [!DNL Elasticsearch] consultas, dados ou índices.
