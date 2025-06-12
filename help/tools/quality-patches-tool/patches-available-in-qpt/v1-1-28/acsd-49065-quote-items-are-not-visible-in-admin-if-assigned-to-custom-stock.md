---
title: 'ACSD-49065: os itens de cotação não estão visíveis no administrador'
description: Aplique o patch ACSD-49065 para corrigir o problema do Adobe Commerce em que os itens de cotação não estão visíveis no administrador se estiverem atribuídos apenas ao estoque personalizado.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: os itens de cotação não estão visíveis no administrador

O patch ACSD-49065 corrige o problema em que os itens de cotação não estão visíveis no administrador se forem atribuídos apenas ao estoque personalizado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-49065. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens de cotação não estarão visíveis no administrador se forem atribuídos somente ao estoque personalizado.

Pré-requisitos:

Os módulos **[!UICONTROL B2B]** e **[!UICONTROL Inventory]** devem ser instalados.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Company]** e **[!UICONTROL B2B Quote]** em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crie um **[!UICONTROL Inventory Source]** secundário e atribua-o a um **[!UICONTROL Inventory Stock]** secundário.
1. Crie um novo produto atribuindo somente o **[!UICONTROL Inventory Source]** secundário (não padrão).
1. Vá para a loja e crie uma nova conta de empresa. Faça logon como o **[!UICONTROL Company Admin]** e adicione o produto criado ao carrinho.
1. Navegue até o carrinho e *[!UICONTROL Request a Quote]*.
1. Vá para o administrador e visualize a cotação solicitada em **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Resultados esperados</u>:

Os itens ficam visíveis na nova cotação criada com os novos produtos sem salvar os produtos novamente.

<u>Resultados reais</u>:

A seção *[!UICONTROL Items Quoted]* está vazia. Se você salvar novamente o produto recém-criado, os itens serão exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
