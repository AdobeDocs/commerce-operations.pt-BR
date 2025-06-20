---
title: 'ACSD-49849: o email do cliente foi substituído pelo email do PayPal'
description: Aplique o patch ACSD-49849 para corrigir o problema do Adobe Commerce em que o email do cliente foi substituído pelo email do PayPal ao fazer um pedido no PayPal Express via GraphQL.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849: o email do cliente foi substituído pelo email [!DNL PayPal]

O patch ACSD-49849 corrige o problema em que o email de um cliente é substituído por um email [!DNL PayPal's] ao ser feito um pedido com [!DNL PayPal Express] via GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49849. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O email de um cliente é substituído pelo email [!DNL PayPal's] ao fazer um pedido com [!DNL PayPal Express] via GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Habilitar e configurar [!DNL PayPal Express] e definir **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crie um produto simples.
1. Conclua o check-out do convidado usando o GraphQL. Para obter mais informações, consulte o [tutorial de check-out do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) na Documentação do desenvolvedor do Adobe Commerce.
1. Use [!DNL PayPal Express] como método de pagamento.
1. Anote o email usado na etapa em que você [configurou seu email para o carrinho](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) na Documentação do desenvolvedor do Adobe Commerce.
1. Depois que o pedido for feito, vá para o administrador do Adobe Commerce e verifique o email na ordem criada.

<u>Resultados esperados</u>:

O email é o mesmo definido durante o check-out.

<u>Resultados reais</u>:

O email definido durante o check-out é substituído pelo email definido na conta [!DNL PayPal].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
