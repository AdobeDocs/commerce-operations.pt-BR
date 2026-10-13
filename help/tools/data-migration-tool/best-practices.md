---
title: Práticas recomendadas de migração de dados
description: Siga estas práticas recomendadas de migração de dados para garantir uma atualização bem-sucedida da Magento 1 para a Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Práticas recomendadas de migração de dados

Esta seção fornece as melhores recomendações para acelerar e simplificar a migração e orientações sobre quanto tempo pode levar.

* **Usar uma cópia do banco de dados de uma instância da Magento 1** ao executar o teste de migração. Não use a instância de produção do banco de dados da loja da Magento 1.

* **Remova dados desatualizados e redundantes** do banco de dados Magento 1 antes da migração.

Esses dados podem incluir logs, cotações de pedidos, produtos visualizados ou comparados recentemente, visitantes, categorias específicas do evento e regras promocionais.

* **Siga as [regras gerais para uma migração bem-sucedida](migrate-data/overview.md#migration-overview)**.

* Para melhorar o desempenho, **habilite a opção `direct_document_copy`** no arquivo `config.xml`:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Os bancos de dados Magento 1 e Magento 2 devem estar localizados no mesmo servidor MySQL e a conta do banco de dados deve ter acesso a ambos os bancos de dados.

## Estimativas de avaliação comparativa

A Adobe testou a migração de dados no seguinte sistema:

* Virtual Box VM, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo, 2,6 GHz
* Banco de dados com 177.000 produtos, 355.000 pedidos e 214.000 clientes

## Resultados de desempenho

* Tempo de migração das configurações: ~10 minutos
* Tempo de migração de dados: ~9 horas (todos os dados, exceto regravações de URL, ~85% do total de dados)
* Estimativa de tempo de inatividade do site: alguns minutos para reindexar e alterar as configurações de DNS. Tempo adicional necessário para aquecer o cache da página.
