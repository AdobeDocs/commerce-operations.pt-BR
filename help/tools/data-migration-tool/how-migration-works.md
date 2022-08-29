---
title: Como a migração de dados funciona
description: Saiba mais sobre o processo de migração de dados entre o Magento 1 e o Magento 2, incluindo terminologia, diagramas de fluxo de trabalho e etapas.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Como a migração de dados funciona

Este tópico fornece uma visão geral de alto nível de como os dados são migrados do Magento 1 para o Magento 2 usando o [!DNL Data Migration Tool].

O [!DNL Data Migration Tool] é uma ferramenta de interface de linha de comando (CLI) usada para transferir dados do Magento 1 para o Magento 2. A Ferramenta verifica a consistência entre as estruturas de banco de dados Magento 1 e 2 (tabelas e campos), rastreia o progresso da transferência de dados, cria logs e executa testes de verificação de dados.

## Terminologia

* **Modos** - um conjunto ordenado de operações para migrar dados do Magento 1.x para o Magento 2.x.
* **Etapas** - as tarefas em um modo que define os tipos de dados a serem migrados.
* **Estágios** - as tarefas na etapa que validam, transferem e verificam os dados.
* **Mapear arquivos** - Arquivos XML que definem as regras e as conexões entre as estruturas de dados Magento 1.x e Magento 2.x para a conclusão dos estágios.

## Modos

O [!DNL Data Migration Tool] divide o processo de migração em três fases ou *modos* para transferir e adaptar os dados do Magento 1.x para o Magento 2.x. Os três modos estão listados aqui e devem ser executados nesta ordem:

1. **Modo de Configurações**: migra a configuração do sistema e as configurações relacionadas ao site.
1. **Modo de dados**: migra ativos do banco de dados em massa.
1. **Modo Delta**: migra alterações incrementais (alterações desde a última execução), como novos clientes e pedidos.

![Modos de migração](../../assets/data-migration/MigrationModes2.png)

## Etapas

O [!DNL Data Migration Tool] usa uma lista de *etapas* em cada modo para migrar um tipo específico de dados. Por exemplo, no modo Configurações , há duas etapas usadas para migrar todos os dados de configurações: As etapas Lojas e Configurações . Os detalhes sobre os dados específicos que são migrados em cada uma dessas etapas (e para as etapas em outros modos) podem ser encontrados no [[!DNL Data Migration Tool] Especificação técnica](technical-specification.md).

![Visão geral da migração](../../assets/data-migration/MigrationOverview2.png)

## Estágios

Em cada etapa há três *etapas* que são sempre executadas nessa ordem para garantir que os dados sejam migrados corretamente:

1. **Verificação de integridade**: Compara os nomes, tipos e outras informações dos campos da tabela para verificar a compatibilidade entre as estruturas de dados Magento 1 e 2.
1. **Transferência de dados**: Transfere a tabela de dados por tabela da Magento 1 e 2.
1. **Verificação de volume**: Compara o número de registros entre tabelas para verificar se a transferência foi bem-sucedida.

![Etapas de migração](../../assets/data-migration/MigrationSteps2.png)

## Mapear arquivos

No nível mais baixo dos processos de migração, está o XML *mapear arquivos*. O [!DNL Data Migration Tool] O usa arquivos de mapa nos estágios de uma etapa para transformar diferentes estruturas de dados entre as tabelas Magento 1.x e 2.x.

Por exemplo, ao transformar dados de um banco de dados do Magento Open Source 1.8.0.0 para o Magento Open Source 2.x.x, o arquivo de mapa contabiliza o fato de que uma tabela foi renomeada e a renomeia de acordo no banco de dados de destino. Se não houver diferenças na estrutura de dados ou no formato de dados, a variável [!DNL Data Migration Tool] O transfere como está, incluindo dados de tabelas criadas por extensões, para o banco de dados do Magento 2.

Quando as diferenças não são declaradas nos arquivos de mapa, a variável [!DNL Data Migration Tool] exibe um erro e não inicia.

Os arquivos de mapeamento são discutidos com mais detalhes na [[!DNL Data Migration Tool] Especificação técnica].

## Diagrama do fluxo de migração

![Fluxo de migração](../../assets/data-migration/migration_flow.png)

<!-- Link definitions -->
[[!DNL Data Migration Tool] Especificação técnica]: technical-specified.md

[Migration Modes]: ../../assets/data-migration/MigrationModes2.png

[Migration Overview]: ../../assets/data-migration/MigrationOverview2.png

[Migration Steps]: ../../assets/data-migration/MigrationSteps2.png

Estamos satisfeitos por você estar considerando mudar da plataforma de comércio nº 1 do mundo — Magento 1.x — para a plataforma do futuro, Magento 2. Estamos animados em compartilhar os detalhes desse processo, que chamamos de migração.

## Componentes de migração

A migração do Magento 2 envolve quatro componentes: dados, extensões e código personalizado, temas e personalizações.

### Dados

Desenvolvemos o **Magento 2[!DNL Data Migration Tool]** para ajudá-lo a mover com eficiência todos os seus produtos, clientes e dados de pedidos, armazenar configurações, promoções e muito mais para o Magento 2. Este guia fornece informações sobre a ferramenta e as práticas recomendadas para usá-la para migrar seus dados.

### Extensões e código personalizado

Temos trabalhado bastante com a comunidade de desenvolvimento para ajudá-lo a usar suas extensões do Magento 1 no Magento 2. Agora estamos orgulhosos de apresentar a [Commerce Marketplace](https://marketplace.magento.com/), onde você pode baixar ou comprar as versões mais recentes de suas extensões favoritas.

Mais informações sobre o desenvolvimento de extensões para o Magento 2 estão disponíveis na seção [Guia do desenvolvedor do PHP](https://developer.adobe.com/commerce/php/development/).

### Temas e personalizações

O Magento 2 usa novas abordagens e tecnologias que oferecem aos comerciantes uma capacidade inigualável de criar experiências inovadoras de compras e dimensionar para novos níveis. Para aproveitar esses avanços, os desenvolvedores devem fazer alterações em seus temas e personalizações. A documentação está disponível online para criar o Magento 2 [temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layouts](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)e [personalizações](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Esforços de migração

Assim como uma atualização entre as versões 1.x (por exemplo, da v1.12 para v1.14), o nível de esforço para migrar do Magento 1 para o Magento 2 depende de como você criou o site e seu nível de personalização.
No entanto, estamos constantemente a melhorar a [!DNL Data Migration Tool] (consulte o [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para mais pormenores); assim, os esforços de migração estão continuamente diminuindo.
