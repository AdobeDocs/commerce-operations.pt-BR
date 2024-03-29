---
title: Práticas recomendadas para modificar tabelas de banco de dados
description: Saiba como e quando modificar tabelas de banco de dados do Adobe Commerce e de terceiros.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Práticas recomendadas para modificar tabelas de banco de dados

Este artigo fornece práticas recomendadas para modificar tabelas de banco de dados criadas por [!DNL Adobe Commerce] ou módulos de terceiros. Entender quando e como modificar tabelas com eficiência ajuda a garantir a viabilidade e a estabilidade a longo prazo de sua plataforma de comércio.

Migrando de [!DNL Magento 1] e outras plataformas de comércio eletrônico, ou trabalhar com módulos da [!DNL Adobe Commerce] Marketplace, pode exigir a adição e o salvamento de dados extras. Seu primeiro instinto pode ser adicionar uma coluna a uma tabela de banco de dados ou ajustar uma existente. No entanto, você só deve modificar um núcleo [!DNL Adobe Commerce] tabela (ou tabela de fornecedores de terceiros) em situações limitadas.

## Por que o Adobe recomenda evitar modificações

O principal motivo para evitar a modificação das tabelas principais é que o Adobe Commerce inclui uma lógica subjacente que contém consultas SQL brutas. As alterações na estrutura da tabela podem causar efeitos colaterais inesperados, que são difíceis de solucionar. A alteração também pode afetar as operações de DDL (Data Definition Language), causando impactos inesperados e imprevisíveis no desempenho.

