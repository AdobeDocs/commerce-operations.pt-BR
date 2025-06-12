---
title: 'ACSD-51036: As condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status do envio'
description: Aplique o patch ACSD-51036 para corrigir o problema do Adobe Commerce em que há condições de corrida durante chamadas de API REST simultâneas, resultando em uma substituição do status de envio na tabela itens solicitados.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036: As condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status de entrega na tabela itens solicitados

O patch ACSD-51036 corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status de envio na tabela itens solicitados. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.31 está instalado. A ID do patch é ACSD-51036. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status da remessa na tabela itens solicitados.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com dois itens.
1. Item de NFF A.
1. Envie solicitação de reembolso para o item A via REST API simultaneamente enquanto envia uma solicitação de entrega para o item B.
1. Ir para a ordem em **[!UICONTROL Admin Panel]**.

<u>Resultados esperados</u>

O status *[!UICONTROL Shipped 1]* deve estar presente para o item B na tabela ordenada *[!UICONTROL Items]*.

<u>Resultados reais</u>

O status *[!UICONTROL Shipped 1]* não está presente para o item B na tabela ordenada *[!UICONTROL Items]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
