---
title: "ACSD-53722: o preço das opções de produto agrupadas muda para US$ 0"
description: Aplique o patch ACSD-53722 para corrigir o problema do Adobe Commerce em que o preço das opções de produto agrupadas muda para $0 quando atualizações programadas para escopos diferentes se tornam ativas.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722: o preço das opções de produto agrupadas muda para US$ 0

O patch ACSD-53722 corrige o problema em que o preço das opções de produto agrupadas muda para $0 quando atualizações programadas para diferentes escopos se tornam ativas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 está instalado. A ID do patch é ACSD-53722. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço das opções de produto agrupadas muda para $0 quando atualizações programadas para diferentes escopos se tornam ativas.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites, A e B.
1. Definir configuração em **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Crie um produto empacotado com um preço fixo nos sites A e B:

   * Preço de produto agrupado = Fixo = *0*

1. Adicione um produto simples como opção suspensa para o pacote. Defina os seguintes preços:

   * Preço de todas as visualizações de loja do produto simples dentro da opção agrupada = *120*
   * Site do produto simples A price inside bundled option = *130*
   * Preço do site B do produto simples dentro da opção agrupada = *140*

1. Agende uma atualização para desativar o produto incluído no site A.

<u>Resultados esperados</u>:

A atualização programada para o site A não afeta o preço do site B.

<u>Resultados reais</u>:

Após a atualização agendada, o preço da opção de produto agrupado no site B é alterado para **$0**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
