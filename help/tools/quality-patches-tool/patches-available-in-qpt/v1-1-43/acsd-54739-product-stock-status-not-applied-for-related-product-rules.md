---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* status não aplicado para *[!UICONTROL Related Product Rules]*'
description: Aplique o patch ACSD-54739 para corrigir o problema do Adobe Commerce em que o status *[!UICONTROL Product Stock]* não é aplicado para *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: status *[!UICONTROL Product stock]* não aplicado para *[!UICONTROL Related Product Rules]*

O patch ACSD-54739 corrige o problema em que o status *[!UICONTROL Product stock]* não é aplicado para *[!UICONTROL Related Product Rules]*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-54739. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status *[!UICONTROL Product stock]* não é aplicado a *[!UICONTROL Related Product Rules]*.

<u>Etapas a serem reproduzidas</u>:

1. Defina a configuração **[!UICONTROL Display Out of Stock Products]** como *Sim*.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** e defina *Sim* para a condição de regra promocional.
1. Crie a regra de produto relacionada. Vá para **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Adicionar uma condição com quantidade de atributo (selecionar em estoque/esgotado).
1. Verifique os produtos no front-end.

<u>Resultados esperados</u>:

O produto em estoque/indisponível corresponde a *[!UICONTROL Related Product Rules]*.

<u>Resultados reais</u>:

O produto em estoque/indisponível não corresponde ao *[!UICONTROL Related Product Rules]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
