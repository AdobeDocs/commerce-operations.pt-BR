---
title: "ACSD-45520: opções de amostra não selecionadas na página de detalhes do produto"
description: O patch ACSD-45520 corrige o problema em que as opções de amostra não são pré-selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho de compras. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-45520: opções de amostra não selecionadas na página de detalhes do produto

O patch ACSD-45520 corrige o problema em que as opções de amostra não são pré-selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho de compras. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções de amostra não são selecionadas na página de detalhes do produto quando um usuário edita produtos configuráveis do carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com opções de produto (por exemplo, cor).
1. Adicione o produto configurável ao carrinho.
1. Vá para a página Meu carrinho.
1. Clique no botão de edição no produto configurável adicionado na Etapa 1.
1. Observe as opções de produto na página de edição.

<u>Resultados esperados</u>:

As opções de produto estão selecionadas.

<u>Resultados reais</u>:

As opções de produto não estão selecionadas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
