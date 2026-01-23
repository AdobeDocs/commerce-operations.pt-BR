---
title: Como funciona a migração de dados
description: Saiba mais sobre o processo de migração de dados entre o Magento 1 e o Magento 2, incluindo terminologia, diagramas de fluxo de trabalho e etapas.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Como funciona a migração de dados

Este tópico fornece uma visão geral de alto nível de como os dados são migrados do Magento 1 para o Magento 2 usando o [!DNL Data Migration Tool].

O [!DNL Data Migration Tool] é uma ferramenta de interface de linha de comando (CLI) usada para transferir dados do Magento 1 para o Magento 2. A ferramenta verifica a consistência entre as estruturas de banco de dados do Magento 1 e 2 (tabelas e campos), rastreia o progresso da transferência de dados, cria registros e executa testes de verificação de dados.

## Terminologia

* **Modos** - um conjunto ordenado de operações para migrar dados do Magento 1.x para o Magento 2.x.
* **Etapas** - as tarefas em um modo que define os tipos de dados a serem migrados.
* **Estágios** - as tarefas na etapa que validam, transferem e verificam os dados.
* **Arquivos de mapa** - Arquivos XML que definem as regras e as conexões entre as estruturas de dados do Magento 1.x e do Magento 2.x para concluir os estágios.

## Modos

O [!DNL Data Migration Tool] divide o processo de migração em três fases ou *modos* para transferir e adaptar dados do Magento 1.x para o Magento 2.x. Os três modos estão listados aqui e devem ser executados nesta ordem:

1. **Modo de Configurações**: migra as configurações do sistema e as configurações relacionadas ao site.
1. **Modo de Dados**: migra ativos do banco de dados em massa.
1. **Modo Delta**: migra alterações incrementais (alterações desde a última execução), como novos clientes e pedidos.

![Modos de Migração](../../assets/data-migration/MigrationModes2.png)

## Etapas

O [!DNL Data Migration Tool] usa uma lista de *etapas* em cada modo para migrar um tipo específico de dados. Por exemplo, no modo Configurações, há duas etapas usadas para migrar todos os dados de configurações: a etapa Lojas e a etapa Configurações. Detalhes sobre os dados específicos migrados em cada uma dessas etapas (e para etapas nos outros modos) podem ser encontrados na [[!DNL Data Migration Tool] Especificação técnica](technical-specification.md).

![Visão geral da migração](../../assets/data-migration/MigrationOverview2.png)

## Estágios

Em cada etapa há três *estágios* que são sempre executados nesta ordem para garantir que os dados sejam migrados corretamente:

1. **Verificação de Integridade**: compara os nomes, tipos e outras informações dos campos da tabela para verificar a compatibilidade entre as estruturas de dados do Magento 1 e 2.
1. **Transferência de Dados**: Transfere a tabela de dados por tabela do Magento 1 e 2.
1. **Verificação de Volume**: compara o número de registros entre tabelas para verificar se a transferência foi bem-sucedida.

![Estágios de migração](../../assets/data-migration/MigrationSteps2.png)

## Mapear arquivos

No nível mais baixo dos processos de migração estão os *arquivos de mapa* XML. O [!DNL Data Migration Tool] usa arquivos de mapa nos estágios de uma etapa para transformar diferentes estruturas de dados entre as tabelas do Magento 1.x e 2.x.

Por exemplo, ao transformar dados de um banco de dados do Magento Open Source 1.8.0.0 em Magento Open Source 2.x.x, o arquivo de mapa considera o fato de uma tabela ter sido renomeada e a renomeia adequadamente no banco de dados de destino. Se não houver diferenças na estrutura ou no formato dos dados, o [!DNL Data Migration Tool] os transferirá como estão, incluindo dados de tabelas criadas por extensões, para o banco de dados do Magento 2.

Quando diferenças não são declaradas nos arquivos de mapa, o [!DNL Data Migration Tool] exibe um erro e não inicia.

Os arquivos de mapeamento são discutidos com mais detalhes na [[!DNL Data Migration Tool] Especificação Técnica].

## Diagrama do fluxo de migração

![Fluxo de migração](../../assets/data-migration/migration_flow.png)

[Especificação técnica [!DNL Data Migration Tool]](technical-specification.md)

Estamos satisfeitos por você estar considerando mudar da plataforma de comércio #1 do mundo — Magento 1.x — para a plataforma do futuro, Magento 2. Estamos felizes em compartilhar os detalhes desse processo, que chamamos de migração.

## Componentes de migração

A migração para o Magento 2 envolve quatro componentes: dados, extensões e código personalizado, temas e personalizações.

### Dados

Desenvolvemos o **Magento 2[!DNL Data Migration Tool]** para ajudá-lo a mover com eficiência todos os seus produtos, clientes e dados de pedidos, configurações de loja, promoções e muito mais para o Magento 2. Este guia fornece informações sobre a ferramenta e as práticas recomendadas para usá-lo para migrar seus dados.

### Extensões e código personalizado

Trabalhamos muito com a comunidade de desenvolvimento para ajudar você a usar as extensões do Magento 1 no Magento 2. Agora temos o orgulho de apresentar a [Commerce Marketplace](https://commercemarketplace.adobe.com//), onde você pode baixar ou comprar as versões mais recentes das suas extensões favoritas.

Mais informações sobre o desenvolvimento de extensões para o Magento 2 estão disponíveis no [Guia do Desenvolvedor do PHP](https://developer.adobe.com/commerce/php/development/).

### Temas e personalizações

O Magento 2 usa novas abordagens e tecnologias que oferecem aos comerciantes uma capacidade inigualável de criar experiências de compra inovadoras e dimensionar para novos níveis. Para aproveitar esses avanços, os desenvolvedores devem fazer alterações em seus temas e personalizações. A documentação está disponível online para criação de [temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) e [personalizações](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) do Magento 2.

## Esforços de migração

Assim como uma atualização entre versões 1.x (por exemplo, da v1.12 para a v1.14), o nível de esforço para migrar do Magento 1 para o Magento 2 depende de como você criou seu site e seu nível de personalização.
No entanto, estamos constantemente aprimorando o [!DNL Data Migration Tool] (consulte o [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para obter mais detalhes); portanto, os esforços de migração estão diminuindo continuamente.
