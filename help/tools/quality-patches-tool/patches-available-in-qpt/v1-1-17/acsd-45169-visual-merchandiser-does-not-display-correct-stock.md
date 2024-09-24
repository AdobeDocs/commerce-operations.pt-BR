---
title: "ACSD-45169: o Visual Merchandiser exibe ações e preços incorretos para o produto configurável"
description: O patch ACSD-45169 corrige o problema em que o Visual Merchandiser não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45169. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169: o Visual Merchandiser exibe ações e preços incorretos para o produto configurável

O patch ACSD-45169 corrige o problema em que o Visual Merchandiser não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45169. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O Visual Merchandiser não exibe o estoque e o preço corretos de um produto configurável após a aplicação de uma atualização em preparo.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Crie qualquer atualização programada para o produto simples (Você só precisa ter IDs de linha e entidade diferentes).
1. Crie um produto configurável.
1. Atribua o produto configurável a uma categoria.
1. Abra a categoria e observe o produto configurável na seção Visual Merchandiser.

<u>Resultados esperados</u>:

O Visual Merchandiser exibe as ações e o preço corretos.

<u>Resultados reais</u>:

O Visual Merchandiser exibe ações e preços incorretos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
