---
title: Alterar ID de incremento
description: Altere a ID do incremento para uma entidade de banco de dados do Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Alterar ID de incremento

Este artigo discute como alterar a ID de incremento de uma entidade de banco de dados do Commerce (DB) (pedido, fatura, aviso de crédito etc.) em um armazenamento do Commerce específico usando a variável `ALTER TABLE` Instrução SQL.

## Versões afetadas

- Adobe Commerce (nas instalações): 2.x.x
- Adobe Commerce na infraestrutura de nuvem: 2.x.x
- MySQL: [qualquer versão compatível](../../installation/prerequisites/database/mysql.md)

## Quando é necessário alterar a ID de incremento

Nesses casos, pode ser necessário alterar a ID de incremento para novas entidades de banco de dados:

- Após uma restauração de backup rígido em um site Live
- Alguns registros de pedidos foram perdidos, mas suas IDs já estão sendo usadas por gateways de pagamento (como PayPal) para sua conta comercial atual. Sendo esse o caso, os gateways de pagamento param de processar novas ordens que tenham as mesmas IDs, retornando o erro &quot;ID de fatura duplicada&quot;

>[!INFO]
>
>Você também pode corrigir o problema do gateway de pagamento para PayPal permitindo vários pagamentos por ID de fatura nas Preferências de Recebimento de Pagamento do PayPal. Consulte [Solicitação rejeitada do gateway PayPal - problema de fatura duplicada] no _Base de dados de conhecimento_.

## Etapas de pré-requisito

1. Localize lojas e entidades para as quais a nova ID de incremento deve ser alterada.
1. Conecte-se ao seu banco de dados MySQL.
Para o Adobe Commerce na infraestrutura de nuvem, primeiro, é necessário se conectar usando o SSH ao seu ambiente.
1. Verifique a `auto_increment` para a tabela de sequência de entidade usando a seguinte query:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Se você estiver verificando um incremento automático para um pedido na loja com ID=1, o nome da tabela seria &#39;sequence_order_1&#39;.

Se o valor da variável `auto_increment` coluna é &#39;1234&#39;, o próximo pedido colocado na loja com `ID=1` terá o ID &#39;#100001234&#39;.

## Atualizar entidade para alterar a ID de incremento

Atualize a entidade usando a seguinte query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Importante: O novo valor de incremento deve ser maior que o atual.

Após executar a seguinte query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

O próximo pedido colocado na loja com `ID=1` terá o ID &#39;#100002000&#39;.

## Etapas adicionais recomendadas para ambientes de produção em nuvem

Antes de executar o `ALTER TABLE` Em um ambiente de produção do Adobe Commerce na infraestrutura de nuvem, recomendamos executar estas etapas:

- Teste todo o procedimento de alteração da ID de incremento em seu ambiente de preparo
- [Criar um backup de banco de dados] para restaurar seu banco de dados de produção em caso de falha

<!-- Link Definitions -->

[Solicitação rejeitada do gateway PayPal - problema de fatura duplicada]: https://support.magento.com/hc/en-us/articles/115002457473
[Criar um backup de banco de dados]: https://support.magento.com/hc/en-us/articles/360003254334
[qualquer versão compatível]
