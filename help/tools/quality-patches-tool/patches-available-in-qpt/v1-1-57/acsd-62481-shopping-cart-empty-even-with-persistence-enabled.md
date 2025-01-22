---
title: 'ACSD-62481: O carrinho de compras permanece vazio mesmo com o [!UICONTROL Persistence] ativado'
description: Aplique o patch ACSD-62481 para corrigir o problema do Adobe Commerce em que o recurso de carrinho persistente falha ao usar o pop-up de logon durante a finalização da compra.
feature: Shopping Cart, Checkout
role: Admin, Developer
source-git-commit: 27a98c42f2c514b3dd1a2f59c140b60b7ac26592
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-62481: O carrinho de compras permanece vazio mesmo com o *[!UICONTROL Persistence]* ativado

O patch ACSD-62481 corrige o problema em que o recurso de carrinho persistente falha ao usar o pop-up de logon durante o check-out porque não tem a caixa de seleção *[!UICONTROL Remember Me]*, fazendo com que os produtos desapareçam do carrinho após desconectar. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-62481. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O recurso de carrinho persistente falha ao usar o pop-up de logon durante o check-out porque ele não tem a caixa de seleção *[!UICONTROL Remember Me]*. Isso faz com que os produtos desapareçam do carrinho após desconectar.

<u>Etapas a serem reproduzidas</u>:

1. No admin, defina a conta de convidado e as configurações do carrinho persistente da seguinte maneira:

   * Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** e defina *[!UICONTROL Allow Guest Checkout]* como *Não*.

      * Clique em **[!UICONTROL Save Config]**.

   * Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** e defina *[!UICONTROL Enable Persistence]* como *Sim*.
   * Deixe todas as outras configurações como padrão, mas altere *[!UICONTROL Clear Persistence on Sign Out]* para *Não*.

      * Clique em **[!UICONTROL Save Config]**.

1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** para adicionar um produto simples ao catálogo.

   * Preencha os detalhes mínimos necessários e verifique se está em estoque.

1. No front-end, crie uma conta de cliente usando o formulário principal `(../customer/account/create/)` e saia.
1. Adicione o produto ao carrinho como convidado.
1. Abra o minicarrinho com o ícone na parte superior direita e clique em **[!UICONTROL View and Edit Cart]**.
1. Prossiga para o check-out.
1. Faça logon na nova conta do cliente por meio da caixa de diálogo pop-up exibida e faça logoff.

<u>Resultados esperados</u>:

O carrinho retém os produtos do usuário conectado anteriormente.

<u>Resultados reais</u>:

* O carrinho está vazio.
* A caixa de diálogo de logon pop-up não mostra a opção *[!UICONTROL Remember Me]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
