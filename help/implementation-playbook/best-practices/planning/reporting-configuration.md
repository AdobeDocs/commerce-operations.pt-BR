---
title: Prática recomendada para a configuração de relatórios
description: Otimize o desempenho do site removendo o módulo de relatórios se não estiver sendo usado.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# Prática recomendada para a configuração de relatórios

Se a sua empresa não requer a funcionalidade de relatórios ou segmentos dinâmicos de clientes, desabilite a [funcionalidade de relatórios](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) para melhorar o desempenho do armazenamento.

## Produtos e versões afetados

[Todas as versões &#x200B;](../../../release/versions.md) com suporte de:

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
