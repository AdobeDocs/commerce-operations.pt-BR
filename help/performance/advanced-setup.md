---
title: Configuração avançada
description: Analise as práticas recomendadas e as recomendações para sistemas de grandes empresas projetados para processar grandes volumes de dados.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# Configuração avançada

[!DNL Commerce] O é um produto altamente flexível e escalonável que contém soluções para comerciantes de todos os tamanhos. Esta seção aborda práticas recomendadas e recomendações sobre como configurar o [!DNL Commerce] para trabalhar com grandes quantidades de dados, carga extrema e outros casos corporativos.

## Desempenho de calibração de índice

Ao lidar com grandes quantidades de dados, a reindexação pode se tornar uma preocupação. A variável [!DNL Commerce] a equipe selecionou os índices mais carregados e ativou a indexação em lote, que permite definir uma parte dos dados a serem processados em cada iteração. Dessa forma, o usuário pode ajustar os tamanhos do lote com base no tipo e no tamanho dos dados no banco de dados.

Para gerenciar essa configuração, edite o `batchRowsCount` parâmetro no `di.xml` do módulo correspondente. Os seguintes índices oferecem suporte a esse recurso:

* Índice de Produtos de Categoria (Módulo de Catálogo)
* Índice de preços (Módulo de catálogo)
* Índice EAV (Módulo de catálogo)
* Índice de estoque (CatalogInventory Module)

Você pode ajustar o desempenho do indexador ajustando as variáveis de tamanho do agrupamento de índice. Isto controla quantas entidades são processadas por vez pelo indexador. Em algumas situações, vimos reduções significativas no tempo de indexação.

Por exemplo, se você estiver executando um perfil semelhante a Meio B2B, poderá substituir o valor de configuração `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` e substituirá o valor padrão de `5000` para `1000`. Isso reduz o tempo de indexação completa de 4 horas para 2 horas com um padrão [!DNL MySQL] configuração.

>[!NOTE]
>
>Não ativamos o agrupamento para o indexador de regras de catálogo. Os comerciantes com um grande número de regras de catálogos precisam ajustar seus [!DNL MySQL] configuração para otimizar o tempo de indexação. Nesse caso, editar o [!DNL MySQL] arquivo de configuração e alocar mais memória para os valores de configuração TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE (o padrão é 16M para ambos) melhorará o desempenho desse indexador, mas resultará em [!DNL MySQL] consumindo mais RAM.

### Limitar grupos de clientes e catálogos compartilhados por sites

Um grande número de SKUs de produtos, sites, grupos de clientes ou catálogos compartilhados afetará o tempo de execução dos indexadores de Preço do produto e Regra do catálogo. Isso ocorre porque, por padrão, todos os sites são atribuídos a todos os grupos de clientes (catálogos compartilhados).

