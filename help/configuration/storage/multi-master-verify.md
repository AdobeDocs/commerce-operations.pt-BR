---
title: Verificar banco de dados dividido
description: Saiba como verificar se uma configuração de banco de dados dividido do Commerce está funcionando corretamente.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verificar banco de dados dividido

{{ee-only}}

{{deprecate-split-db}}

Após a configuração, os bancos de dados mestres são configurados da seguinte maneira:

- Banco de dados principal do Commerce: 369 tabelas
- Banco de dados de cotação do Commerce: 11 tabelas
- Banco de dados de vendas do Commerce: 55 tabelas

Para verificar se os bancos de dados divididos estão funcionando corretamente, execute as tarefas a seguir e verifique se os dados foram adicionados às tabelas do banco de dados usando uma ferramenta de banco de dados como [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| O que verificar | Como verificar |
| -------------- | ------------- |
| o banco de dados de cotação está funcionando | Adicionar itens ao carrinho. Verifique se linhas foram adicionadas ao banco de dados de cotações `quote`, `quote_address`, e `quote_item` tabelas. |
| o banco de dados de vendas está funcionando | Concluir um pedido (qualquer método de pagamento, incluindo cheque/ordem de pagamento). Verifique se linhas foram adicionadas ao banco de dados de vendas `sales_order_address`, `sales_order_item`, e `sales_order_payment` tabelas. |

>[!WARNING]
>
>Você deve fazer backup das duas instâncias adicionais do banco de dados manualmente. O Commerce faz backup somente da instância do banco de dados principal. A variável [`magento setup:backup --db`](../../installation/tutorials/backup.md) O comando e as opções de Admin não fazem backup das tabelas adicionais.
