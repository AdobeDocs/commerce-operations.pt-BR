---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule] não cancela as regras anteriores devido à quantidade insuficiente do produto'
description: Aplique o patch ACSD-59865 para corrigir o problema do Adobe Commerce em que o valor *Etapa de quantidade de desconto* em *Desconto de quantia fixa,* *Porcentagem de desconto de preço do produto,* e *Comprar X obtém Y* [!UICONTROL Cart Price Rules] não cancela mais a ação das regras anteriores.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] não cancela as regras anteriores devido à quantidade insuficiente do produto

O patch ACSD-59865 corrige o problema em que o valor *[!UICONTROL Discount quantity step]* em *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* e *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] não cancela mais a ação das regras anteriores. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 está instalado. A ID do patch é ACSD-59865. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O [!UICONTROL Cart Price Rule] não cancela as regras aplicadas anteriormente devido a uma quantidade insuficiente de produtos no carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** e clique em **[!UICONTROL Add New rule]**.
   * Definir **[!UICONTROL Rule Name]** = *Teste - 1*
   * Selecionar todos os *Sites* e *Grupos de clientes*
   * Conjunto **[!UICONTROL Priority]** = *0*
   * Vá para a seção **[!UICONTROL Actions]**:
      * Definir **[!UICONTROL Apply]** = *Percentual de desconto no preço do produto*
      * Conjunto **[!UICONTROL Discount amount]** = *10*
      * Conjunto **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Conjunto **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Definir **[!UICONTROL Discard subsequent rules]** como *Não*
1. Limpe o cache.
1. Vá para a Loja, adicione um item ao carrinho e prossiga para *check-out/carrinho*.
1. Verifique se o desconto de *10%* foi aplicado ao carrinho.
1. Retorne ao **[!UICONTROL Cart Price Rules]** e crie uma nova regra.
   * Definir **[!UICONTROL Rule Name]** = *Teste - 2*
   * Selecionar todos os **[!UICONTROL Websites]** e **[!UICONTROL Customer Groups]**
   * Conjunto **[!UICONTROL Priority]** = *2*
   * Navegue até a seção **[!UICONTROL Actions]**:
      * Definir **[!UICONTROL Apply]** = *Percentual de desconto no preço do produto*
      * Conjunto **[!UICONTROL Discount amount]** = *20*
      * Conjunto **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Conjunto **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Limpe o cache.
1. Volte para a Loja novamente.
1. Atualize o carrinho para atualizar as regras. Verifique se o desconto de *10%* não é mais aplicado.
1. Adicione itens ao carrinho até que a quantidade atenda ao valor de *Etapa* necessário para a segunda regra.

<u>Resultados esperados</u>:

O primeiro [!UICONTROL Cart Price Rule] é aplicado quando as condições da segunda regra são atendidas.

<u>Resultados reais</u>:

As regras de preço são aplicadas conforme configurado no painel de administração.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
