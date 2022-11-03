---
title: Prática recomendada para a configuração de relatórios
description: Otimize o desempenho do site removendo o módulo de relatórios se você não estiver usando.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Prática recomendada para a configuração do relatório

Se sua empresa não exigir a funcionalidade de segmentos dinâmicos ou de relatórios de clientes, desative a [Funcionalidade de relatórios](https://docs.magento.com/user-guide/configuration/general/reports.html) para melhorar o desempenho da loja.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Desativar relatórios

Caso não use os Relatórios ou os segmentos dinâmicos do cliente, desative a funcionalidade Relatórios .

1. Em Admin, navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Relatórios**.
1. Em **Opções gerais**, definir **Ativar relatórios** para *Não*.
1. Liberar cache executando `php bin/magento cache:flush` ou no Administrador em **Sistema** > **Ferramentas** > **Gerenciamento de cache**.

## Informações adicionais

- [Gerar relatórios no Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmentos dinâmicos do cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
