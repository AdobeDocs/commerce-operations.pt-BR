---
title: Configuração avançada
description: Revise as práticas recomendadas e recomendações para sistemas empresariais de grande porte, projetados para processar grandes volumes de dados.
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---


# Configuração avançada

[!DNL Commerce] O é um produto altamente flexível e escalável que contém soluções para comerciantes de todos os tamanhos. Esta seção aborda as práticas recomendadas e recomendações sobre como configurar [!DNL Commerce] para trabalhar com grandes quantidades de dados, carga extrema e outros casos corporativos.

## Calibrar o desempenho do índice

Ao lidar com grandes quantidades de dados, a reindexação pode se tornar uma preocupação. O [!DNL Commerce] A equipe selecionou os índices mais carregados e a indexação em lote ativada, o que permite definir uma parte dos dados a serem processados em cada iteração. Dessa forma, o usuário pode ajustar os tamanhos do lote com base no tipo e no tamanho dos dados no banco de dados.

Para gerenciar essa configuração, edite o `batchRowsCount` no `di.xml` do módulo correspondente. Os seguintes índices são compatíveis com esse recurso:

* Índice de produtos de categoria (módulo de catálogo)
* Índice de preços (módulo do catálogo)
* Índice EAV (módulo do catálogo)
* Índice de Estoque (Módulo CatalogInventory)

Você pode ajustar o desempenho do indexador ajustando as variáveis de tamanho do lote de índice. Isso controla quantas entidades são processadas por vez pelo indexador. Em algumas situações, assistimos a reduções significativas no tempo de indexação.

Por exemplo, se você estiver executando um perfil semelhante à Média B2B, é possível substituir o valor da configuração `batchRowsCount` em `app/code/Magento/catalog/etc/di.xml` e substituir o valor padrão de `5000` para `1000`. Isso reduz o tempo total de indexação de 4 horas para 2 horas com um padrão [!DNL MySQL] configuração.

>[!NOTE]
>
>Não ativamos o agrupamento para o indexador de regras de catálogo. Os comerciantes com um grande número de regras de catálogos precisam ajustar seus [!DNL MySQL] configuração para otimizar o tempo de indexação. Nesse caso, a edição de [!DNL MySQL] o arquivo de configuração e a alocação de mais memória para os valores de configuração TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE (o padrão é 16M para ambos) melhorarão o desempenho desse indexador, mas resultarão em [!DNL MySQL] consumindo mais RAM.

### Limitar grupos de clientes e catálogos compartilhados por sites

Um grande número de SKUs de produtos, sites, grupos de clientes ou catálogos compartilhados afetará o tempo de execução dos indexadores de Preço do produto e Regra do catálogo. Isso ocorre porque, por padrão, todos os sites são atribuídos a todos os grupos de clientes (catálogos compartilhados).

