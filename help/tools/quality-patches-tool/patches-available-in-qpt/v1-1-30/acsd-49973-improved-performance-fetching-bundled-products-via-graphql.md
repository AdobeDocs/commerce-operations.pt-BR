---
title: "ACSD-49973: melhor desempenho ao buscar produtos empacotados via [!DNL GraphQL]"
description: Aplique o patch ACSD-49973 para corrigir o problema do Adobe Commerce em que ocorre degradação de desempenho ao buscar produtos agrupados via  [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973: melhor desempenho ao buscar produtos empacotados via [!DNL GraphQL]

O patch ACSD-49973 melhora o desempenho ao buscar produtos empacotados via [!DNL GraphQL]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 está instalado. A ID do patch é ACSD-49973. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A degradação de desempenho ocorre ao buscar produtos agrupados via [!DNL GraphQL].

<u>Pré-requisitos</u>:

Crie produtos do pacote 2000 usando o [Kit de ferramentas de desempenho](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=pt-BR).

<u>Etapas a serem reproduzidas</u>:

1. Habilitar o agente de log de consulta [!DNL DB]:

   ```
   bin/magento dev:query-log:enable
   ```

1. Executar a seguinte consulta [!DNL GraphQL]:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Verifique `var/log/db.log` para solicitações para a tabela `catalog_product_bundle_selection`.

<u>Resultados esperados</u>:

As solicitações para a tabela `catalog_product_bundle_selection` não devem estar presentes em `var/log/db.log`.

<u>Resultados reais</u>:

Há 2000 solicitações para a tabela `catalog_product_bundle_selection` que são acionadas ao mesmo tempo, o que causa degradação de desempenho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
