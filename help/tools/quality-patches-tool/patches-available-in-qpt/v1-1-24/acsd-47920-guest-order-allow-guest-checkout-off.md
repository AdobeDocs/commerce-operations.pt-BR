---
title: 'ACSD-47920: um usuário convidado pode fazer pedidos por meio da API REST mesmo quando [!UICONTROL Allow Guest Checkout] está desativado'
description: Aplique o patch ACSD-47920 para corrigir o problema do Adobe Commerce em que os pedidos podem ser feitos por meio da API REST como um usuário convidado mesmo quando o [!UICONTROL Allow Guest Checkout] está desativado.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: um usuário convidado pode fazer pedidos por meio da API REST mesmo quando **[!UICONTROL Allow Guest Checkout]** está desativado

O patch ACSD-47920 corrige o problema em que os pedidos podem ser feitos por meio da API REST como um usuário convidado mesmo quando o **[!UICONTROL Allow Guest Checkout]** está desativado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-47920. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pedidos podem ser feitos por meio da API Rest como um usuário convidado, mesmo quando o **[!UICONTROL Allow Guest Checkout]** está desativado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Administrador do Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > e defina **[!UICONTROL Allow Guest Checkout]** como _Não_.
1. Use a REST API para adicionar um produto ao carrinho e fazer um pedido.

<u>Resultados esperados</u>:

A API de check-out de convidado retorna um erro *[!UICONTROL Sorry, guest checkout is not available]* se **[!UICONTROL Allow Guest Checkout]** estiver definido como _Não_.

<u>Resultados reais</u>:

A API de check-out de convidado permite fazer um pedido mesmo se **[!UICONTROL Allow Guest Checkout]** estiver definido como _Não_.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
