---
title: 'ACSD-51683: a opção personalizável não pode ser adicionada ao carrinho usando o GraphQL'
description: Aplique o patch ACSD-51683 para corrigir o problema do Adobe Commerce em que a opção personalizável não pode ser adicionada ao carrinho usando o GraphQL.
feature: GraphQL
role: Admin
exl-id: 9cdf71aa-3dea-4f8c-b4d6-d6f192a9710d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51683: a opção personalizável não pode ser adicionada ao carrinho usando o GraphQL

O patch ACSD-51683 corrige o problema em que a opção personalizável não pode ser adicionada ao carrinho usando o GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 está instalado. A ID do patch é ACSD-51683. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A opção personalizável não pode ser adicionada ao carrinho usando o GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com uma opção personalizável de **Campo de texto**.
1. [Adicionar ao carrinho](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) o produto criado com a opção personalizável necessária via GraphQL.
1. Envie a solicitação de [carrinho](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) do GraphQL para verificar o produto e seus detalhes no carrinho.

<u>Resultados esperados</u>

A seção `Customizable_options` na resposta do GraphQL contém os dados fornecidos ao adicionar o produto ao carrinho.

<u>Resultados reais</u>

A seção `Customizable_options` na resposta do GraphQL está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
