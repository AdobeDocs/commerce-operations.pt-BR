---
title: Práticas recomendadas de migração de dados
description: Siga estas práticas recomendadas de migração de dados para garantir um upgrade bem-sucedido do Magento 1 para o Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Práticas recomendadas de migração de dados

Esta seção fornece as melhores recomendações para acelerar e simplificar a migração e orientações sobre quanto tempo pode levar.

* **Usar uma cópia do banco de dados de uma instância do Magento 1** ao executar testes de migração. Não use a instância de produção do banco de dados de armazenamento do Magento 1.

* **Remover dados desatualizados e redundantes** do banco de dados Magento 1 antes da migração.

Esses dados podem incluir logs, cotações de pedidos, produtos visualizados ou comparados recentemente, visitantes, categorias específicas do evento e regras promocionais.

* **Siga as [regras gerais para uma migração bem-sucedida](migrate-data/overview.md#migration-overview)**.

* Para aumentar o desempenho, **habilitar o `direct_document_copy` opção** no seu `config.xml` arquivo:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Os bancos de dados Magento 1 e Magento 2 devem estar localizados no mesmo servidor MySQL e a conta do banco de dados deve ter acesso a ambos os bancos de dados.

## Estimativas de avaliação comparativa

O Adobe testou a migração de dados no seguinte sistema:

* Virtual Box VM, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo, 2,6 GHz
* Banco de dados com 177.000 produtos, 355.000 pedidos e 214.000 clientes

## Resultados de desempenho

* Tempo de migração das configurações: ~10 minutos
* Tempo de migração de dados: ~9 horas (todos os dados, exceto regravações de URL, ~85% do total de dados)
* Estimativa de tempo de inatividade do site: alguns minutos para reindexar e alterar as configurações de DNS. Tempo adicional necessário para aquecer o cache da página.
