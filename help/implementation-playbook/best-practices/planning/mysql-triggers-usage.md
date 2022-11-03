---
title: Uso de acionadores MySQL
description: Saiba como usar acionadores MySQL de maneira eficaz com o Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Práticas recomendadas para uso de acionadores MySQL

Este artigo explica como evitar problemas de desempenho ao usar acionadores MySQL. Os Triggers são usados para registrar alterações em tabelas de auditoria.

## Produtos e versões afetados

- Adobe Commerce no local
- Adobe Commerce na infraestrutura de nuvem

>[!WARNING]
>
>Para projetos em nuvem do Adobe Commerce, sempre teste as alterações de configuração no ambiente de preparo antes de alterar a configuração do ambiente de produção.

## Entender os impactos no desempenho

Os Acionadores são interpretados como um código, o que significa que o MySQL não os pré-compila.

Ao entrar no espaço de transação do query, os acionadores adicionam sobrecarga a um analisador e interpretador para cada query executada com a tabela. Os acionadores compartilham o mesmo espaço de transações que as consultas originais e, enquanto essas consultas competem por bloqueios na tabela, os acionadores competem independentemente por bloqueios em outra tabela.

Essa sobrecarga adicional pode afetar negativamente o desempenho do site se vários acionadores forem usados.

>[!WARNING]
>
>O Adobe Commerce não é compatível com acionadores personalizados no banco de dados do Adobe Commerce porque os acionadores personalizados podem introduzir incompatibilidades com versões futuras do Adobe Commerce. Para obter as práticas recomendadas, consulte [Diretrizes gerais do MySQL](../../../installation/prerequisites/database/mysql.md) na documentação do Adobe Commerce.

## Usar acionadores com eficiência

Para evitar problemas de desempenho ao usar acionadores, siga estas diretrizes:

- Se você tiver acionadores personalizados que gravam alguns dados quando o acionador é executado, mova essa lógica para gravar diretamente nas tabelas de auditoria. Por exemplo, ao adicionar uma query adicional no código do aplicativo, após a query, você quis criar o acionador para.
- Analise os acionadores personalizados existentes e considere removê-los e escrever diretamente nas tabelas do lado do aplicativo. Verifique se há acionadores no seu banco de dados usando o [`SHOW TRIGGERS` Instrução SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Para obter assistência, perguntas ou preocupações adicionais, [enviar um tíquete de suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Informações adicionais

- [Pré-requisitos do MySQL](../../../installation/prerequisites/database/mysql.md)
- [Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
