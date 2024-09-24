---
title: "ACSD-50817: otimiza o trabalho cron sales_clean_quotes para ser executado mais rápido"
description: Aplique o patch ACSD-50817 para otimizar o trabalho cron "sales_clean_quotes" para ser executado mais rápido adicionando um índice composto nas colunas "store_id" e "updated_at" na tabela de cotações.
feature: Quotes
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-50817: otimiza o trabalho cron `sales_clean_quotes` para ser executado mais rápido

O patch ACSD-50817 otimiza o trabalho cron `sales_clean_quotes` para ser executado mais rápido adicionando um índice composto nas colunas `store_id` e `updated_at` na tabela de aspas. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.31 está instalado. A ID do patch é ACSD-50817.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O trabalho cron `sales_clean_quotes` é muito lento. Com este patch, ele foi otimizado para ser executado mais rápido ao adicionar um índice composto nas colunas `store_id` e `updated_at` na tabela de aspas.

<u>Etapas a serem reproduzidas</u>:

1. Gerar 50-80M de cotações com `updated_at` definido como &lt; período de 30 dias.
1. Execute o trabalho cron `sales_clean_quotes` ou a seguinte consulta na tabela de cotações:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Resultados esperados</u>

O trabalho Cron `sales_clean_quotes` é otimizado para execução mais rápida ao adicionar um índice composto nas colunas `store_id` e `updated_at` na tabela de aspas.

<u>Resultados reais</u>

A consulta está muito lenta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
