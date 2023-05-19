---
title: Uso de gatilhos MySQL
description: Saiba como usar acionadores MySQL com eficiência com o Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Práticas recomendadas para uso de acionadores do MySQL

Este artigo explica como evitar problemas de desempenho ao usar acionadores MySQL. Os acionadores são usados para registrar alterações em tabelas de auditoria.

## Produtos e versões afetados

- Adobe Commerce no local
- Adobe Commerce na infraestrutura em nuvem

>[!WARNING]
>
>Para Adobe Commerce em projetos na nuvem, sempre teste as alterações de configuração no ambiente de preparo antes de alterar a configuração para o ambiente de produção.

## Compreender os impactos no desempenho

Os acionadores são interpretados como código, significando que o MySQL não os pré-compila.

Ao conectar-se ao espaço de transação do query, os acionadores adicionam overhead a um analisador e interpretador para cada query executada com a tabela. Os acionadores compartilham o mesmo espaço de transação que as consultas originais e, enquanto essas consultas competem por bloqueios na tabela, os acionadores competem independentemente por bloqueios em outra tabela.

Essa sobrecarga adicional pode afetar negativamente o desempenho do site se muitos acionadores forem usados.

>[!WARNING]
>
>O Adobe Commerce não oferece suporte a acionadores personalizados no banco de dados do Adobe Commerce, pois esses acionadores podem introduzir incompatibilidades com versões futuras do Adobe Commerce. Para obter as práticas recomendadas, consulte [Diretrizes gerais do MySQL](../../../installation/prerequisites/database/mysql.md) na documentação do Adobe Commerce.

## Usar acionadores com eficiência

Para evitar problemas de desempenho ao usar acionadores, siga estas diretrizes:

- Se você tiver acionadores personalizados que gravam alguns dados quando o acionador é executado, mova essa lógica para gravar diretamente nas tabelas de auditoria. Por exemplo, adicionando uma consulta adicional no código do aplicativo, após a consulta, você pretendia criar o acionador para.
- Revise os acionadores personalizados existentes e considere removê-los e gravá-los diretamente nas tabelas do lado do aplicativo. Verifique os acionadores existentes no banco de dados usando o [`SHOW TRIGGERS` Instrução SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Para obter assistência, dúvidas ou dúvidas adicionais, [enviar um tíquete de suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Informações adicionais

- [Pré-requisitos do MySQL](../../../installation/prerequisites/database/mysql.md)
- [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
