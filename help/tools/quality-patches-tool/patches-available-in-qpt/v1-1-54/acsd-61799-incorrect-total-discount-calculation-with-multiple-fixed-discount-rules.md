---
title: 'ACSD-61799: cálculo de desconto total incorreto com várias regras de carrinho de desconto fixo aplicadas à cotação'
description: Aplique o patch ACSD-61799 para corrigir o problema do Adobe Commerce em que o desconto total é calculado incorretamente quando várias regras de carrinho com descontos fixos são aplicadas à cotação.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: cálculo de desconto total incorreto com várias regras de carrinho de desconto fixo aplicadas à cotação

O patch ACSD-61799 resolve/corrige o problema em que o desconto total é calculado incorretamente quando várias regras de carrinho com descontos fixos são aplicadas à cotação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61799. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desconto total é calculado incorretamente quando várias regras de carrinho com *[!UICONTROL Fixed amount discount for the whole cart]* são aplicadas a um carrinho de compras.

<u>Etapas a serem reproduzidas</u>:

1. Crie quatro produtos com um preço de US$ 1.000.
1. Crie três regras de preço do carrinho sem nenhuma condição que dê um desconto de US$ 100 para todo o carrinho.
1. Crie outra regra de preço do carrinho que dê um desconto de USD$ 100 para todo o carrinho, com uma condição que impeça a aplicação da regra.
1. Desative a regra.
1. Adicione três produtos ao carrinho de compras e observe o desconto no carrinho.
1. Adicione mais produtos ao carrinho e observe o desconto no carrinho.
1. Habilitar a regra de preço do carrinho desabilitada.
1. Atualize a página do carrinho de compras e observe o desconto no carrinho.

<u>Resultados esperados</u>:

1. Adicionar outros produtos ao carrinho não altera a quantidade de desconto.
1. Ativar a regra de preço do carrinho com uma condição que não se aplica não altera a quantidade de desconto.

<u>Resultados reais</u>:

1. Adicionar outros produtos ao carrinho altera a quantidade de desconto.
1. Habilitar a regra de preço do carrinho com uma condição que não se aplica altera o valor do desconto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