Outro motivo para evitar a alteração da estrutura da tabela de banco de dados é que suas alterações podem causar problemas se a equipe principal de desenvolvimento ou desenvolvedores de terceiros alterarem a estrutura de suas tabelas de banco de dados. Por exemplo, há algumas tabelas do banco de dados principal que têm uma coluna chamada `additional_data`. Este tem sido sempre um `text` tipo de coluna. No entanto, por motivos de desempenho, a equipe principal pode alterar a coluna para `longtext`. Esse tipo de coluna é um alias para JSON. Ao converter para esse tipo de coluna, há ganhos de desempenho e capacidade de pesquisa adicionados a essa coluna, que não existe como um `text` tipo. Você pode ler mais sobre este tópico em [Tipo de dados JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Saber quando salvar ou remover dados

A Adobe recomenda que você determine primeiro se precisa salvar esses dados. Se você estiver movendo dados de um sistema herdado, os dados que você puder remover economizarão tempo e esforço durante a migração. (Há maneiras de arquivar dados se eles precisarem ser acessados posteriormente.) Para ser um bom administrador do aplicativo e do desempenho, não há problema em desafiar uma solicitação para salvar dados adicionais. Seu objetivo é garantir que salvar os dados seja um requisito para atender a uma necessidade comercial que não pode ser atendida de outra maneira.

### Dados herdados

Se o seu projeto contiver dados herdados, como pedidos antigos ou registros de clientes, considere um método de pesquisa alternativo. Por exemplo, se a empresa exigir acesso aos dados apenas para referência ocasional, considere implementar uma pesquisa externa do banco de dados antigo hospedado fora da plataforma de comércio em vez de migrar dados antigos para [!DNL Adobe Commerce].

Essa situação exigiria que o banco de dados fosse migrado para um servidor, oferecendo uma interface da Web para ler os dados ou talvez treinamento no uso do MySQL Workbench ou de ferramentas semelhantes. A exclusão desses dados do novo banco de dados agiliza a migração permitindo que a equipe de desenvolvimento se concentre no novo site em vez de solucionar problemas de migração de dados.

Outra opção relacionada para manter os dados externos para o comércio, mas permitir que você os use em tempo real, seria aproveitar outras ferramentas, como o GraphQL mesh. Essa opção combina diferentes fontes de dados e as retorna como uma única resposta.

Por exemplo, você pode `stitch` junto pedidos antigos de um banco de dados externo, talvez o antigo site Magento 1 que está desativado. Em seguida, usando a malha do GraphQL, mostre-as como parte do histórico de pedidos dos clientes. Esses pedidos antigos podem ser combinados com os pedidos do seu [!DNL Adobe Commerce] ambiente.

Para obter mais informações sobre como usar a malha de API com o GraphQL, consulte [O que é a API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrar dados herdados com atributos de extensão

Se você determinar que os dados herdados exigem migração ou que os novos dados precisam ser salvos em [!DNL Adobe Commerce], o Adobe recomenda usar [atributos de extensão](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. A utilização de atributos de extensão para salvar dados adicionais oferece as seguintes vantagens:

- Você pode controlar os dados que estão sendo mantidos e a estrutura do banco de dados, o que garante que os dados sejam salvos com o tipo de coluna correto e índices adequados.
- Maioria das entidades em [!DNL Adobe Commerce] e [!DNL Magento Open Source] oferecem suporte ao uso de atributos de extensão.
- Os atributos de extensão são um mecanismo agnóstico em armazenamento que oferece flexibilidade para salvar os dados no local ideal para o seu projeto.

Dois exemplos de locais de armazenamento são tabelas de banco de dados e [!DNL Redis]. Os principais aspectos a serem considerados ao escolher um local são se o local apresenta complexidade extra ou se afeta o desempenho.

### Considere outras alternativas

Como desenvolvedor, é vital sempre considerar o uso de ferramentas fora do [!DNL Adobe Commerce] como o GraphQL mesh e o Adobe App Builder. Essas ferramentas podem ajudar você a reter o acesso aos dados, mas não têm impacto no aplicativo principal de comércio ou em suas tabelas de banco de dados subjacentes. Com essa abordagem, você expõe seus dados por meio de uma API. Em seguida, você adiciona uma fonte de dados à configuração do App Builder. Com o GraphQL Mesh, é possível combinar essas fontes de dados e produzir uma única resposta, conforme mencionado na [dados herdados](#legacy-data).

Para obter detalhes adicionais sobre a malha GraphQL, consulte [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Modificação de uma tabela principal ou de terceiros

Se você decidir armazenar dados modificando um [!DNL Adobe Commerce] ou tabela de banco de dados de módulo de terceiros, use as seguintes diretrizes para minimizar o impacto na estabilidade e no desempenho.

- Adicionar somente novas colunas.
- Nunca modifique o _type_ valor de uma coluna existente. Por exemplo, não altere uma `integer` para um `varchar` para atender ao seu caso de uso exclusivo.
- Evite adicionar colunas às tabelas de atributos EAV. Essas tabelas já estão sobrecarregadas de lógica e responsabilidade.
- Antes de ajustar uma tabela, determine seu tamanho. A alteração de tabelas grandes afeta a implantação, o que pode causar minutos ou horas de atraso quando as alterações são aplicadas.

## Práticas recomendadas para modificar uma tabela de banco de dados externa

O Adobe recomenda seguir estas etapas quando você adiciona uma coluna a uma tabela do banco de dados principal ou a uma tabela de terceiros:

1. Crie um módulo com um nome no namespace que represente o que você está atualizando.

   Por exemplo: `app/code/YourCompany/Customer`

1. Crie os arquivos apropriados para habilitar o módulo (consulte [Criar um módulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Crie um arquivo chamado `db_schema.xml` no `etc` e faça as alterações apropriadas.

   Se aplicável, gere um `db_schema_whitelist.json` arquivo. Consulte [Esquema Declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} para obter mais informações.

### Impactos potenciais

Adicionar uma coluna a um banco de dados externo pode afetar seu projeto do Adobe Commerce das seguintes maneiras:

- As atualizações podem ser mais complicadas.
- As implantações serão afetadas se a tabela que está sendo modificada for grande.
- As migrações para uma nova plataforma podem ser mais complicadas.

## Maneiras de evitar a modificação das tabelas principais

Você pode evitar modificar tabelas de banco de dados do Adobe Commerce usando [atributos de extensão](#migrate-legacy-data-with-extension-attributes). Outra alternativa é usar uma coluna especial (`additional_data`) encontrado em algumas tabelas principais para armazenar dados e salvá-los no formato codificado em JSON.

### Salvar dados em uma coluna de dados codificada em JSON

Algumas tabelas principais têm um `additional_data` coluna que contém dados codificados em JSON. Essa coluna oferece uma maneira nativa de mapear dados adicionais em um campo. O uso desse método evita a adição de uma tabela para elementos de dados pequenos e simples que armazenam informações para recuperação de dados sem um requisito de pesquisa. A variável `additional_data` normalmente, a coluna está disponível somente no nível do item, não para toda a cota ou pedido.

- Vantagens de usar o `additional_data` campo

   - Nenhum campo adicional é necessário, o que mantém o número de colunas mínimo. Isso é útil no fluxo de vendas, em que já há muitas tabelas envolvidas. É melhor não adicionar mais complexidade a esse processo já complicado. Este método satisfaz muitos casos de uso, mas não todos.

- Desvantagens

   - Esse método é ideal apenas para armazenar dados somente leitura. Esse problema ocorre porque nosso código precisaria ter sua serialização cancelada para modificar e criar o objeto para adicionar dependências ou relações de banco de dados.

   - É difícil usar operações de banco de dados para procurar por esses campos. A pesquisa com esse método está lenta.

   - Tenha muito cuidado ao armazenar dados na `additional_data` para evitar o acionamento de operações de serialização ou desserialização que poderiam quebrar o código criando um JSON inválido ou causando erros de leitura durante o tempo de execução.

   - Esses campos devem ser claramente declarados no código, para que um desenvolvedor possa encontrá-los facilmente.

   - Outros problemas que podem ocorrer e que podem ser muito difíceis de diagnosticar. Por exemplo, com algumas funções nativas do PHP se você não usar [!DNL Adobe Commerce] métodos wrapper fornecidos pelo aplicativo principal, o resultado final dos dados transformados pode ser diferente do formato esperado. Sempre use as funções do invólucro para garantir a consistência e a previsibilidade dos dados que estão sendo salvos ou recuperados.

Estes são exemplos de tabelas que têm a coluna e a estrutura para a variável `additional_data` coluna.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

Nas versões 2.4.3, 2.4.4 e 2.4.5, há dez tabelas com a coluna `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
