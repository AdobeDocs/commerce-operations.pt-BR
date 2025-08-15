---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados'
description: Aplique o patch ACSD-61553 para resolver o problema do Adobe Commerce em que o [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados

O patch ACSD-61553 corrige o problema em que o [!UICONTROL Cart Price Rule] é calculado incorretamente quando vários descontos com prioridades diferentes são aplicados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53 está instalado. A ID do patch é ACSD-61553. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
