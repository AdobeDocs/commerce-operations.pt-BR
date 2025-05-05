---
title: 'ACSD-58325: botão [!UICONTROL Import] disponível mesmo após um erro de validação'
description: Aplique o patch ACSD-58325 para corrigir o problema do Adobe Commerce em que o botão [!UICONTROL Import] está disponível mesmo após um erro de validação.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
source-git-commit: c50fa066d02c04a08c28730afffe4508019a93aa
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: botão [!UICONTROL Import] disponível mesmo após um erro de validação

O patch ACSD-58325 corrige o problema em que o botão **[!UICONTROL Import]** está disponível mesmo após um erro de validação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-58325. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O botão [!UICONTROL Import] está disponível mesmo após um erro de validação.

<u>Etapas a serem reproduzidas</u>:

1. Crie o arquivo CSV para a importação de produto com um nome de imagem incorreto no arquivo.
1. Crie uma importação de produto agendada usando o arquivo CSV criado.
1. Aguarde até que a importação programada seja executada.
1. Verificar [!UICONTROL Last outcome] na grade **[!UICONTROL Scheduled Imports/Exports]**.

<u>Resultados esperados</u>:

[!UICONTROL Last outcome] deveria ser [!UICONTROL Failed].

<u>Resultados reais</u>:

[!UICONTROL Last outcome] é [!UICONTROL Successful].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
