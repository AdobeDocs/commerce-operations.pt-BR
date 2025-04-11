---
title: 'ACP2E-3705: a execução do cron "indexer_update_all_views" falha quando "MAGE_INDEXER_THREADS_COUNT" é definido'
description: Aplique o patch do ACP2E-3705 para corrigir o problema do Adobe Commerce em que a execução do cron "indexer_update_all_views" falha quando "MAGE_INDEXER_THREADS_COUNT" está definido.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
source-git-commit: 7ef772510274bc8681c395656437d64f8b40e70a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `indexer_update_all_views` execução de cron falha quando `MAGE_INDEXER_THREADS_COUNT` está definido

>[!NOTE]
>
>Este patch substitui o [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) para as versões 2.4.7 e posteriores.

O patch ACP2E-3705 corrige o problema em que a execução do cron `indexer_update_all_views` falha quando `MAGE_INDEXER_THREADS_COUNT` é definido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACP2E-3705. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A execução do cron `indexer_update_all_views` falha quando `MAGE_INDEXER_THREADS_COUNT` está definido com um valor maior que *2*, afetando especificamente o indexador [!UICONTROL Customer Segments] com B2B habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Aplique o patch de QPT [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Habilitar **[!UICONTROL Category Permissions]**.
1. Defina os seguintes indexadores para o modo **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Crie alguns produtos e atribua-os a uma categoria.
1. Executar um reindexação completo.
1. Ir para uma categoria e definir **[!UICONTROL Category Permissions]**.
1. Execute o trabalho do cron `indexer_update_all_views` com `MAGE_INDEXER_THREADS_COUNT` definido como *8*.

<u>Resultados esperados</u>:

A reindexação foi concluída sem erros.

<u>Resultados reais</u>:

O trabalho cron `indexer_update_all_views` encontra o seguinte erro:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
