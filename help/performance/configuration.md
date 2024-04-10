---
title: Práticas recomendadas de configuração
description: Otimize o tempo de resposta de sua implantação do Adobe Commerce ou Magento Open Source usando essas práticas recomendadas.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# Práticas recomendadas de configuração

O Commerce fornece muitas configurações e ferramentas que você pode usar para melhorar o tempo de resposta nas páginas, bem como fornecer uma taxa de transferência mais alta.

## Cron Jobs

Todas as operações assíncronas no [!DNL Commerce] são executados usando o Linux `cron` comando. Consulte [Configurar e executar o cron](../configuration/cli/configure-cron-jobs.md) para configurá-lo corretamente.

## Indexadores

Um indexador pode ser executado em **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]** modo. A variável **[!UICONTROL Update on Save]** O modo de indexação indexa imediatamente sempre que o catálogo ou outros dados são alterados. Esse modo assume uma baixa intensidade de operações de atualização e navegação na loja. Isso pode levar a atrasos significativos e indisponibilidade de dados durante cargas altas. Recomendamos usar **Atualização programada** para fins de desempenho, porque armazena informações sobre atualizações de dados e executa a indexação por partes no plano de fundo por meio de um trabalho cron específico. É possível alterar o modo de cada [!DNL Commerce] indexador separadamente no  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** página de configuração. A variável [!UICONTROL Customer Grid] o índice deve ser sempre definido como **[!UICONTROL Update on Save]** modo.

>[!TIP]
>
>A reindexação no MariaDB 10.4 e 10.6 leva mais tempo em comparação com outros MariaDB ou [!DNL MySQL] versões. Sugerimos modificar a configuração padrão do MariaDB, que é descrita na seção [pré-requisitos de instalação](../installation/prerequisites/database/mysql.md).

## Caches

Ao iniciar sua loja na produção, ative todos os caches do **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** página. Recomendamos usar [!DNL Varnish], pois é uma solução eficiente de cache de página de produção.

## Notificações de email assíncronas

A ativação da configuração &quot;Notificações de email assíncronas&quot; move processos que lidam com notificações de email de check-out e processamento de pedidos para o segundo plano. Para ativar esse recurso, vá para **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulte [Emails de vendas](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) no _Guia do usuário do Magento Open Source_ para obter mais informações.

## Processamento assíncrono de dados de pedido

Pode haver momentos em que as vendas intensas em uma loja ocorram ao mesmo tempo em que [!DNL Commerce] O está executando um processamento intensivo de pedidos. Você pode configurar [!DNL Commerce] distinguir esses dois padrões de tráfego no nível do banco de dados para evitar conflitos entre operações de leitura e gravação nas tabelas correspondentes. Você pode armazenar e indexar dados de pedido de maneira assíncrona. Os pedidos são colocados em armazenamento temporário e movidos em massa para a grade do Order Management sem colisões. É possível ativar essa opção em **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulte [Atualizações de Grade Agendadas](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) no _Guia do usuário do Magento Open Source_ para obter mais informações.

>[!WARNING]
>
>A variável **[!UICONTROL Developer]** A guia e as opções só estão disponíveis em [Modo de desenvolvedor](../configuration/cli/set-mode.md). [Adobe Commerce na infraestrutura em nuvem](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) não suporta `Developer` modo.

## Salvamento assíncrono de configuração

Para projetos com um grande número de configurações no nível da loja, salvar uma configuração de loja pode levar um tempo excessivo ou resultar em um tempo limite. A variável _Configuração assíncrona_ O módulo permite salvamentos assíncronos de configuração executando um trabalho cron que usa um consumidor para processar o salvamento em uma fila de mensagens. AsyncConfig está **desabilitado** por padrão.

Você pode ativar o AsyncConfig usando a interface de linha de comando:

```bash
bin/magento setup:config:set --config-async 1
```

