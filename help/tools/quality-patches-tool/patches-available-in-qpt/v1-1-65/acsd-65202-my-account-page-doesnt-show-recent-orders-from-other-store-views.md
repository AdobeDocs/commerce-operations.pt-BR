---
title: 'ACSD-65202: a página Minha conta não mostra pedidos recentes de outras exibições de loja'
description: Aplique o patch ACSD-65202 para corrigir o problema do Adobe Commerce, em que a página Minha conta não exibe pedidos recentes de outras exibições de loja na mesma loja.
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 0af6ab4ef15e8aa56354886b341b70a080662eae
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# ACSD-65202: a página [!UICONTROL My Account] não mostra pedidos recentes de outras exibições de loja

O patch ACSD-65202 corrige o problema em que a página **[!UICONTROL My Account]** não exibe pedidos recentes de outras exibições de loja na mesma loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-65202. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p12

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao ir para a página da conta do cliente (seção **[!UICONTROL My Account]**), você não vê pedidos recentes feitos em outra visualização de loja. No entanto, ao acessar o histórico de pedidos (seção *[!UICONTROL My Orders]*), você verá todos os pedidos em ambas as Exibições de Loja.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. No painel *Admin*, crie um novo Modo de Exibição de Loja e insira seu código como, *segundo*, para identificar o modo de exibição.
1. Crie um produto simples e reindexe.
1. Crie uma conta de cliente e coloque um pedido na exibição de armazenamento padrão cujo código é *padrão*.
1. Vá para a página **[!UICONTROL My Orders]** e verifique se a ordem está visível nos Modos de Exibição de Loja, por exemplo:
1. Padrão: https://localhost/pub/default/sales/order/history/
1. Segunda: https://localhost/pub/second/sales/order/history/

1. Vá para a página **[!UICONTROL My Account]** em ambos os Modos de Exibição de Loja:
1. Padrão: https://localhost/pub/default/customer/account/
1. Segunda: https://localhost/pub/second/customer/account/

<u>Resultados esperados</u>:

Você pode ver pedidos de ambas as exibições de armazenamento na página Pedidos. É a mesma loja, só uma vista diferente.

<u>Resultados reais</u>:

O comportamento é inconsistente. Os pedidos não aparecem na segunda exibição de armazenamento.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
