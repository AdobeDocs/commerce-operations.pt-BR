---
title: Solução de desempenho de banco de dados dividida
description: Leia sobre a solução de banco de dados dividido para Adobe Commerce e Magento Open Source.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# Visão geral da solução de banco de dados dividida

{#ee-only}

{{deprecate-split-db}}

A Adobe Commerce oferece várias vantagens de escalabilidade, incluindo a capacidade de usar três bancos de dados principais separados para diferentes áreas funcionais do aplicativo Commerce.

Check-out, pedidos e dados de produto podem usar cada um um um banco de dados principal separado que você pode replicar opcionalmente. Essa separação dimensiona independentemente o carregamento de check-outs de sites, atividades de gerenciamento de pedidos, navegação em sites e atividades de merchandising, dependendo de suas necessidades. Essas alterações oferecem flexibilidade considerável na maneira como o nível do banco de dados pode ser dimensionado.

>[!INFO]
>
>A infraestrutura em nuvem da Adobe Commerce _not_ oferecem suporte a esse recurso.

O `ResourceConnections` fornece a conexão unificada do banco de dados MySQL para o aplicativo Commerce. Para consultas aos bancos de dados principais, implementamos o padrão de banco de dados CQRS (Command Query Responsibility Segregation). Este padrão lida com a lógica de roteamento das consultas de leitura e gravação para os bancos de dados apropriados. Os desenvolvedores não precisam saber qual configuração está sendo usada e não há conexões separadas de banco de dados de leitura e gravação.

Se você configurar a replicação opcional do banco de dados, você terá as seguintes vantagens:

- Backup de dados
- Análise de dados sem afetar o banco de dados principal
- Escalabilidade

Os bancos de dados MySQL são replicados de forma assíncrona, o que significa que os escravos não precisam ser conectados permanentemente para receber atualizações do principal.

A figura a seguir mostra como esse recurso funciona.

![O Adobe Commerce usa bancos de dados diferentes para armazenar tabelas](../../assets/configuration/split-db-diagram-ee.png)

No Magento Open Source, somente um banco de dados principal é usado.

O Adobe Commerce usa três bancos de dados principais e um número configurável de bancos de dados escravos para replicação. O Adobe Commerce tem uma única interface para conexões de banco de dados, resultando em desempenho mais rápido e melhor escalabilidade.

## Opções de configuração

Devido ao modo como a solução de desempenho de banco de dados dividido foi criada, seu código personalizado e os componentes instalados _cannot_ siga um destes procedimentos:

- Gravar diretamente no banco de dados (em vez disso, você deve usar a interface do banco de dados do Adobe Commerce)
- Use JOINs que afetam as vendas ou [citação](https://glossary.magento.com/quote) bancos de dados
- Usar chaves estrangeiras para tabelas no check-out, vendas ou bancos de dados principais

>[!WARNING]
>
>Entre em contato com desenvolvedores de componentes para verificar se seus componentes fazem alguma das ações anteriores. Em caso positivo, é necessário escolher apenas um dos seguintes:
>
>- Solicite aos desenvolvedores de componentes que atualizem seus componentes.
>- Usar os componentes como estão _without_ a solução de banco de dados dividido.
>- Remova os componentes para usar a solução de banco de dados dividido.


Isso também significa que é possível:

- Configurar a solução de banco de dados dividida _before_ Colocando o Commerce em produção.

   O Adobe recomenda configurar bancos de dados divididos assim que possível após instalar o software Commerce.

- [Configurar manualmente](multi-master-manual.md) a solução de banco de dados dividido.

   Você deve executar essa tarefa se já tiver instalado componentes ou se o Commerce já estiver em produção. (_Não_ Atualizar um sistema de produção; faça as atualizações em um sistema de desenvolvimento e sincronize as alterações depois de testá-las.)

   >[!WARNING]
   >
   >Você deve fazer o backup das duas instâncias de banco de dados adicionais manualmente. O Commerce faz o backup apenas da instância do banco de dados principal. O [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) As opções de comando e de Administrador não fazem backup das tabelas adicionais.

## Pré-requisitos

O banco de dados dividido requer que você configure três bancos de dados principais do MySQL em qualquer host (todos os três no servidor do Commerce, cada banco de dados em um servidor separado e assim por diante). Estas são as _principal_ bancos de dados e são usados da seguinte maneira:

- Um banco de dados principal para [checkout](https://glossary.magento.com/checkout) tabelas
- Um banco de dados principal para tabelas de vendas (também conhecido como _Sistema de gerenciamento de pedidos_ ou _OMS_, tabelas)
- Um banco de dados principal para o restante das tabelas de aplicativos do Commerce 2

Além disso, você pode configurar, opcionalmente, qualquer número de _escravo_ bancos de dados que servem como balanceadores de carga e backups.

Este guia discute como configurar somente os bancos de dados principais. Fornecemos configurações e referências de exemplo para você configurar bancos de dados escravos, se desejar.

Neste guia, os três bancos de dados principais são nomeados como:

- `magento_quote`
- `magento_sales`
- `magento`

(É possível nomear os bancos de dados conforme desejar.)
