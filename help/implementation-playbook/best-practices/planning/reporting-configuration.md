---
title: Prática recomendada para a configuração de relatórios
description: Otimize o desempenho do site removendo o módulo de relatórios se não estiver sendo usado.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Prática recomendada para a configuração de relatórios

Se a sua empresa não requer a funcionalidade de relatórios ou segmentos dinâmicos de clientes, desabilite a [funcionalidade de relatórios](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) para melhorar o desempenho do armazenamento.

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Desativar relatórios

Se você não usar os Relatórios ou segmentos dinâmicos de clientes, desative a funcionalidade Relatórios.

1. No Administrador, navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Relatórios**.
1. Em **Opções Gerais**, defina **Habilitar Relatórios** como *Não*.
1. Liberar cache executando `php bin/magento cache:flush` ou no Administrador em **Sistema** > **Ferramentas** > **Gerenciamento de Cache**.

## Informações adicionais

- [Gerar relatórios no Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [Segmentos dinâmicos do cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
