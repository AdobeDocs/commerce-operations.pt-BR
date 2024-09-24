---
title: "MDVA-43232: a classificação de produtos em um merchandiser visual por Preço especial para cima (ou para baixo) causa um erro"
description: O patch MDVA-43232 corrige o problema em que a classificação de produtos no visual merchandiser por Preço especial para cima (ou para baixo) causa um erro ao salvar a categoria. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-43232. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232: Classificar produtos em um merchandiser visual por Preço especial para cima (ou para baixo) causa um erro

O patch MDVA-43232 corrige o problema em que a classificação de produtos no visual merchandiser por Preço especial para cima (ou para baixo) causa um erro ao salvar a categoria. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 está instalada. A ID do patch é MDVA-43232. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Classificar produtos no visual merchandiser por Preço especial para cima (ou para baixo) causa um erro ao salvar a categoria.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se há dois sites.
1. Navegue até **Lojas** > **Configuração** > **Catálogo** > **Preço** e defina Escopo do Preço do Catálogo = Site.
1. Novamente, navegue até **Lojas** > **Configuração** > **Catálogo** > **Visual Merchandiser** > **Atributos Visíveis para Regras de Categoria** > e adicione um Preço Especial.
1. Crie um produto simples e atribua os produtos a ambos os sites.
1. Adicione um preço especial ao escopo padrão do produto.
1. Alterne para o escopo da outra loja e substitua o Preço e o Preço Especial desse produto.
1. Fazer uma reindexação `catalog_product_price`.
1. Vá para **Catálogo** > **Categorias** e crie uma nova categoria.
1. Adicione uma regra de categoria para filtrar produtos com preço especial.
1. Salve a categoria.
1. Na seção Produtos em Categoria, defina Ordem de classificação = Preço especial como Superior (ou Inferior).
1. Salve a categoria novamente.

<u>Resultados esperados</u>:

A categoria é salva sem erros.

<u>Resultados reais</u>:

Uma exceção é lançada:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
