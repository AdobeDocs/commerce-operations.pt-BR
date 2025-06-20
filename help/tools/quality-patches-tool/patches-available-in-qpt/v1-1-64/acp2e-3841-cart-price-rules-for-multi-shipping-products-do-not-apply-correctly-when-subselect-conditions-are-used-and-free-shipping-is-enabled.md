---
title: 'ACP2E-3841: As regras de preço do carrinho para produtos de remessa múltipla não se aplicam corretamente quando as condições de subseleção são usadas e a remessa gratuita é ativada'
description: Aplique o patch ACP2E-3841 para corrigir o problema do Adobe Commerce em que as regras de preço do carrinho para produtos de vários envios não se aplicam corretamente quando as condições de subseleção são usadas e o envio gratuito está ativado.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACP2E-3841: As regras de preço do carrinho para produtos de remessa múltipla não se aplicam corretamente quando as condições de subseleção são usadas e a remessa gratuita é ativada

O patch ACP2E-3841 corrige o problema em que as regras de preço do carrinho para produtos de vários envios não se aplicam corretamente quando as condições de subseleção são usadas e o envio gratuito está ativado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACP2E-3841. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p9

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As regras de preço do carrinho para produtos de remessa múltipla não se aplicam corretamente quando as condições de subseleção são usadas e a remessa gratuita é ativada.

<u>Pré-requisitos</u>:

**Configurações:**
1. **[!UICONTROL Free Shipping]** = *Habilitado*
1. **[!UICONTROL Minimum Order Amount]** = *9999999*

**Categorias necessárias:**
1. Categoria de teste 1
1. Categoria de ensaio 2

**Produtos necessários:**
1. Teste do produto 1:
   1. Categorias: Categoria Teste 1
   1. Preço: $ 45
1. Teste do produto 2:
   1. Categorias: Categoria Teste 2
   1. Preço: $ 56,25 

      **(Os preços devem ser os mesmos mostrados aqui para garantir que o teste funcione corretamente.)**

**Regra de preço do carrinho:**

Faça logon como administrador e vá para **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Use estes valores:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: Testar envio gratuito
1. **[!UICONTROL Active]**: *Sim*
1. **[!UICONTROL Websites]**: *Site Principal*
1. **[!UICONTROL Customer Groups]**: *NÃO CONECTADO, Geral, Atacado, Retailer*
1. **[!UICONTROL Coupon]**: *Sem Cupom*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

Ações:

**[!UICONTROL Percent of product price discount]** = *10*

<u>Etapas a serem reproduzidas</u>:

1. Faça logon na loja.
2. Adicionar teste de produto 1.
3. Adicione duas quantidades de Product Test 2.
4. Visitar carrinho.
5. Selecione **[!UICONTROL Check Out with Multiple Addresses]**.

<u>Resultados esperados</u>:

Nenhum erro.

<u>Resultados reais</u>:

*Erro de 500*

*Mensagem: Funcionalidade obsoleta: Conversão implícita de float 112.5 para int perde precisão em /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php na linha 214*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
