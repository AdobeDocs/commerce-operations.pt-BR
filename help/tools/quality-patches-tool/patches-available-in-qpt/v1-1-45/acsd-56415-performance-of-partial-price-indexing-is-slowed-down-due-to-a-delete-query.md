---
title: 'ACSD-56415: desempenho de [!UICONTROL Partial Price Indexing] desacelerado devido à consulta "DELETE"'
description: Aplique o patch ACSD-56415 para corrigir o problema do Adobe Commerce em que o desempenho do [!UICONTROL Partial Price Indexing] é atrasado devido a uma consulta "DELETE" quando o banco de dados tem muitos dados de preço parciais para indexar.
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415: O desempenho de [!UICONTROL Partial Price Indexing] está lento devido à consulta `DELETE`

O patch ACSD-56415 corrige o problema em que o desempenho de [!UICONTROL Partial Price Indexing] é atrasado devido a uma consulta `DELETE` quando o banco de dados tem muito índice de dados de preço parcial. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 está instalado. A ID do patch é ACSD-56023. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho de [!UICONTROL Partial Price Indexing] está atrasado devido a uma consulta `DELETE` quando o banco de dados tem muito índice de dados de preço parcial.

<u>Etapas a serem reproduzidas</u>:

1. Crie *300000 produtos* e *10 sites* usando o perfil de desempenho grande.
1. Faça logon no Painel de administração.
1. Criar *10 grupos de clientes*.
1. Execute a consulta abaixo para adicionar produtos à tabela `_cl`:

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Execute o comando abaixo para acionar o processo de indexação de preço parcial:

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Resultados esperados</u>:

O DELETE de consulta SQL `main_table` FROM `catalog_product_index_price` é executado rapidamente.

<u>Resultados reais</u>:

A DELETE de consulta SQL `main_table` FROM `catalog_product_index_price` é executada muito lentamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
