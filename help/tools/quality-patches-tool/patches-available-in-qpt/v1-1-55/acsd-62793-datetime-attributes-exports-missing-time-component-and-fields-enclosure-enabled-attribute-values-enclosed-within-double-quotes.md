---
title: 'ACSD-62793: atributos Datetime em exportações sem componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver habilitado, os valores de atributo serão colocados entre aspas duplas'
description: Aplique o patch ACSD-62793 para corrigir o problema do Adobe Commerce em que os atributos datetime em dados exportados não têm o componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver habilitado, os valores de atributo na coluna *additional_attributes* serão colocados entre aspas duplas.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
source-git-commit: 1645006f142c902ac729a99502f59b6d42266691
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# ACSD-62793: atributos Datetime em exportações sem componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver habilitado, os valores de atributo serão colocados entre aspas duplas

O patch ACSD-62793 corrige o problema em que os atributos datetime em dados exportados não têm o componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver habilitado, os valores de atributo na coluna *additional_attributes* serão colocados entre aspas duplas. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-62793. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os atributos Datetime nos dados exportados não incluem o componente de tempo. Além disso, se **[!UICONTROL Fields Enclosure]** estiver habilitado, os valores de atributo na coluna *additional_attributes* serão colocados entre aspas duplas.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo de produto com **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Atribua o atributo ao conjunto de atributos **[!UICONTROL Default]**.
1. Crie um produto simples com um valor de data e hora para o novo atributo.
1. Exporte o produto para um arquivo CSV de **[!UICONTROL System]** > *Transferência de Dados* > **[!UICONTROL Export]**.
1. Verifique o valor do atributo na coluna *additional_attributes*. Ele só tem a parte de data, mas não a hora.
1. Atualize o valor do atributo para usar a hora, por exemplo, &quot;08/10/22, 15:20&quot;.
1. Importe o arquivo CSV.
1. Verifique a tabela *catalog_product_entity_datetime*.

<u>Resultados esperados</u>:

A data e a hora são exportadas e importadas corretamente.

<u>Resultados reais</u>:

Somente a parte de data é exportada e importada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