Para diminuir o tempo de indexação, você pode [excluir determinados sites dos grupos de clientes (catálogos compartilhados)](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexer-optimization.html#customer-group-limitations-by-websites).

## Configurar Redis

Às vezes, uma instância de Redis não é suficiente para atender às solicitações recebidas. Há várias soluções que podemos recomendar para resolver essa situação.

Primeiro, [!DNL Commerce] O permite configurar armazenamento de cache separado para cada tipo de cache. Isso permite instalar quantas instâncias separadas do Redis forem o número de tipos de cache registrados no Magento. De forma realista, você pode querer instâncias de Redis para os caches usados mais ativamente, como configuração, layout e blocos.

Outra solução pode ser colocar o cache de configuração no sistema de arquivos e mover os outros caches para o servidor Redis. Com essa solução, você precisa de uma ferramenta separada para a invalidação centralizada do cache de configuração em todos os nós da Web.

Você também pode usar um cluster Redis que executa operações paralelas de leitura/gravação com um número de nós que aumenta automaticamente. [!DNL Commerce] O não fornece configuração para esse caso, mas pode ser iniciado com pequenas personalizações.

## Configurar [!DNL RabbitMQ]

Magento Open Source e Adobe [!DNL Commerce] suporte a filas de mensagens implementadas por meio de [!DNL RabbitMQ]. [!DNL Commerce] O usa esse serviço para executar várias operações assíncronas, incluindo operações de catálogo B2B e atualizações assíncronas de estoque. Todas as interfaces para adicionar mais tarefas ao servidor de tarefas são distribuídas com o produto e estão disponíveis para implementação de lógica assíncrona personalizada no escopo de extensões de terceiros. Como em qualquer outra integração, [!DNL Commerce] fornece um exemplo de arquivo de configuração para [!DNL RabbitMQ] que contém todas as configurações recomendadas e está totalmente pronto para o uso da produção.

## Dividir o banco de dados

>[!WARNING]
>
>O recurso de banco de dados dividido era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) na versão 2.4.2 do Adobe Commerce. Consulte [Reverter de um banco de dados dividido para um único banco de dados](https://devdocs.magento.com/guides/v2.4/config-guide/revert-split-database.html).

O Adobe Commerce permite configurar o armazenamento escalável de banco de dados para atender às necessidades de uma empresa em crescimento. Você pode configurar três bancos de dados principais separados que atendem a domínios específicos:

* Banco de dados principal (catálogo)
* Banco de Dados de Check-out
* Base de Dados OMS (Order Management System)

Para configurar bancos de dados adicionais, você deve criar um banco de dados vazio e executar um dos seguintes comandos:

Para Check-out do Banco de Dados Principal

```bash
bin/magento setup:db-schema:split-quote
```

Para OMS Principal DB

```bash
bin/magento setup:db-schema:split-sales
```

Esses comandos migram tabelas de domínio específicas do banco de dados principal para um banco de dados de domínio. Eles também mudam a [!DNL Commerce] configuração para permitir conectividade correspondente e processamento de restrições.

Com bancos de dados separados para check-out e Order Management, é possível distribuir a carga entre os servidores do banco de dados. Você pode veicular mais finalizações e processar mais pedidos por segundo sem afetar a disponibilidade do catálogo e de outras operações. Recomendamos dividir bancos de dados para períodos de vendas flash ou ativas, ou usá-los permanentemente para projetos naturalmente de alta carga. A migração dos dados atuais entre bancos de dados deve ser executada sob a supervisão do administrador do sistema.  Não divida bancos de dados no modo Produção.

Além de bancos de dados principais, [!DNL Commerce] O permite configurar vários bancos de dados escravos (um para cada recurso de dados declarado no sistema). Um banco de dados escravo serve como uma réplica completa do banco de dados principal ou um dos bancos de dados principais do domínio. Ele é emitido para operações de leitura em um recurso específico.

Você pode adicionar um banco de dados subordinado executando o seguinte comando:

```bash
bin/magento setup:db-schema:add-slave
```

Esse comando executa alterações de configuração, mas não configura a replicação propriamente dita. Isso deve ser feito manualmente.

Depois de dividir o banco de dados principal e definir bancos de dados escravos, [!DNL Commerce] O regula automaticamente as conexões com um banco de dados específico, tomando decisões com base no tipo de solicitação (POST, PUT, GET, etc.) e no recurso de dados. If [!DNL Commerce] Para que suas extensões executem operações de gravação em uma solicitação GET, o sistema alterna automaticamente a conexão do banco de dados subordinado para o principal. Funciona da mesma forma com bancos de dados principais: assim que você trabalha com uma tabela relacionada ao check-out, o sistema redireciona todas as consultas para um banco de dados específico. Enquanto isso, todas as consultas relacionadas ao catálogo irão para o banco de dados principal.

Para obter mais detalhes sobre a configuração e os benefícios de várias configurações principais/escravas, consulte
[Solução de desempenho de banco de dados dividida](https://devdocs.magento.com/guides/v2.4/config-guide/multi-master/multi-master.html).

## Fornecer conteúdo de mídia

O Magento não fornece integração específica para veicular e fornecer conteúdo de mídia. Todas as abordagens comuns podem ser usadas juntas no Magento.

A maneira mais fácil de veicular conteúdo de mídia é entregá-lo e armazená-lo em cache em um [!DNL Varnish] servidor. Essa abordagem assume um sistema de arquivos compartilhados para armazenar conteúdo de mídia ou um servidor dedicado apontando para [!DNL Varnish].

Para ambientes de médio e alto carregamento, recomendamos usar serviços de Rede de entrega de conteúdo (CDN) como Fastly, Akamai e outros. Ao trabalhar com esses serviços, [!DNL Commerce] O usa a abordagem de pull clássica para atualizações de conteúdo. Você deve configurar [!DNL Commerce] URLs para funcionar com o serviço CDN correspondente. Ao mover o conteúdo de mídia para um CDN, você diminuirá significativamente a carga em suas instâncias.

## Configurar armazenamento de log

O armazenamento de logs e sua influência em outras operações de disco afeta a disponibilidade dos nós da Web, especialmente em situações de alta carga. Recomendamos que você minimize o registro se não precisar. Você também pode configurar o registro para que ele grave em um sistema de armazenamento separado que tenha altas velocidades de acesso. Observe que qualquer gargalo no acesso ao armazenamento de log pode afetar diretamente o processamento de solicitações recebidas que registram operações de gravação ou leitura como parte de seu fluxo.
