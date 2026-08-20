---
title: 'MDVA-42507: o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho'
description: O patch MDVA-42507 resolve o problema em que o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-42507. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
exl-id: 19f61e31-67da-4bd6-bce7-a9250f3946c7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-42507: o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho

O patch MDVA-42507 resolve o problema em que o cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-42507. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Ativar modo de desenvolvedor.
1. Abra vários produtos e páginas de categoria e verifique (por meio de cabeçalhos) se eles são carregados do cache.
1. Aplique qualquer atualização de preparo para a regra de carrinho.
1. Verifique se as páginas de categoria e produto ainda estão carregadas do cache.

<u>Resultados esperados</u>:

O cache de página inteira NÃO é limpo após a aplicação da atualização de preparo para a regra de carrinho.

<u>Resultados reais</u>:

O cache de página inteira é limpo após a aplicação da atualização de preparo para a regra de carrinho.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
