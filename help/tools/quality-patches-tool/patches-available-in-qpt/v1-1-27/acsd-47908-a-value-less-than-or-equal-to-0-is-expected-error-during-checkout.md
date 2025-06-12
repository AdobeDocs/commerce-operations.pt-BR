---
title: 'ACSD-47908: erro *Um valor menor ou igual a 0 é esperado* durante a finalização'
description: Aplique o patch ACSD-47908 para corrigir o erro do Adobe Commerce *Um valor menor ou igual a 0 é esperado* ao selecionar a origem e a quantidade na etapa de envio durante a finalização da compra.
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908: *Um valor menor ou igual a 0 é esperado* erro durante o check-out

O patch ACSD-47908 corrige o erro *Um valor menor ou igual a 0 é esperado* ao selecionar a origem e a quantidade na etapa de envio durante o check-out. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 está instalado. A ID do patch é ACSD-47908. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O seguinte erro é lançado ao selecionar a origem e a quantidade na etapa de remessa durante o check-out: *Um valor menor ou igual a 0 é esperado*.

<u>Pré-requisitos</u>:

Instale os módulos do Adobe Commerce Inventory management (MSI).

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** e configure várias fontes.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** e crie um novo estoque.
   * Agora atribua as origens ao novo estoque.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e edite pelo menos um produto.
   * Verifique se os produtos estão atribuídos às novas fontes e especifique a quantidade disponível.
1. Vá para **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e crie um novo pedido.
1. Adicione esses produtos ao pedido e coloque-o.
1. Clique em **[!UICONTROL Ship]**.
1. Selecione a origem da entrega.
1. Especifique a quantidade de cada item a ser entregue.
1. Recarregue a página.
1. Clique em **[!UICONTROL Proceed to Shipment]**.

<u>Resultados esperados</u>:

A nova página de remessa é aberta sem nenhum erro.

<u>Resultados reais</u>:

* Não é possível validar a quantidade inserida.
* O seguinte erro é lançado: *Insira um valor menor ou igual a 0*.

  No entanto, o erro é inconsistente e nem sempre pode aparecer.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
