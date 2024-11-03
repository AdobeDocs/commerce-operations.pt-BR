---
title: "ACSD-44938: VAT_ID não pode ser aplicado na solicitação do GraphQL para o usuário convidado"
description: O patch ACSD-44938 corrige o problema em que a VAT_ID não pode ser aplicada em uma solicitação GraphQL para um usuário convidado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-44938: VAT_ID não pode ser aplicado na solicitação GraphQL para o usuário convidado

O patch ACSD-44938 corrige o problema em que a VAT_ID não pode ser aplicada em uma solicitação GraphQL para um usuário convidado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

VAT_ID não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.

<u>Etapas a serem reproduzidas</u>:

1. Siga as etapas mencionadas no [tutorial do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-shopping-cart.html) em nossa documentação do desenvolvedor para criar um carrinho de convidado.
1. Tente aplicar VAT_ID para o usuário convidado usando o GraphQL.

<u>Resultados esperados</u>:

VAT_ID pode ser aplicado da mesma forma que para um cliente registrado. Consulte o artigo [createCustomerAddress mutation](https://developer.adobe.com/commerce/webapi/graphql/mutations/create-customer-address.html) na documentação do desenvolvedor.

<u>Resultados reais</u>:

VAT_ID não pode ser aplicado a um usuário convidado usando GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
