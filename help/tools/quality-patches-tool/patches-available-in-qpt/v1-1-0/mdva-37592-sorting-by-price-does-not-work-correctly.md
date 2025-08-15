---
title: 'MDVA-37592: A classificação por preço não funciona para produtos com preço zero'
description: O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 está instalada. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592: A classificação por preço não funciona para produtos com preço zero

O patch do Adobe Commerce MDVA-37592 resolve o problema em que a classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 está instalada. A ID do patch é MDVA-37592. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa arquitetura de nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os tipos de implantação) 2.3.6-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classificação por preço não funciona corretamente para produtos com preço zero atribuído a um catálogo compartilhado.

<u>Pré-requisitos</u>:

B2B está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar catálogo compartilhado.
1. Crie quatro produtos com os preços a seguir e atribua-os a uma categoria - US$ 50, US$ 60, US$ 70 e US$ 80.
1. Crie um catálogo compartilhado com os produtos acima.
1. Defina o preço personalizado como zero para o produto com um preço de US$ 70.
1. Agora, crie um usuário da empresa e atribua-o ao catálogo compartilhado recém-criado.
1. Faça logon usando a conta da empresa e navegue até a categoria à qual os produtos estão atribuídos.
1. Tente classificar por preço.

<u>Resultados esperados</u>:

O produto com preço zero é classificado corretamente.

<u>Resultados reais</u>:

O produto com preço zero NÃO está classificado corretamente. Em vez disso, é classificado de acordo com o preço original.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
