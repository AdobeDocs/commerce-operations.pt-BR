---
title: 'MDVA-27239: os produtos de venda cruzada não são exibidos'
description: O patch do MDVA-27239 corrige o problema em que os produtos de venda cruzada não são exibidos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: os produtos de venda cruzada não são exibidos

O patch do MDVA-27239 corrige o problema em que os produtos de venda cruzada não são exibidos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4, 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos de venda cruzada não são exibidos no bloco de venda cruzada na página do carrinho de compras.

<u>Pré-requisitos</u>:

1. Desative o módulo Magento_TargetRule ou remova-o do bloco de layout Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Criar produto 1.
1. Crie uma atualização de programação para o Produto 1, de modo que os produtos recém-criados tenham row_id diferente de entity_id.
1. Crie o Produto 2, Produto 3 e Produto 4.
1. Defina o Produto 3 como venda cruzada para o Produto 4.
1. Defina o Produto 4 como venda cruzada para o Produto 2.

<u>Etapas a serem reproduzidas</u>:

1. Adicione o Produto 4 e o Produto 2 ao carrinho de compras.
1. Verifique a página do carrinho de compras.

<u>Resultados esperados</u>:

O produto 3 é exibido no bloco de venda cruzada.

<u>Resultados reais</u>:

O bloco de venda cruzada está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
