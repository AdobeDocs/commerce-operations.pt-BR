---
title: Práticas recomendadas para migração de dados
description: Siga essas práticas recomendadas de migração de dados para garantir uma atualização bem-sucedida do Magento 1 para o Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Práticas recomendadas para migração de dados

Esta seção fornece as melhores recomendações para acelerar e simplificar sua migração e orientações sobre quanto tempo pode demorar.

* **Use uma cópia do banco de dados de uma instância do Magento 1** ao executar testes de migração. Não use a instância de produção do banco de dados de armazenamento do Magento 1.

* **Remover dados desatualizados e redundantes** do banco de dados do Magento 1 antes da migração.

Esses dados podem incluir registros, cotações de pedidos, produtos vistos ou comparados recentemente, visitantes, categorias específicas de eventos e regras promocionais.

* **Siga as [regras gerais para migração bem-sucedida](migrate-data/overview.md#migration-overview)**.

* Para melhorar o desempenho, **habilite o `direct_document_copy` opção** em seu `config.xml` arquivo:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Os bancos de dados Magento 1 e Magento 2 devem estar localizados no mesmo servidor MySQL e a conta de banco de dados deve ter acesso a ambos os bancos de dados.

## Estimativas de referência

O Adobe testou a migração de dados no seguinte sistema:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 core 2,6 GHz
* Banco de dados com 177.000 produtos, 355.000 pedidos e 214.000 clientes

## Resultados de desempenho

* Hora da migração das configurações: ~10 minutos
* Hora da migração de dados: ~9 horas (todos os dados, exceto regravações de URL, ~85% do total de dados)
* Estimativa de tempo de inatividade do site: alguns minutos para reindexar e alterar as configurações de DNS. Tempo adicional necessário para aquecer o cache da página.
