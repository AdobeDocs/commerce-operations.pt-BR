---
title: 'ACSD-65195: A mutação "createCompany" do GraphQL retorna um erro para um país sem uma região necessária'
description: Aplique o patch ACSD-65195 para corrigir o problema do Adobe Commerce em que a mutação "createCompany" do GraphQL lança um erro para países que não exigem uma região.
feature: B2B, Companies, GraphQL
role: Admin, Developer
source-git-commit: 8eb1d7f9d787ddb3b1cc619744920ab8a9914ae8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-65195: A mutação do GraphQL `createCompany` retorna um erro para um país sem uma região necessária

O patch ACSD-65195 corrige o problema em que a mutação [!UICONTROL GraphQL] `createCompany` lança um erro para países que não exigem uma região. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 está instalado. A ID do patch é ACSD-65195. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação [!UICONTROL GraphQL] `createCompany` retorna um erro quando uma região é especificada para um país que não requer uma.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL B2B Companies]**.
1. Envie a mutação `createCompany` [!UICONTROL GraphQL] com um campo de região especificado para um país que não exige uma mutação. Por exemplo: [!UICONTROL country_id]: *AE* e [!UICONTROL region]: *Dubai*.
1. Verifique a resposta do GraphQL.

<u>Resultados esperados</u>:

A empresa deve ser criada com sucesso sem retornar um erro quando uma região for especificada para um país que não exige um.

<u>Resultados reais</u>:

A empresa não é criada e o seguinte erro é retornado:
`Error: Invalid value of "Dubai" provided for the region field.`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