Para diminuir o tempo de indexação, é possível [excluir determinados sites dos grupos de clientes (catálogos compartilhados)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Configurar Redis

Às vezes, uma instância do Redis não é suficiente para atender às solicitações recebidas. Há várias soluções que podemos recomendar para resolver essa situação.

Primeiro, [!DNL Commerce] permite configurar o armazenamento em cache separado para cada tipo de cache. Isso permite que você instale quantas instâncias Redis separadas forem o número de tipos de cache registrados no Magento. Na prática, você pode desejar instâncias do Redis para os caches usados mais ativamente, como configuração, layout e blocos.

Outra solução pode ser colocar o cache de configuração no sistema de arquivos e mover os outros caches para o servidor Redis. Com essa solução, você precisa de uma ferramenta separada para a invalidação centralizada do cache de configuração em todos os nós da Web.

Você também pode usar um cluster Redis que executa operações paralelas de leitura/gravação com um número de nós que aumenta automaticamente. [!DNL Commerce] O não fornece configuração para esse caso, mas pode ser iniciado com pequenas personalizações.

## Configurar [!DNL RabbitMQ]

MAGENTO OPEN SOURCE e ADOBE [!DNL Commerce] filas de mensagens de suporte implementadas por meio do [!DNL RabbitMQ]. [!DNL Commerce] O usa esse serviço para executar várias operações assíncronas, incluindo operações de catálogo B2B e atualizações de estoque assíncronas. Todas as interfaces para adicionar mais trabalhos ao servidor de trabalhos são distribuídas com o produto e estão disponíveis para implementação de lógica assíncrona personalizada no escopo de extensões de terceiros. Como em qualquer outra integração, [!DNL Commerce] O fornece um exemplo de arquivo de configuração para [!DNL RabbitMQ] que contém todas as configurações recomendadas e está totalmente pronto para uso de produção.

## Dividir o banco de dados

>[!WARNING]
>
>O recurso de banco de dados dividido foi [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) na versão 2.4.2 do Adobe Commerce. Consulte [Reverter de um banco de dados dividido para um único banco de dados](../configuration/storage/revert-split-database.md).

O Adobe Commerce permite configurar o armazenamento de banco de dados escalável para atender às necessidades de uma empresa em crescimento. Você pode configurar três bancos de dados mestres separados que atendem a domínios específicos:

* Banco de Dados Principal (Catálogo)
* Fazer check-out do banco de dados
* Banco de Dados do OMS (Order Management System)

Para configurar bancos de dados adicionais, você deve criar um banco de dados vazio e executar um dos seguintes comandos:

Para o BD Mestre de Check-out

```bash
bin/magento setup:db-schema:split-quote
```

Para OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Esses comandos migram tabelas de domínio específicas do banco de dados principal para um banco de dados de domínio. Eles também alteram o [!DNL Commerce] para permitir conectividade correspondente e processamento de restrições.

Com bancos de dados separados para checkout e Order Management, é possível distribuir a carga entre os servidores de banco de dados. Você pode fazer mais check-outs e processar mais pedidos por segundo sem afetar a disponibilidade do catálogo e de outras operações. Recomendamos dividir bancos de dados por períodos de vendas rápidas ou ativas ou usá-los permanentemente para projetos naturalmente de alta carga. A migração de dados atuais entre bancos de dados deve ser executada sob a supervisão do administrador do sistema.  Não divida os bancos de dados enquanto estiver no modo de Produção.

Além dos bancos de dados mestre, [!DNL Commerce] permite configurar vários bancos de dados subordinados (um para cada recurso de dados declarado no sistema). Um banco de dados subordinado serve como uma réplica completa do banco de dados principal ou de um dos bancos de dados mestre do domínio. É emitido para operações de leitura em um recurso específico.

Você pode adicionar um banco de dados subordinado executando o seguinte comando:

```bash
bin/magento setup:db-schema:add-slave
```

Esse comando executa alterações de configuração, mas não configura a própria replicação. Isso deve ser feito manualmente.

Depois de dividir o banco de dados mestre e definir bancos de dados escravos, [!DNL Commerce] O regula automaticamente as conexões com um banco de dados específico, tomando decisões com base no tipo de solicitação (POST, PUT, GET etc.) e no recurso de dados. Se [!DNL Commerce] Para que suas extensões executem operações de gravação em uma solicitação GET, o sistema alterna automaticamente a conexão do banco de dados escravo para o mestre. Funciona da mesma forma com bancos de dados mestres: assim que você trabalha com uma tabela relacionada a check-out, o sistema redireciona todas as consultas para um banco de dados específico. Enquanto isso, todas as consultas relacionadas ao catálogo irão para o banco de dados principal.

Para obter mais detalhes sobre a configuração e os benefícios de várias configurações mestre/escravo, consulte
[Solução de desempenho de banco de dados dividido](../configuration/storage/multi-master.md).

## Veicular conteúdo de mídia

O Magento não fornece nenhuma integração específica para veicular e fornecer conteúdo de mídia. Todas as abordagens comuns podem ser usadas juntas no Magento.

A maneira mais fácil de veicular conteúdo de mídia é entregar e armazenar em cache em um [!DNL Varnish] servidor. Essa abordagem pressupõe um sistema de arquivos compartilhado para armazenamento de conteúdo de mídia ou um servidor dedicado apontando para [!DNL Varnish].

Para ambientes de carga média e alta, recomendamos usar serviços de Rede de entrega de conteúdo (CDN) como Fastly, Akamai e outros. Ao trabalhar com esses serviços, [!DNL Commerce] O usa a abordagem pull clássica para atualizações de conteúdo. Você deve configurar [!DNL Commerce] URLs para trabalhar com o serviço CDN correspondente. Ao mover conteúdo de mídia para um CDN, você diminuirá significativamente a carga em suas instâncias.

## Configurar armazenamento de log

O armazenamento de registros e sua influência em outras operações de disco afeta a disponibilidade dos nós da Web, especialmente em situações de alta carga. Recomendamos que você minimize o registro, se não precisar. Você também pode configurar o registro para que ele seja gravado em um sistema de armazenamento separado que tenha altas velocidades de acesso. Observe que qualquer gargalo no acesso ao armazenamento de log pode afetar diretamente o processamento de solicitações recebidas que registram operações de gravação ou leitura como parte de seu fluxo.
