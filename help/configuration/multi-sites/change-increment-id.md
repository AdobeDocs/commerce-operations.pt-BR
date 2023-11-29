---
title: Alterar ID de incremento
description: Alterar a ID de incremento de uma entidade de banco de dados do Commerce.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Alterar ID de incremento

Este artigo discute como alterar a ID de incremento de uma entidade de banco de dados (BD) do Commerce (pedido, fatura, aviso de crédito etc.) em uma loja específica do Commerce usando o `ALTER TABLE` Instrução SQL.

## Versões afetadas

- Adobe Commerce (no local): 2.x.x
- Infraestrutura do Adobe Commerce na nuvem: 2.x.x
- MySQL: [qualquer versão compatível](../../installation/prerequisites/database/mysql.md)

## Quando você precisaria alterar a ID de incremento?

Talvez seja necessário alterar a ID de incremento para novas entidades de BD nestes casos:

- Após uma restauração de backup rígido em um site ativo
- Alguns registros de pedidos foram perdidos, mas suas IDs já estão sendo usadas por gateways de pagamento (como PayPal) para sua conta de Comerciante atual. Sendo assim, os gateways de pagamento param de processar novos pedidos que têm as mesmas IDs, retornando o erro &quot;ID de fatura duplicada&quot;

>[!INFO]
>
>Você também pode corrigir o problema do gateway de pagamento para PayPal, permitindo vários pagamentos por ID de fatura nas Preferências de Recebimento de Pagamento do PayPal. Consulte [Solicitação rejeitada do gateway do PayPal - problema de fatura duplicado](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) no _Knowledge base_.

## Etapas de pré-requisito

1. Localize lojas e entidades para as quais a nova ID de incremento deve ser alterada.
1. Conecte-se ao banco de dados MySQL.
Para o Adobe Commerce na infraestrutura em nuvem, no início, é necessário se conectar usando SSH ao seu ambiente.
1. Verificar o atual `auto_increment` para a tabela de sequência de entidades usando a seguinte query:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Se você estiver verificando um incremento automático para um pedido no armazenamento com ID=1, o nome da tabela será &#39;sequence_order_1&#39;.

Se o valor de `auto_increment` é &#39;1234&#39;, o próximo pedido feito na loja com `ID=1` terá a ID &#39;#100001234&#39;.

## Atualizar entidade para alterar ID de incremento

Atualize a entidade usando a seguinte consulta:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Importante: o novo valor de incremento deve ser maior que o atual.

Após executar a seguinte query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

O próximo pedido feito na loja com `ID=1` terá a ID &#39;#100002000&#39;.

## Etapas adicionais recomendadas para ambientes de produção em nuvem

Antes de executar o `ALTER TABLE` em um ambiente de produção do Adobe Commerce na infraestrutura em nuvem, recomendamos executar estas etapas:

- Teste todo o procedimento de alteração da ID de incremento no ambiente de preparo
- [Criar um backup de BD] para restaurar seu BD de produção em caso de falha

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[Criar um backup de BD]: https://support.magento.com/hc/en-us/articles/360003254334
[qualquer versão compatível]
