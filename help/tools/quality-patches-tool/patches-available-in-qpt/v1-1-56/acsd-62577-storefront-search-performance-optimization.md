---
title: 'ACSD-62577: otimização de desempenho de pesquisa de vitrine'
description: Aplique o patch ACSD-62577 para corrigir o problema do Adobe Commerce em que o desempenho de pesquisa da loja é degradado devido à execução lenta da consulta causada por uma tabela "search_query" grande.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: otimização de desempenho de pesquisa de vitrine

O patch ACSD-62577 corrige o problema de desempenho lento de consultas de pesquisa da loja ao otimizar índices de consulta e tabela. Este patch está disponível com o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. A ID do patch é ACSD-62577. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6, 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As tabelas `search_query` grandes retardam significativamente as pesquisas de vitrine eletrônica, aumentando os tempos de resposta de front-end devido a consultas ineficientes e à falta de índices de tabela otimizados.

<u>Etapas a serem reproduzidas</u>:

1. Configure o Adobe Commerce Develop usando o kit de ferramentas de desempenho `small.xml`.
1. Acesse a linha de comando SQL e exclua a tabela `search_query` usando os seguintes comandos:

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Preencha a tabela `search_query` com um grande número de registros, por exemplo: 4 milhões de registros.
1. Acione caches de reindexação e liberação.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Habilitar logs de depuração do banco de dados:

   ```
   bin/magento dev:query-log:enable  
   ```

1. Pesquise um termo na barra de pesquisa da loja, por exemplo,
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Verifique o `db.log` para o tempo de execução da consulta para o seguinte SQL:

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Resultados esperados</u>:

O tempo de execução da consulta é otimizado, resultando em um aumento menos significativo no tempo de resposta ao processar tabelas `search_query` grandes.

<u>Resultados reais</u>:

O tempo de execução da consulta aumenta significativamente devido à manipulação ineficiente da tabela `search_query` grande:

```
TIME: 10.8520 seconds  
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
