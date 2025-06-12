---
title: 'MDVA-40550: Produtos ausentes no front-end após reindexação'
description: O patch MDVA-40550 resolve o problema em que a reindexação resulta na ausência de produtos em algumas ou todas as categorias da loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-40550. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550: Produtos ausentes no front-end após reindexação

O patch MDVA-40550 resolve o problema em que a reindexação resulta na ausência de produtos em algumas ou todas as categorias da loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-40550. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto.
1. Alternar indexadores para **Atualizar por agendamento**.
   * Atribua o produto a uma categoria.
1. Habilite xdebug e torne o ponto de interrupção xdebug em `\Magento\Indexer\Model\Indexer::reindexAll` e `\Magento\Indexer\Model\IndexMutex::execute`.
1. Execute uma **reindexação completa** de `catalog_category_product` com o comando:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Aguarde a execução parar no ponto de interrupção `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Em outro console, execute um **reindexação parcial** em paralelo com o comando:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Aguarde a execução parar no ponto de interrupção `\Magento\Indexer\Model\IndexMutex::execute`. Ele bloqueará o indexador `catalog_category_product`.
1. Retomar a execução da reindexação completa de `catalog_category_product` e aguardar um tempo limite de bloqueio (60 segundos).

<u>Resultados esperados</u>:

Nenhuma mensagem de erro no console.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

*Não foi possível adquirir bloqueio para o índice: catalog_category_product.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
