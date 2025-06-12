---
title: 'ACSD-49835: a caixa de seleção [!UICONTROL Use Default Value] não está salva'
description: Aplique o patch ACSD-49835 para corrigir o problema do Adobe Commerce em que a caixa de seleção [!UICONTROL Use Default Value] não é salva corretamente em um nível de armazenamento para um atributo de seleção múltipla.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835: a caixa de seleção [!UICONTROL Use Default Value] não está salva

O patch ACSD-49835 corrige o problema em que a caixa de seleção [!UICONTROL Use Default Value] não é salva corretamente em um nível de armazenamento para um atributo de seleção múltipla. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 está instalado. A ID do patch é ACSD-49835. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A caixa de seleção [!UICONTROL Use Default Value] não está salva corretamente em um nível de armazenamento para um atributo de seleção múltipla.

<u>Etapas a serem reproduzidas</u>:

1. Crie um **[!UICONTROL Multiple-select Attribute]** em **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e adicione-o a um conjunto de atributos.
1. Vá para **[!UICONTROL Product]** e salve **[!UICONTROL Values]** em **[!UICONTROL All Store Views (Default Scope)]**.
1. Vá para uma **[!UICONTROL Store View Scope]** específica e salve o produto.
1. Vá para **[!UICONTROL Store View Scope]** e marque a caixa de seleção **[!UICONTROL Use Default Value]**.

<u>Resultados esperados</u>:

Os valores de atributo de seleção múltipla são salvos corretamente ao marcar a caixa de seleção [!UICONTROL Use Default Value] em [!UICONTROL Store View Scope].

<u>Resultados reais</u>:

Os valores de atributo de seleção múltipla não são salvos corretamente ao marcar a caixa de seleção [!UICONTROL Use Default Value] em [!UICONTROL Store View Scope].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
