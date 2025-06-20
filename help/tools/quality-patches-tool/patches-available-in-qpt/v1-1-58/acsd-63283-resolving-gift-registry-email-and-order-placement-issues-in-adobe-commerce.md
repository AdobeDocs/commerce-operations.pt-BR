---
title: 'ACSD-63283: Resolvendo problemas de email e posicionamento de pedido do [!UICONTROL Gift Registry] no Adobe Commerce'
description: Aplique o patch ACSD-63283 para corrigir o problema do Adobe Commerce em que a solicitação de itens do [!UICONTROL Gift Registry] causa uma exceção e garante que o [!UICONTROL Gift Registry Updates] inclua apenas os itens corretos.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: Resolvendo problemas de email e posicionamento de pedido do [!UICONTROL Gift Registry] no Adobe Commerce

O patch ACSD-63283 corrige o problema em que a ordenação de itens do [!UICONTROL Gift Registry] causa uma exceção e garante que o [!UICONTROL Gift Registry Updates] inclua apenas os itens corretos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63283. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

>[!NOTE]
>Este patch substitui e estende o patch QPT [ACSD-56280](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed).

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A funcionalidade [!UICONTROL Gift Registry] no Adobe Commerce é afetada por dois problemas significativos:

* Quando um cliente faz um pedido para itens de seu [!UICONTROL Gift Registry], o processo falha devido a uma exceção sendo acionada.
* Além disso, o email [!UICONTROL Gift Registry Updates] enviado ao proprietário do Registro inclui incorretamente itens de todos os registros de presentes, em vez de restringir as atualizações a itens no Registro específico que está sendo atualizado.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos: Produto A e Produto B.
1. Crie dois clientes: Cliente A e Cliente B.
1. Faça logon como Cliente A e crie um novo [!UICONTROL Gift Registry].
1. Navegue até a página do produto A e adicione-a ao [!UICONTROL Wishlist]. Abra o [!UICONTROL Wishlist Page] e mova o Produto A para o [!UICONTROL Gift Registry] usando [!UICONTROL Add to Gift Registry].
1. Faça logon como Cliente B, crie um novo [!UICONTROL Gift Registry] e adicione o Produto B a ele.
1. Como Cliente B, compartilhe o [!UICONTROL Gift Registry] por email: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Faça logout como Cliente B.
1. Clique no link recebido no email. Adicione o Produto B ao [!UICONTROL Cart] e faça um pedido.

<u>Resultados esperados</u>:

O Cliente B recebe o email com itens atualizados somente de seu registro de presentes.

<u>Resultados reais</u>:

O Cliente B recebe o email com itens de todos os registros de presentes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
