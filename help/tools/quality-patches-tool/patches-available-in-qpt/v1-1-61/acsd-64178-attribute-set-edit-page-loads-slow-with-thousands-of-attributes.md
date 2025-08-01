---
title: 'ACSD-64178: a página [!UICONTROL Edit Attribute Set] é carregada lentamente com milhares de atributos de produto'
description: Aplique o patch ACSD-64178 para corrigir o problema do Adobe Commerce em que a página [!UICONTROL Edit Attribute Set] é carregada lentamente se houver milhares de atributos de produto.
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178: a página [!UICONTROL Edit Attribute Set] é carregada lentamente com milhares de atributos de produto

O patch ACSD-64178 corrige o problema em que a página **[!UICONTROL Edit Attribute Set]** é carregada lentamente se houver milhares de atributos de produto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64178. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página **[!UICONTROL Edit Attribute Set]** será carregada lentamente se houver milhares de atributos de produto.

<u>Etapas a serem reproduzidas</u>:

1. Crie pelo menos 4.200 atributos não atribuídos a qualquer um dos conjuntos de atributos.
1. Na barra lateral Admin, vá para **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**. Clique em qualquer conjunto de atributos para editar.

<u>Resultados esperados</u>:

A página é carregada em um tempo razoável.

<u>Resultados reais</u>:

O carregamento da página leva vários minutos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
