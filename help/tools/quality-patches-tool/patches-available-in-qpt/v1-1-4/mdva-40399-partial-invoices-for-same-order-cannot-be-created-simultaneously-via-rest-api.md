---
title: "MDVA-40399: faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via API"
description: O patch MDVA-40399 corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente por meio da API Rest. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 está instalada. A ID do patch é MDVA-40399. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: faturas parciais para o mesmo pedido não podem ser criadas simultaneamente via API

O patch MDVA-40399 corrige o problema em que faturas parciais para o mesmo pedido não podem ser criadas simultaneamente por meio da API Rest. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 está instalada. A ID do patch é MDVA-40399. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Faturas parciais para os mesmos pedidos não podem ser criadas simultaneamente usando a API Rest.

<u>Pré-requisitos</u>:

Um produto configurável com pelo menos duas variações.

<u>Etapas a serem reproduzidas</u>:

1. Adicione ambas as variantes do produto configurável ao carrinho.
1. Coloque o pedido.
1. Crie duas faturas simultaneamente para o pedido por meio da API Rest.

<u>Resultados esperados</u>:

* Ambas as faturas devem ser criadas com sucesso.
* `qty_invoiced` deve ser atualizado para ambas as faturas na tabela `sales_order_item`.
* Ambos os produtos devem ter uma quantidade faturada.

<u>Resultados reais</u>:

* Ambas as NFFs são criadas com sucesso.
* `qty_invoiced` não é atualizado em relação a uma das faturas na tabela `sales_order_item`.
* Na página **Visualização do pedido** do Administrador, a quantidade de faturas é exibida somente para um produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
