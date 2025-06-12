---
title: 'ACSD-49822: Atualizações na página de lista de requisições não refletidas na lista de requisições de impressão'
description: Aplique o patch ACSD-49822 para corrigir o problema do Adobe Commerce em que as atualizações na página de lista de requisições não são refletidas na lista imprimir requisições.
feature: Admin Workspace, B2B
role: Admin
exl-id: 053b8900-0900-4b7e-ba1b-ad4b88ca3f35
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-49822: Atualizações na lista de requisições não refletidas na lista de requisições de impressão

O patch ACSD-49822 corrige o problema em que as atualizações na página da lista de requisições não são refletidas na lista imprimir requisições. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49822. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As atualizações na página da lista de requisições não são refletidas na lista imprimir requisições.

<u>Etapas a serem reproduzidas</u>:

1. Habilite a lista de requisições navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[recursos B2B]**.
1. Crie um produto.
1. Efetue log-in como cliente e adicione dois produtos à lista de requisições.
1. Vá para **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Exibir uma lista de requisições.
1. Clique em **[!UICONTROL Print]** no canto superior direito.
1. Feche a janela de impressão e imprima a página da lista de requisições.
1. Exclua um item da lista ou atualize a quantidade de um item e tente imprimi-lo novamente.
1. Você observará que os itens não são atualizados na janela de impressão.
1. Feche a janela de impressão.
1. Você observará que os itens não são atualizados na página de impressão da lista de requisições.

<u>Resultados esperados</u>:

A lista a ser impressa é atualizada após a aplicação de qualquer alteração.

<u>Resultados reais</u>:

As atualizações não são refletidas na página de impressão da lista de requisições.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