A variável `set` O comando grava o seguinte no `app/etc/env.php` arquivo:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Inicie o seguinte Consumidor para começar a processar as mensagens na fila na base primeiro a entrar primeiro a sair:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Atualização de estoque adiada

Em tempos de vendas intensas, [!DNL Commerce] pode adiar atualizações de estoque relacionadas a pedidos. Isso minimiza o número de operações e acelera o processo de colocação de pedidos. No entanto, essa opção é arriscada e só pode ser usada quando Backorders são ativados no armazenamento, porque essa opção pode levar a quantidades de estoque negativas. Essa opção pode trazer uma melhora significativa no desempenho dos fluxos de saída para lojas que podem facilmente reabastecer seu estoque sob demanda. Para ativar atualizações de estoque adiadas no site, acesse **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulte [Gerenciar inventário](https://docs.magento.com/user-guide/catalog/inventory.html) no _Guia do usuário do Adobe Commerce_ para obter mais informações.

>[!INFO]
>
>Essa opção só estará disponível se **[!UICONTROL Backorder with any mode]** está ativado.

>[!INFO]
>
>Essa opção também funciona com [Posicionamento assíncrono de pedidos](high-throughput-order-processing.md#asynchronous-order-placement) em combinação com [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Configurações de otimização do lado do cliente

Para melhorar a capacidade de resposta da loja [!DNL Commerce] , vá para o Administrador no modo Padrão ou Desenvolvedor e altere as seguintes configurações:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Grupo de configurações | Configuração | Valor |
| ------------------- | -------------------------- | ------ |
| Configurações da grade | Indexação assíncrona | Ativar |
| Configurações de CSS | Reduzir arquivos CSS | Sim |
| [!DNL JavaScript] Configurações | Minify [!DNL JavaScript] Arquivos | Sim |
| [!DNL JavaScript] Configurações | Ativar [!DNL JavaScript] Agrupamento | Sim |
| Configurações do modelo | Minify HTML | Sim |

>[!INFO]
>
>A variável **[!UICONTROL Developer]** A guia e as opções só estão disponíveis em [Modo de desenvolvedor](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] na infraestrutura em nuvem](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) não suporta `Developer` modo.

Quando você ativa o **[!UICONTROL Enable [!DNL JavaScript] Bundling]** , você permite que o Commerce mescle todos os recursos JS em um ou um conjunto de pacotes carregados nas páginas da loja. O agrupamento de JS resulta em menos solicitações para o servidor, o que melhora o desempenho da página. Também ajuda o navegador a armazenar em cache recursos JS na primeira chamada e a reutilizá-los para navegação adicional. Essa opção também traz uma avaliação lenta, pois todo o JS é carregado como texto. Ele inicia a análise e a avaliação do código somente após ações específicas serem acionadas na página. No entanto, essa configuração não é recomendada para lojas em que o tempo de carregamento da primeira página é extremamente crítico, pois todo o conteúdo JS será carregado na primeira chamada.

>[!INFO]
>
>Consulte [Otimização de arquivos CSS e Javascript no Adobe Commerce na infraestrutura em nuvem e no Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) na Central de ajuda do Adobe Commerce_ para obter mais informações sobre como otimizar o CSS e o Javascript.

### Dicas de agrupamento

* Recomendamos que você use ferramentas de terceiros para minificação e agrupamento (como [r.js](https://requirejs.org/)). [!DNL Commerce] os mecanismos integrados não são ideais e são enviados como alternativas de fallback.
* A ativação do protocolo HTTP/2 pode ser uma boa alternativa para usar o empacotamento JS. O protocolo oferece muitos dos mesmos benefícios. Ela é ativada por padrão na Adobe Commerce em projetos de infraestrutura em nuvem.
* Não recomendamos usar configurações obsoletas, como mesclar arquivos JS e CSS, pois foram projetadas apenas para JS carregado de forma síncrona na seção HEAD da página. O uso dessa técnica pode fazer com que o agrupamento e a lógica requireJS funcionem incorretamente.

## Validação de segmentos de cliente

Comerciantes que têm um grande número de [segmentos de clientes](https://docs.magento.com/user-guide/marketing/customer-segments.html) podem sofrer uma degradação significativa do desempenho com ações do cliente, como fazer logon no cliente e adicionar produtos ao carrinho.

As ações do cliente acionam um processo de validação para segmentos de clientes, que é o que pode causar degradação do desempenho. Por padrão, o Adobe Commerce valida cada segmento em tempo real para definir quais segmentos de clientes são correspondidos e quais não são.

Para evitar a degradação do desempenho, é possível definir o **[!UICONTROL Real-time Check if Customer is Matched by Segment]** opção de configuração do sistema para **Não** para validar segmentos de clientes por uma única consulta SQL de condição combinada.

Para ativar essa otimização, vá para **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Essa configuração melhora o desempenho da validação de segmentos de clientes se houver muitos segmentos de clientes no sistema. No entanto, não funciona com [banco de dados dividido](../configuration/storage/multi-master.md) ou quando não houver clientes registrados.

## Agendamento de manutenção do banco de dados {#database}

Recomendamos executar backups periódicos do banco de dados para suas instâncias de Preparo e Produção. Devido à natureza intensiva de I/O das operações de backup, você pode encontrar backups mais lentos e possíveis problemas. A execução de processos de banco de dados para vários ambientes ao mesmo tempo pode ser mais lenta devido à contenção dos recursos disponíveis.

Para obter melhor desempenho, agende seus backups para serem executados sucessivamente, um de cada vez, fora dos horários de pico. Esse método evita a contenção de I/O e reduz o tempo de conclusão, especialmente para instâncias menores, bancos de dados maiores e assim por diante.

Por exemplo, recomendamos agendar um backup do banco de dados de Produção seguido pelo banco de dados de Preparo quando suas lojas encontrarem visitas menores.

## Limitar número de produtos na grade

Para melhorar o desempenho da grade de produtos para catálogos grandes, recomendamos limitar o número de produtos na grade com o **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** definição da configuração do sistema.

Essa configuração do sistema está desabilitada por padrão. Ao ativá-la, é possível limitar o número de produtos na grade a um valor específico. **[!UICONTROL Records Limit]** é uma configuração personalizável com um valor mínimo padrão de `20000`.
Quando a variável **[!UICONTROL Limit Number of Products in Grid]** estiver ativada e o número de produtos na grade for maior que o limite de registro, a coleção limitada de registros será retornada. Quando o limite é atingido, o total de registros encontrados, o número de registros selecionados e os elementos de paginação ficam ocultos no cabeçalho da grade.

Quando o número total de produtos na grade é limitado, isso não afeta as ações de massa da grade de produtos. Ela afeta apenas a camada de apresentação da grade de produtos. Por exemplo, há um número limitado de `20000` produtos na grade, o usuário clica em **[!UICONTROL Select All]**, seleciona a variável **[!UICONTROL Update attributes]** ação em massa e atualiza alguns atributos. Como resultado, todos os produtos são atualizados, não a coleção limitada de `20000` registros.

A limitação da grade de produtos afeta apenas as coleções de produtos usadas pelos componentes da interface do usuário. Como resultado, nem todas as grades de produtos são afetadas por essa limitação. Somente aqueles que estão usando `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
É possível limitar as coleções de grade de produto somente nas seguintes páginas:

* Grade de Produtos do Catálogo
* Adicionar grade de produtos relacionados/venda adicional/venda cruzada
* Adicionar produtos ao produto do pacote
* Adicionar produtos ao produto do grupo
* Página Criar pedido do administrador

Se você não quiser que a grade de produtos seja limitada, recomendamos usar filtros mais precisamente para que a coleção de resultados tenha menos itens do que **[!UICONTROL Records Limit]**.
