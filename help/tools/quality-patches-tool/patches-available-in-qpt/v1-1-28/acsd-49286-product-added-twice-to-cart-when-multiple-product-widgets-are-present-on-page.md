---
title: "ACSD-49286: produto adicionado duas vezes ao carrinho quando vários widgets de produto estão presentes"
description: Aplique o patch ACSD-49286 para corrigir o problema do Adobe Commerce em que o produto é adicionado duas vezes a um carrinho quando vários widgets de produto estão presentes na página.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: produto adicionado duas vezes ao carrinho quando vários widgets de produto estão presentes

O patch ACSD-49286 corrige o problema em que o produto é adicionado duas vezes ao carrinho quando vários widgets de produto estão presentes na página. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-49286. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto é adicionado duas vezes ao carrinho quando vários widgets de produto estão presentes na página.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no administrador e vá para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Na seção de conteúdo, clique em **[!UICONTROL Edit]** usando [!DNL Page Builder].
1. Adicionar dois elementos de linha a **[!UICONTROL Content]**.
1. Adicione produtos em ambos os elementos de linha.
1. Na primeira linha, defina a aparência do produto como [!UICONTROL Product Grid] e selecione qualquer categoria para exibir.
1. Na segunda linha, defina a aparência do produto como [!UICONTROL Product Carousel] e selecione qualquer outra categoria para exibir.
1. Acesse a loja **[!UICONTROL Home Page]** e adicione um produto da Grade de Produtos.
1. Adicionar outro produto de [!UICONTROL Product Carousel].

<u>Resultados esperados</u>:

A quantidade de produtos não deve ser duplicada após adicionar um produto ao carrinho por meio de [!UICONTROL Product Grid].

<u>Resultados reais</u>:

A quantidade de produtos dobra após adicionar um produto ao carrinho por meio de [!UICONTROL Product Grid].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem. 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
