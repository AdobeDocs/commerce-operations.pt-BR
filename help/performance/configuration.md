---
title: Práticas recomendadas de configuração
description: Otimize o tempo de resposta da implantação do Adobe Commerce ou Magento Open Source usando essas práticas recomendadas.
source-git-commit: 20c4f55162b25be8906562c395abf4671437992b
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Práticas recomendadas de configuração

O Commerce fornece muitas configurações e ferramentas que você pode usar para melhorar o tempo de resposta nas páginas, além de oferecer uma taxa de transferência mais alta.

## Trabalhos Cron

Todas as operações assíncronas em [!DNL Commerce] são executados com o Linux `cron` comando. Consulte [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) para configurá-lo corretamente.

## Indexadores

Um indexador pode ser executado em **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]** modo. O **[!UICONTROL Update on Save]** O modo imediatamente indexa sempre que o catálogo ou outros dados forem alterados. Esse modo assume uma baixa intensidade das operações de atualização e navegação na sua loja. Pode levar a atrasos significativos e à indisponibilidade de dados durante cargas altas. Recomendamos usar **Atualização programada** modo em produção, pois armazena informações sobre atualizações de dados e realiza a indexação por partes em segundo plano por meio de um trabalho cron específico. Você pode alterar o modo de cada [!DNL Commerce] indexador separadamente no  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** página de configuração.

A reindexação no MariaDB 10.4 leva mais tempo em comparação com outros MariaDB ou [!DNL MySQL] versões. Como solução alternativa, sugerimos modificar a configuração padrão do MariaDB e definir os seguintes parâmetros:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Caches

Ao iniciar sua loja na produção, ative todos os caches do **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** página. Recomendamos usar [!DNL Varnish], pois é uma solução eficiente de cache de página de produção.

## Notificações por email assíncronas

Habilitar a configuração &quot;Notificações por email assíncronas&quot; move processos que lidam com as notificações por email de check-out e de processamento de pedidos para o segundo plano. Para ativar esse recurso, acesse **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulte [Emails de vendas](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) no _Guia do usuário do Magento Open Source_ para obter mais informações.

## Processamento assíncrono de dados de pedido

Pode haver momentos em que as vendas intensas em uma loja ocorrem ao mesmo tempo em que [!DNL Commerce] O está executando processamento intensivo de pedidos. Você pode configurar [!DNL Commerce] distinguir esses dois padrões de tráfego no nível do banco de dados para evitar conflitos entre operações de leitura e gravação nas tabelas correspondentes. Você pode armazenar e indexar dados do pedido de forma assíncrona. Os pedidos são colocados em armazenamento temporário e movidos em massa para a grade do Order Management sem conflitos. Você pode ativar essa opção em **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulte [Atualizações de Grade Programada](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) no _Guia do usuário do Magento Open Source_ para obter mais informações.

>[!WARNING]
>
>O **[!UICONTROL Developer]** e as opções só estão disponíveis em [Modo de desenvolvedor](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce na infraestrutura de nuvem](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) não suporta `Developer` modo.

## Atualização de estoque adiada

Em períodos de vendas intensas, [!DNL Commerce] O pode adiar atualizações de estoque relacionadas a pedidos. Isso minimiza o número de operações e acelera o processo de posicionamento do pedido. No entanto, essa opção é arriscada e só pode ser usada quando os Backorders forem ativados na loja, porque essa opção pode levar a quantidades negativas de estoque. Essa opção pode trazer uma melhoria significativa no desempenho dos fluxos de Check-out para lojas que podem facilmente repreencher seu estoque sob demanda. Para ativar atualizações de estoque adiadas em seu site, acesse **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulte [Gerenciamento de inventário](https://docs.magento.com/user-guide/catalog/inventory.html) no _Guia do usuário do Adobe Commerce_ para obter mais informações.

>[!INFO]
>
>Essa opção só estará disponível se **[!UICONTROL Backorder with any mode]** está ativada.

## Configurações de otimização do lado do cliente

Para melhorar a capacidade de resposta da loja de sua [!DNL Commerce] , acesse Admin no modo Padrão ou Desenvolvedor e altere as seguintes configurações:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Grupo de configurações | Configuração | Valor |
| ------------------- | -------------------------- | ------ |
| Configurações de grade | Indexação assíncrona | Habilitar |
| Configurações de CSS | Minimizar arquivos CSS | Sim |
| [!DNL JavaScript] Configurações | Minimizar [!DNL JavaScript] Arquivos | Sim |
| [!DNL JavaScript] Configurações | Habilitar [!DNL JavaScript] Pacote | Sim |
| Configurações do modelo | Minimizar HTML | Sim |

>[!INFO]
>
>O **[!UICONTROL Developer]** e as opções só estão disponíveis em [Modo de desenvolvedor](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] na infraestrutura em nuvem](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) não suporta `Developer` modo.

Quando você ativa o **[!UICONTROL Enable [!DNL JavaScript] Bundling]** , você permite que o Commerce mescle todos os recursos JS em um ou em um conjunto de pacotes que são carregados em páginas de loja. O pacote de JS resulta em menos solicitações para o servidor, o que melhora o desempenho da página. Também ajuda o navegador a armazenar em cache os recursos do JS na primeira chamada e reutilizá-los para qualquer navegação posterior. Essa opção também traz avaliação lenta, pois todo JS é carregado como texto. Ele inicia a análise e a avaliação do código somente após ações específicas serem acionadas na página. No entanto, essa configuração não é recomendada para armazenamentos em que o primeiro tempo de carregamento de página é extremamente crítico, pois todo o conteúdo JS será carregado na primeira chamada.

>[!INFO]
>
>Consulte [Otimização de arquivos CSS e Javascript no Adobe Commerce na infraestrutura em nuvem e no Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) no Adobe Commerce Help Center_ para obter mais informações sobre a otimização de CSS e Javascript.

### Dicas de pacote

* Recomendamos que você use ferramentas de terceiros para minificação e empacotamento (como [r.js](http://requirejs.org/)). [!DNL Commerce] os mecanismos integrados não são ideais e são enviados como alternativas de fallback.
* Ativar o protocolo HTTP2 pode ser uma boa alternativa para usar o pacote JS. O protocolo oferece praticamente os mesmos benefícios.
* Não recomendamos usar configurações obsoletas como mesclar arquivos JS e CSS, pois foram projetadas apenas para JS carregado de forma síncrona na seção HEAD da página. O uso dessa técnica pode fazer com que o empacotamento e a lógica do JS funcionem incorretamente.

## Programação de manutenção de banco de dados {#database}

Recomendamos executar backups periódicos do banco de dados para suas instâncias de Preparo e Produção. Devido à natureza intensa de E/S das operações de backup, você pode encontrar backups mais lentos e possíveis problemas. A execução de processos de banco de dados para vários ambientes ao mesmo tempo pode ser executada mais lentamente devido à contenção de recursos disponíveis.

Para um melhor desempenho, programe seus backups para serem executados sucessivamente, um de cada vez, em horários fora do horário de pico. Esse método evita a contenção de E/S e reduz o tempo de conclusão, especialmente para instâncias menores, bancos de dados maiores e assim por diante.

Por exemplo, recomendamos o agendamento de um backup do banco de dados de Produção seguido pelo banco de dados de Preparo quando suas lojas encontrarem visitas menores.
