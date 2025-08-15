---
title: 'MDVA-43601: os acionadores são removidos da tabela "catalog_product_price" após o reindexação completo'
description: O patch MDVA-43601 corrige o problema em que os acionadores são removidos da tabela "catalog_product_price" após um reindexação completo de "catalog_rule" ou "catalog_product". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601: os acionadores são removidos da tabela &quot;catalog_product_price&quot; após o reindexação completo

O patch MDVA-43601 corrige o problema em que os acionadores são removidos da tabela `catalogrule_product_price` após uma reindexação completa de `catalogrule_rule` ou `catalogrule_product`. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os acionadores são removidos da tabela `catalogrule_product_price` após uma reindexação completa de `catalogrule_rule` ou `catalogrule_product`.

<u>Etapas a serem reproduzidas</u>:

1. Defina todos os indexadores como *Atualizar pela Agenda*.
1. Verifique os disparadores criados para a tabela `catalogrule_product_price` executando a seguinte solicitação SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindexar manualmente `catalogrule_rule` ou `catalogrule_product` executando o seguinte comando: `bin/magento indexer:reindex catalogrule_rule`
1. Verifique novamente os acionadores da tabela `catalogrule_product_price`.

<u>Resultados esperados</u>:

Os acionadores na tabela `catalogrule_product_price` são preservados após uma reindexação completa.

<u>Resultados reais</u>:

Nenhum acionador encontrado para a tabela `catalogrule_product_price`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
