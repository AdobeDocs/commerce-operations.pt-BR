---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule] não aplica desconto do carrinho [!UICONTROL Customer Segment] correspondente sem código de cupom'
description: Aplique o patch ACSD-58163 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule] não aplica um desconto para um convidado do carrinho [!UICONTROL Customer Segment] correspondente sem um código de cupom.
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163: [!UICONTROL Cart Price Rule] não aplica desconto do carrinho [!UICONTROL Customer Segment] correspondente sem código de cupom

O patch ACSD-58163 corrige o problema em que o [!UICONTROL Cart Price Rule] não aplica um desconto do carrinho [!UICONTROL Customer Segment] correspondente sem um código de cupom. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 está instalado. A ID do patch é ACSD-58163. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Cart Price Rule] não aplica um desconto a um convidado do carrinho [!UICONTROL Customer Segment] correspondente sem um código de cupom.

<u>Etapas a serem reproduzidas</u>:

1. Criar segmento de cliente:
   * Para visitantes.
   * Com a condição de ter um produto no carrinho de compras.

1. Criar um *[!UICONTROL Cart Price Rule]*:
   * Sem código de cupom.
   * Com a condição para corresponder ao segmento de cliente visitante.

1. Crie um produto simples.
1. Abra a loja como convidado.
1. Adicione um produto simples ao carrinho.
1. Vá para o carrinho de compras.

<u>Resultados esperados</u>:

*[!UICONTROL Cart Price Rule]* desconto aplicado.

<u>Resultados reais</u>:

O desconto de *[!UICONTROL Cart Price Rule]* não foi aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
