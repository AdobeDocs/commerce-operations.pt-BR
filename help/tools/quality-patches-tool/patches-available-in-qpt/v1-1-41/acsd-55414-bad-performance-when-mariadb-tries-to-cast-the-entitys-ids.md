---
title: 'ACSD-55414: Desempenho incorreto quando MariaDB tenta lançar os entitys_ids'
description: Aplique o patch ACSD-55414 para corrigir o problema do Adobe Commerce quando o MariaDB tenta converter "entitys_ids" de sequência de caracteres em número inteiro, isso dificulta o desempenho da reindexação.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414: Desempenho incorreto quando MariaDB tenta converter o `entitys_ids`

O patch ACSD-55414 corrige o problema em que o desempenho da reindexação é dificultado quando o MariaDB tenta converter `entitys_ids` de sequência de caracteres em inteiro. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.41 está instalado. A ID do patch é ACSD-55414. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho da reindexação é dificultado quando o MariaDB tenta converter o `entitys_ids` de sequência de caracteres em inteiro.

<u>Etapas a serem reproduzidas</u>:

1. Atualize `setup/performance-toolkit/profiles/ce/small.xml` configurando *50000* produtos simples.
1. Gere este perfil executando o comando: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Executar reindex: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Resultados esperados</u>:

O reindexação leva um tempo razoável para ser concluída.

<u>Resultados reais</u>:

A reindexação leva muito tempo para ser concluída.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
