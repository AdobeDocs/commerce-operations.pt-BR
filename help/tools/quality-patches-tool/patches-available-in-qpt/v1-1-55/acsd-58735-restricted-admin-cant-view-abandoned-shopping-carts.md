---
title: "ACSD-58735: O administrador restrito não pode visualizar carrinhos de compras abandonados na conta do cliente para o site associado"
description: Aplique a correção ACSD-58735 para corrigir o problema do Adobe Commerce em que um administrador restrito não consegue visualizar os carrinhos de compras abandonados na página da conta do cliente no Administrador do Commerce de um site associado.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735: O administrador restrito não pode visualizar carrinhos de compras abandonados na conta do cliente para o site associado

O patch ACSD-58735 corrige o problema em que um usuário administrador com uma função restrita não consegue visualizar carrinhos de compras de clientes abandonados da guia Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]**.

O problema ocorre porque, ao exibir a visualização em grade para vários sites, se um carrinho abandonado for carregado por padrão no painel de Administração, ele não obterá a ID da loja associada para exibição.

Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-58735. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os administradores restritos não podem visualizar carrinhos de compras abandonados na página da conta do cliente no painel de Administração.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma função de administrador com acesso a apenas um dos sites.
1. Criar um carrinho abandonado.
1. Faça logon como um usuário administrador com privilégios totais. Verifique **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** e veja se o carrinho é exibido.
1. Marque **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** como o usuário administrador restrito.

<u>Resultados esperados</u>:

O administrador restrito pode ver carrinhos de compras abandonados para o site associado.

<u>Resultados reais</u>:

O administrador restrito não vê carrinhos de compras abandonados para o site associado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
