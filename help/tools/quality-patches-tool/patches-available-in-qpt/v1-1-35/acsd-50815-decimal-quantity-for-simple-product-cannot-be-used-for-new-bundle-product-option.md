---
title: "ACSD-50815: a quantidade decimal do produto simples não pode ser usada para a nova opção de produto agrupada"
description: Aplique o patch ACSD-50815 para corrigir o problema do Adobe Commerce em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado.
feature: Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-50815: a quantidade decimal do produto simples não pode ser usada para a opção de novo produto agrupado

O patch ACSD-50815 corrige o problema em que a quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 está instalado. A ID do patch é ACSD-50815. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade decimal de um produto simples não pode ser usada para uma nova opção de produto agrupada.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador.
1. Crie um novo produto simples.
   * Na janela **[!UICONTROL Advanced Inventory]**, defina [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Salve o produto simples.
1. Crie um novo produto incluído.
1. Adicione qualquer opção.
1. Adicione o produto simples nesta opção.
1. Defina uma quantidade decimal para o produto simples na opção de produto agrupado. Por exemplo, 1.5.

<u>Resultados esperados</u>:

É possível definir a quantidade decimal. Nenhum erro é exibido.

<u>Resultados reais</u>:

O erro, *Insira um número válido neste campo*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
