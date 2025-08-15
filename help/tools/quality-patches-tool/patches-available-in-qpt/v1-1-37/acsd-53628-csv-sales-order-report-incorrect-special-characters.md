---
title: 'ACSD-53628: o relatório de ordem de venda CSV mostra caracteres especiais incorretos'
description: Aplique o patch ACSD-53628 para corrigir o problema do Adobe Commerce em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-53628: o relatório de ordem de venda CSV mostra caracteres especiais incorretos

O patch ACSD-53628 corrige o problema em que o relatório de ordem de venda CSV mostra caracteres especiais incorretos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37 está instalado. A ID do patch é ACSD-53628. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O relatório de ordem de venda CSV mostra caracteres especiais incorretos.

<u>Etapas a serem reproduzidas</u>:

1. Alterar **[!UICONTROL Base Currency]** e **[!UICONTROL Default Display Currency]** para Euro na configuração de moeda.
1. Fazer um pedido.
1. Na barra lateral Admin, vá para **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Selecione datas. Clique em **[!UICONTROL Show Report]**. Clique em **[!UICONTROL Export]** para exportar o CSV.

<u>Resultados esperados</u>:

Caracteres especiais em um arquivo CSV exportado são mostrados corretamente no Excel.

<u>Resultados reais</u>:

O relatório de ordem de venda CSV mostra caracteres especiais incorretamente.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
