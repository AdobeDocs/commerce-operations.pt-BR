---
title: 'ACSD-64753: o armazenamento pré-selecionado na Retirada na Loja não é atualizado quando o endereço de entrega é alterado'
description: Aplique o patch ACSD-64753 para corrigir o problema do Adobe Commerce em que a loja pré-selecionada não foi atualizada quando um novo endereço de entrega foi inserido fora do raio de serviço da loja selecionada.
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 036c1b81d9ec8f55f002446a8ea6078c6f8014d9
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-64753: a loja pré-selecionada em &quot;Retirada na Loja&quot; não é atualizada quando o endereço de entrega é alterado

O patch ACSD-64753 corrige o problema em que a loja pré-selecionada não era atualizada quando um novo endereço de entrega era inserido fora do raio de serviço da loja selecionada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 está instalado. A ID do patch é ACSD-64753. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A loja pré-selecionada não foi atualizada quando um novo endereço de entrega foi inserido fora do raio de serviço da loja selecionada.

<u>Etapas a serem reproduzidas</u>:

1. Habilite **[!UICONTROL In-Store Delivery]** navegando até **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Forneça uma Chave de API [!DNL Google] válida para [!DNL Google Distance Provider]. Para fazer isso, navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Adicione uma nova origem (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) e defina os seguintes valores:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sim*
   * **[!UICONTROL Country United]**: *Estados*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Fluxo de Carol*
   * **[!UICONTROL Postcode]**: *60188*
1. Adicione um novo estoque (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**), atribua a nova fonte e o site principal a ela.
1. Edite qualquer produto, atribua o produto à nova Source, Em Estoque e quantidade > *0*.
1. Aguarde até que a reindexação seja concluída.
1. Na loja, crie um novo cliente e adicione um endereço da Califórnia como faturamento e envio padrão.
1. Adicione outro endereço Illinois não padrão a este cliente.
1. Adicione o produto ao carrinho e prossiga para a finalização da compra.
1. Deixe o endereço de entrega selecionado Califórnia e escolha o método de envio **[!UICONTROL Pick in Store]**. Clique em **[!UICONTROL Next]**.

<u>Resultados esperados</u>:

Como o endereço da Califórnia está fora do raio máximo de pesquisa (200 km), o Source de Illinois não deve estar disponível para o cliente.

<u>Resultados reais</u>:

A origem em Illinois pode ser selecionada e o cliente pode prosseguir para o check-out.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
