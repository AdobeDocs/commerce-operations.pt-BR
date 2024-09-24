---
title: "ACSD-46581: O total de impostos estimado não é atualizado após selecionar um país no carrinho de compras"
description: Aplique o patch ACSD-46581 para resolver o problema do Adobe Commerce, em que a alíquota do imposto não é atualizada após trocar o país no carrinho de compras.
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-46581: O total de imposto estimado não é atualizado após selecionar um país no carrinho de compras

Este patch ACSD-46581 resolve o problema em que a alíquota do imposto não é atualizada depois de trocar o país no carrinho de compras. Ele é atualizado somente após selecionar o método de envio. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 está instalado. A ID do patch é ACSD-46581. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A alíquota do imposto não é atualizada depois de alternar o país no carrinho de compras.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, vá para **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Criar uma nova alíquota de imposto para **[!UICONTROL Country]** = _Estados Unidos_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Criar uma nova alíquota de imposto para **[!UICONTROL Country]** = _Índia_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Crie uma regra de imposto com alíquotas de imposto para os EUA e a Índia.
1. Vá para **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** e habilite mais de um método de envio (_Taxa Uniforme_ e _Envio Gratuito_, por exemplo).
1. Crie um produto simples com a classe de imposto **[!UICONTROL Taxable Goods]**.
1. Adicione o produto ao carrinho na loja.
1. Abra o carrinho de compras e verifique o valor do imposto.
1. As configurações de imposto padrão dos Estados Unidos são aplicadas e o imposto é calculado com base em uma taxa de 8,25%.
1. Mude o país para a Índia.

<u>Resultados esperados</u>:

O valor do imposto mudou para 10% quando o país foi transferido para a Índia.

<u>Resultados reais</u>:

O valor do imposto permanece o mesmo na seção total do carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
