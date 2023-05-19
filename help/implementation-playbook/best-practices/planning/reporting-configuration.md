---
title: Prática recomendada para a configuração de relatórios
description: Otimize o desempenho do site removendo o módulo de relatórios se não estiver sendo usado.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Prática recomendada para a configuração de relatórios

Se a sua empresa não exigir a funcionalidade de geração de relatórios ou segmentos dinâmicos de clientes, desative a opção [Funcionalidade de relatórios](https://docs.magento.com/user-guide/configuration/general/reports.html) para melhorar o desempenho da loja.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Desativar relatórios

Se você não usar os Relatórios ou segmentos dinâmicos de clientes, desative a funcionalidade Relatórios.

1. No Administrador, navegue até **Lojas** > **Configurações** > **Configuração** > **Geral** > **Relatórios**.
1. Em **Opções gerais**, definir **Ativar relatórios** para *Não*.
1. Liberar cache executando `php bin/magento cache:flush` ou no Administrador em **Sistema** > **Ferramentas** > **Gerenciamento de cache**.

## Informações adicionais

- [Gerar relatórios no Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmentos dinâmicos do cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
