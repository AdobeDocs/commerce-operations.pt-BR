---
title: Como funciona a migração de dados
description: Saiba mais sobre o processo de migração de dados entre o Magento 1 e o Magento 2, incluindo terminologia, diagramas de fluxo de trabalho e etapas.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Como funciona a migração de dados

Este tópico fornece uma visão geral de alto nível de como os dados são migrados do Magento 1 para o Magento 2 usando o [!DNL Data Migration Tool].

A variável [!DNL Data Migration Tool] é uma ferramenta de interface de linha de comando (CLI) usada para transferir dados do Magento 1 para o Magento 2. A ferramenta verifica a consistência entre as estruturas de banco de dados do Magento 1 e 2 (tabelas e campos), rastreia o progresso da transferência de dados, cria registros e executa testes de verificação de dados.

## Terminologia

* **Modos** - um conjunto ordenado de operações para migrar dados do Magento 1.x para o Magento 2.x.
* **Etapas** - as tarefas em um modo que define os tipos de dados que serão migrados.
* **Estágios** - as tarefas na etapa que validam, transferem e verificam os dados.
* **Mapear arquivos** - Arquivos XML que definem as regras e conexões entre as estruturas de dados Magento 1.x e Magento 2.x para concluir os estágios.

## Modos

A variável [!DNL Data Migration Tool] divide o processo de migração em três fases ou *modos* para transferir e adaptar dados do Magento 1.x para o Magento 2.x. Os três modos estão listados aqui e devem ser executados nesta ordem:

1. **Modo de configurações**: migra a configuração do sistema e as configurações relacionadas ao site.
1. **Modo de dados**: migra ativos do banco de dados em massa.
1. **Modo Delta**: migra alterações incrementais (alterações desde a última execução), como novos clientes e pedidos.

![Modos de migração](../../assets/data-migration/MigrationModes2.png)

## Etapas

A variável [!DNL Data Migration Tool] usa uma lista de *etapas* em cada modo para migrar um tipo específico de dados. Por exemplo, no modo Configurações, há duas etapas usadas para migrar todos os dados de configurações: a etapa Lojas e a etapa Configurações. Detalhes sobre os dados específicos migrados em cada uma dessas etapas (e para etapas nos outros modos), podem ser encontrados na [[!DNL Data Migration Tool] Especificação técnica](technical-specification.md).

![Visão geral da migração](../../assets/data-migration/MigrationOverview2.png)

## Estágios

Em cada etapa há três *estágios* que são sempre executadas nessa ordem para garantir que os dados sejam migrados corretamente:

1. **Verificação de integridade**: compara os nomes de campos, tipos e outras informações da tabela para verificar a compatibilidade entre as estruturas de dados do Magento 1 e 2.
1. **Transferência de dados**: transfere a tabela de dados por tabela da Magento 1 e 2.
1. **Verificação do volume**: compara o número de registros entre tabelas para verificar se a transferência foi bem-sucedida.

![Estágios de migração](../../assets/data-migration/MigrationSteps2.png)

## Mapear arquivos

No nível mais baixo dos processos de migração estão os *mapear arquivos*. A variável [!DNL Data Migration Tool] O usa arquivos de mapa nos estágios de uma etapa para transformar diferentes estruturas de dados entre as tabelas Magento 1.x e 2.x.

Por exemplo, ao transformar dados de um banco de dados Magento Open Source 1.8.0.0 em Magento Open Source 2.x.x, o arquivo de mapa leva em conta o fato de que uma tabela foi renomeada e a renomeia adequadamente no banco de dados de destino. Se não houver diferenças na estrutura ou no formato dos dados, a variável [!DNL Data Migration Tool] transfere-o como está, incluindo dados de tabelas criadas por extensões, para o banco de dados Magento 2.

Quando as diferenças não forem declaradas nos arquivos de mapa, a variável [!DNL Data Migration Tool] O exibe um erro e não é iniciado.

Os arquivos de mapeamento são discutidos com mais detalhes no [[!DNL Data Migration Tool] Especificação técnica].

## Diagrama do fluxo de migração

![Fluxo de migração](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Especificação técnica](technical-specification.md)

Estamos satisfeitos por você estar considerando mudar da plataforma de comércio #1 do mundo — Magento 1.x — para a plataforma do futuro, Magento 2. Estamos felizes em compartilhar os detalhes desse processo, que chamamos de migração.

## Componentes de migração

A migração para o Magento 2 envolve quatro componentes: dados, extensões e código personalizado, temas e personalizações.

### Dados

Desenvolvemos o **MAGENTO 2[!DNL Data Migration Tool]** para ajudá-lo a mover com eficiência todos os seus produtos, clientes e dados de pedidos, configurações de loja, promoções e muito mais para o Magento 2. Este guia fornece informações sobre a ferramenta e as práticas recomendadas para usá-lo para migrar seus dados.

### Extensões e código personalizado

Estamos trabalhando duro com a comunidade de desenvolvimento para ajudá-lo a usar suas extensões Magento 1 no Magento 2. Agora estamos orgulhosos de apresentar o [Commerce Marketplace](https://marketplace.magento.com/), onde você pode baixar ou comprar as versões mais recentes de suas extensões favoritas.

Mais informações sobre o desenvolvimento de extensões para o Magento 2 estão disponíveis na [Guia do desenvolvedor do PHP](https://developer.adobe.com/commerce/php/development/).

### Temas e personalizações

O Magento 2 usa novas abordagens e tecnologias que dão aos comerciantes uma capacidade inigualável de criar experiências de compra inovadoras e escalar para novos níveis. Para aproveitar esses avanços, os desenvolvedores devem fazer alterações em seus temas e personalizações. A documentação está disponível online para criar o Magento 2 [temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), e [personalizações](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Esforços de migração

Assim como um upgrade entre versões 1.x (por exemplo, de v1.12 para v1.14), o nível de esforço para migrar do Magento 1 para o Magento 2 depende de como você criou seu site e seu nível de personalização.
No entanto, estamos constantemente melhorando a [!DNL Data Migration Tool] (consulte a [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para obter mais detalhes); portanto, os esforços de migração estão diminuindo continuamente.
