---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados'
description: Aplique o patch ACSD-61553 para resolver o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%
---
# ACSD-61553: [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados

O patch ACSD-61553 corrige o problema em que o [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 está instalado. A ID do patch é ACSD-61553. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com um preço de US$ 9.000.
1. Crie um [!UICONTROL Cart Price Rule]: Regra A com um desconto fixo de US$ 700 sem condições e sem descartar as regras subsequentes.
1. Criar outro [!UICONTROL Cart Price Rule]: Regra B com um desconto fixo de $1000 sem condições e sem descartar regras subsequentes.
1. Adicione o produto com a quantidade 13 ao carrinho.
1. Atualize as regras com qualquer um dos cenários abaixo:

   Cenário 01

       Regra A
     Prioridade: 1
     Desconto de Quantidade Máxima Aplicado a: 1
     
     Regra B
     Prioridade: 0
     Desconto de Quantidade Máxima Aplicado a: 0
   
   Cenário 02

       Regra A
     Prioridade: 0
     Desconto de Quantidade Máxima Aplicado a: 0
     
     Regra B
     Prioridade: 1
     Desconto de Quantidade Máxima Aplicado a: 1
   
   Cenário 03

       Regra A
     Prioridade: 0
     Desconto de Quantidade Máxima Aplicado a: 0
     
     Regra B
     Prioridade: 0
     Desconto de Quantidade Máxima Aplicado a: 1
   
1. Clique no botão **[!UICONTROL Update Shopping Cart]** para recalcular os descontos.

<u>Resultados esperados</u>:

Você vê o seguinte desconto total para diferentes cenários:

    Cenário 01: $13.700
    Cenário 02: $10.100
    Cenário 03: $10.100

<u>Resultados reais</u>:

Nos três cenários, o desconto total é de US$ 9.000.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
