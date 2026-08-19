---
title: 'ACSD-44938: VAT_ID não pode ser aplicado na solicitação  [!DNL GraphQL]  de usuário convidado'
description: O patch ACSD-44938 corrige o problema em que o "VAT_ID" não pode ser aplicado em uma solicitação  [!DNL GraphQL]  de um usuário convidado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-44938: VAT_ID não pode ser aplicado na solicitação [!DNL GraphQL] para o usuário convidado

O patch ACSD-44938 corrige o problema em que o `VAT_ID` não pode ser aplicado em uma solicitação [!DNL GraphQL] para um usuário convidado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`VAT_ID` não pode ser aplicado em uma solicitação [!DNL GraphQL] para um usuário convidado.

<u>Etapas a serem reproduzidas</u>:

1. Siga as etapas mencionadas no [[!DNL GraphQL] tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) em nossa documentação do desenvolvedor para criar um carrinho de convidado.
1. Tente aplicar `VAT_ID` para o usuário convidado usando [!DNL GraphQL].

<u>Resultados esperados</u>:

`VAT_ID` pode ser aplicado da mesma forma que para um cliente registrado. Consulte o artigo [`createCustomerAddress` mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) na documentação do desenvolvedor.

<u>Resultados reais</u>:

`VAT_ID` não pode ser aplicado a um usuário convidado usando [!DNL GraphQL].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre o [!DNL Quality Patches Tool], consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
