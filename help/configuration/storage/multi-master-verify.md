---
title: Verificar banco de dados dividido
description: Saiba como verificar se uma configuração de banco de dados dividido do Commerce está funcionando corretamente.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Verificar banco de dados dividido

{{ee-only}}

{{deprecate-split-db}}

Após a configuração, os bancos de dados mestres são configurados da seguinte maneira:

- Banco de dados Commerce principal: 369 tabelas
- banco de dados Commerce quote: 11 tabelas
- Banco de dados de vendas do Commerce: 55 tabelas

Para verificar se os bancos de dados divididos estão funcionando corretamente, execute as tarefas a seguir e verifique se os dados foram adicionados às tabelas do banco de dados usando uma ferramenta de banco de dados como o [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| O que verificar | Como verificar |
| -------------- | ------------- |
| o banco de dados de cotação está funcionando | Adicionar itens ao carrinho. Verifique se linhas foram adicionadas às tabelas `quote`, `quote_address` e `quote_item` do banco de dados de cotações. |
| o banco de dados de vendas está funcionando | Concluir um pedido (qualquer método de pagamento, incluindo cheque/ordem de pagamento). Verifique se as linhas foram adicionadas às tabelas `sales_order_address`, `sales_order_item` e `sales_order_payment` do banco de dados de vendas. |

>[!WARNING]
>
>Você deve fazer backup das duas instâncias adicionais do banco de dados manualmente. O Commerce faz backup somente da instância do banco de dados principal. O comando [`magento setup:backup --db`](../../installation/tutorials/backup.md) e as opções de Admin não fazem backup das tabelas adicionais.
