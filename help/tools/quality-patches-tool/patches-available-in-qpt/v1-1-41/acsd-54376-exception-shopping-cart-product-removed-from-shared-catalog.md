---
title: 'ACSD-54376: Exceção no carrinho de compras quando o produto foi removido de [!UICONTROL shared catalog]'
description: Aplique o patch ACSD-54376 para corrigir o problema do Adobe Commerce em que uma exceção ocorre no carrinho de compras quando um produto é removido do [!UICONTROL shared catalog] após ser adicionado ao carrinho.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: 59047ccb-d434-46cd-8d2f-ceb0c85a785a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376: Exceção no carrinho de compras quando o produto foi removido de [!UICONTROL shared catalog]

O patch ACSD-54376 corrige o problema em que uma exceção ocorre no carrinho de compras quando um produto é removido do [!UICONTROL shared catalog] depois de ser adicionado ao carrinho. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 está instalado. A ID do patch é ACSD-54376. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma exceção ocorre no carrinho de compras quando um produto é removido do [!UICONTROL shared catalog] depois de ser adicionado ao carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com B2B.
1. Habilitar [!UICONTROL shared catalog].
1. Crie um produto e atribua-o ao padrão [!UICONTROL shared catalog].
1. Adicione um produto ao carrinho pela loja.
1. Remova o produto do [!UICONTROL shared catalog].
1. Navegue até a página de finalização usando o menu suspenso do minicarrinho.

<u>Resultados esperados</u>:

As exceções são tratadas e não são exibidas a você.

<u>Resultados reais</u>:

Uma exceção não tratada é exibida na página de check-out.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
