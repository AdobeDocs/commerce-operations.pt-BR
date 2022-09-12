---
title: Verificar banco de dados dividido
description: Saiba como verificar se uma configuração de banco de dados Split do Commerce está funcionando corretamente.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Verificar banco de dados dividido

{{ee-only}}

{{deprecate-split-db}}

Após a configuração, os bancos de dados principais são configurados da seguinte maneira:

- Banco de dados do Comércio principal: 369 tabelas
- Comércio [citação](https://glossary.magento.com/quote) banco de dados: 11 tabelas
- Banco de dados de vendas de comércio: 55 tabelas

Para verificar se os bancos de dados divididos estão funcionando corretamente, execute as seguintes tarefas e verifique se os dados são adicionados às tabelas do banco de dados usando uma ferramenta de banco de dados como [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| O que verificar | Como verificar |
| -------------- | ------------- |
| banco de dados de cotação está funcionando | Adicionar itens ao carrinho. Verifique se linhas foram adicionadas ao banco de dados de cotação `quote`, `quote_address`e `quote_item` tabelas. |
| o banco de dados de vendas está funcionando | Preencher uma ordem (qualquer método de pagamento, incluindo cheque/ordem de pagamento). Verifique se linhas foram adicionadas ao banco de dados de vendas `sales_order_address`, `sales_order_item`e `sales_order_payment` tabelas. |

>[!WARNING]
>
>Você deve fazer o backup das duas instâncias de banco de dados adicionais manualmente. O Commerce faz o backup apenas da instância do banco de dados principal. O [`magento setup:backup --db`](../../installation/tutorials/backup.md) As opções de comando e de Administrador não fazem backup das tabelas adicionais.
