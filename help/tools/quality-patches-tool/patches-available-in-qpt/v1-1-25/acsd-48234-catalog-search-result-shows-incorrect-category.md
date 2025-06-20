---
title: 'ACSD-48234: contagem incorreta de itens de categoria do resultado da pesquisa do catálogo quando [!UICONTROL Display Out of Stock Products] habilitado'
description: Aplique o patch ACSD-48234 para corrigir o problema do Adobe Commerce em que o resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção [!UICONTROL Display Out of Stock Products] estiver habilitada.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: o resultado da pesquisa de catálogo mostra a contagem de itens de categoria incorreta **[!UICONTROL Display Out of Stock Products]** habilitada

O patch ACSD-48234 resolve o problema em que o resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção **[!UICONTROL Display Out of Stock Products]** está habilitada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-48234. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.


## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O resultado da pesquisa no catálogo mostra uma contagem de itens de categoria incorreta quando a opção **[!UICONTROL Display Out of Stock Products]** está habilitada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e abra o atributo **[!UICONTROL color]**.
1. Adicione duas opções, por exemplo, laranja e verde. Salve o atributo.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** e adicione o atributo **[!UICONTROL color]** ao conjunto de atributos **[!UICONTROL Default]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e defina **[!UICONTROL Display Out of Stock Products]** como _Sim_.
1. Crie a categoria &quot;cat1&quot;.
1. Crie dois produtos:
   1. Nome: prod1, Cor: laranja, Categorias: cat1.
   1. Nome: prod2, Cor: verde, Categorias: cat1.
1. Abra a categoria cat1 na loja.
1. Selecione a cor laranja na navegação em camadas.

<u>Resultados esperados</u>:

Somente o produto prod1 é exibido.

<u>Resultados reais</u>:

Os produtos prod1 e prod2 são mostrados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
