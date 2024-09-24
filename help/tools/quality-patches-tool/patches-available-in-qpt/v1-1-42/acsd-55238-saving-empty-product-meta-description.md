---
title: "ACSD-55238: Salvar a metadescrição do produto vazia"
description: Aplique o patch ACSD-55238 para corrigir o problema do Adobe Commerce em que uma descrição de produto que contém o código de HTML gerado pelo  [!DNL Page Builder]  ou outro editor de HTML é sempre exibida na metadescrição e não há como defini-la como vazia.
feature: Products, Page Builder, Page Content
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: Salvar a metadescrição vazia do produto

O patch ACSD-55238 corrige o problema em que uma descrição de produto contendo código de HTML gerado por um editor de HTML é sempre exibida na metadescrição. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 está instalado. A ID do patch é ACSD-55238. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma descrição do produto que contém o código de HTML gerado por [!DNL Page Builder] ou outro editor de HTML é sempre exibida na metadescrição e não há como defini-la como vazia.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** e crie um novo bloco com qualquer conteúdo.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** e crie um novo produto. Defina a meta descrição como empty.
1. Adicione o bloco criado acima usando *[!DNL Page Builder]* na guia *[!UICONTROL Content]* e salve o produto.
1. Abra o produto na loja e verifique seu elemento de documento `meta name = "description"`.

<u>Resultados esperados</u>:

A meta descrição está vazia.

<u>Resultados reais</u>:

Quando um produto tem um bloco em sua descrição, ele é usado para a metadescrição do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
